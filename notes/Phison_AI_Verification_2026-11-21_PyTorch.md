# 群聯 AI 系統驗證面試訓練｜2026-11-21：PyTorch 推論、Device、效能與驗證

> 目標職缺：群聯電子 AI 系統驗證工程師（Middleware）0509。  
> 整理方式：依 11/21 的 10 題及後續追問，重構為「題目 → 建議回答／程式 → 個人錯誤與修正」的面試複習筆記，非逐字聊天紀錄。第 10 題部分追問及補充在 11/22 完成。  
> **分數說明**：分數為當時教練提供的練習回饋；修正後答對不代表第一次限時作答即 AC。未回報的題目不虛構已完成結果。

## 0. 當日訓練概覽

| 題號 | 主題 | 練習情況 |
|---|---|---|
| 1 | Tensor Shape：`permute`、`reshape`、`mean` | 初答 9/10；追問 10/10 |
| 2 | `sum(dim=0/1)`、`unsqueeze` | 10/10 |
| 3 | `model.train()` vs `model.eval()` | 初答 2/10；追問 7/10；最後確認 10/10 |
| 4 | `torch.no_grad()` | 初答 7/10；追問 10/10 |
| 5 | `no_grad()` vs `inference_mode()` | 初答 7/10；追問 8/10 |
| 6 | 跨 GPU 推論一致性、效能 Debug | 初答 5/10；中間追問 7.5/10，效能實驗題續練 |
| 7 | Batch Inference Python 實作 | 初版 4/10 → 第二版 8/10 → 修正後 AC |
| 8 | Device Mismatch 與推論程式除錯 | 初答 7/10；Batch 追問 4/5 |
| 9 | Batch Size、Latency、Throughput | 初答 4/10；效能追問 5/5 |
| 10 | AI Middleware 交付驗證 | 初答 4/10；11/22 追問 7/10；最後兩項由教練補充 |

## 1. Tensor 與 Shape

### Q1. 推導以下 Tensor 的 Shape，`permute` 與 `reshape` 有何差異？

```python
x = torch.randn(2, 3, 224, 224)
y = x.permute(0, 2, 3, 1)
z = y.reshape(2, -1, 3)
w = z.mean(dim=1)
```

**答案：**

| Tensor | Shape | 說明 |
|---|---|---|
| `x` | `(2, 3, 224, 224)` | NCHW |
| `y` | `(2, 224, 224, 3)` | NHWC |
| `z` | `(2, 50176, 3)` | 空間維度 224×224 展平 |
| `w` | `(2, 3)` | 對第 1 維求平均 |

- `permute` 調換**維度次序**，通常為 View，改 stride、不複製底層資料。
- `reshape` 在元素總數相同的前提下改變形狀；可能回傳 View，也可能複製。不能把 `reshape` 當成轉置。

**追問：**

```python
a = torch.tensor([[1, 2, 3], [4, 5, 6]])
b = a.permute(1, 0)      # [[1, 4], [2, 5], [3, 6]]
c = a.reshape(3, 2)      # [[1, 2], [3, 4], [5, 6]]
# b.shape == c.shape == (3, 2)，但元素排列不同
```

當日追問回答正確。

### Q2. `sum` 與 `unsqueeze`

```python
a = torch.tensor([[1, 2, 3], [4, 5, 6]])
b = a.sum(dim=0)       # tensor([5, 7, 9])
c = a.sum(dim=1)       # tensor([6, 15])
d = a.unsqueeze(0)     # shape [1, 2, 3]
```

- `dim=0`：沿第 0 維加總，保留各欄。
- `dim=1`：沿第 1 維加總，保留各列。
- `unsqueeze(0)`：在最前方加入大小 1 的維度。

## 2. train/eval、Autograd、Inference Mode

### Q3. `model.train()` 和 `model.eval()` 有什麼不同？

**面試建議回答：** `model.train()`／`model.eval()` 切換模型內部特定 Layer 的執行行為，並**不是**開關梯度、凍結參數或執行權重更新。

| Layer | Train | Eval |
|---|---|---|
| Dropout | 隨機將部分活化設成 0（含適當縮放） | 停用隨機丟棄 |
| BatchNorm（預設追蹤統計量） | 使用當前 Batch 統計量並更新 Running Stats | 使用先前累積的 Running Stats |
| Linear / Conv | 一般 Forward | 一般 Forward |

- 忘記 `eval()` 可能使 Dropout 輸出有隨機性、BatchNorm 受當前 Batch 影響，造成不穩定或與預期不一致的推論。
- **`eval()` 不會自動關閉 Autograd；`train()` 也不會自動更新權重。**
- 一般訓練流程：`outputs=model(x)` → `loss.backward()`（梯度）→ `optimizer.step()`（更新參數）。

**當時錯誤**：「train 開梯度、eval 關梯度」、「忘記 eval 權重會更新」。追問確認已能答出：只執行 `model.eval(); model(images)`，若參數需要梯度且 Autograd 啟用，仍可建立計算圖，但沒有 optimizer step 時權重不會自動更新。

### Q4. `torch.no_grad()` 有什麼作用？為何 `eval()` 後仍要使用？

**建議回答：**

- `model.eval()` 管理 Dropout／BatchNorm 等的評估模式；`torch.no_grad()` 停用區塊內一般運算的反向梯度圖記錄。
- 對純推論可減少需為 Backward 保存的中間資訊與 Autograd 開銷，通常節省記憶體，也可能加快速度；模型權重／輸出等仍需記憶體。
- 若要算輸入影像 Gradient（如 Saliency Map），不能在相關計算外層直接關閉梯度。
- `no_grad()` 不會永久更改參數的 `requires_grad`。

```python
model = torch.nn.Linear(3, 2)  # weight 預設 requires_grad=True
x = torch.randn(1, 3)
model.eval()

y1 = model(x)            # y1.requires_grad == True
with torch.no_grad():
    y2 = model(x)        # y2.requires_grad == False
# 只有 forward，不會自動更新 model.weight
```

### Q5. `no_grad()` 與 `inference_mode()` 的差異？

**面試建議回答：** 兩者均避免一般反向梯度圖記錄；`inference_mode` 還減少 View Tracking 與 Version Counter 更新等額外開銷，並停用 Forward-mode AD，因此純推論有時更快，但建立的 Inference Tensor 在後續 Autograd 使用上有額外限制。並非「完全不儲存任何 Metadata」。

- 純推論：可以優先評估 `inference_mode()`，以實測 Benchmark 決定。
- 若結果需參與後續 Autograd：使用較合適的梯度模式，避免直接沿用不能被儲存供 Backward 的 Inference Tensor。
- 如果只是記錄 Log、Trace 資料流或進行效能 Profiling，**不等於一定需要 Autograd**。

**追問程式：**

```python
w = torch.tensor([2.0, 3.0], requires_grad=True)
with torch.inference_mode():
    y = torch.tensor([4.0, 5.0])

loss = (w * y).sum()     # 這個乘法可能直接 RuntimeError
loss.backward()
```

原因：計算 `w` 梯度時乘法的 Backward 需要保存 `y`，但 Inference Tensor 不能以這種方式保存；錯誤可能在**Forward 建立運算圖**時出現，而非一定要等到 `backward()`。並非 `y` 自身必須求梯度。

若將 `inference_mode()` 改為 `no_grad()`，`y` 為一般 Tensor，`w.grad` 可得到 `tensor([4., 5.])`。也可以離開 `inference_mode()` **之後**呼叫 `y = y.clone()` 生成一般 Tensor；在區塊內 Clone 仍可能得到 Inference Tensor。

## 3. 跨 GPU 正確性與效能定位

### Q6. 相同模型權重在不同 GPU 上，為何結果或效能不同？

**可能原因：**
1. Input Tensor 不一致：Resize、影像解碼、RGB/BGR、Normalization、dtype、Shape。
2. 模型／推論設定不同：`eval()`、是否使用 `autocast()`、FP32/TF32/FP16/BF16、Batch Size。
3. GPU 架構與 PyTorch、CUDA、cuDNN、Driver 版本差異。
4. 浮點數運算順序、底層 Kernel、可能的非決定性操作。
5. CPU 前處理、CPU→GPU 傳輸、Warm-up、GPU 負載與同步時機造成效能差異。

**`torch.no_grad()` 通常不會改變純 Forward 的數值**，不應當成預測差異的主要原因。固定 Seed 可以排除某些隨機因素，但不能保證跨硬體逐位相同。

**建議 Debug 步驟：**
1. 固定同一份經前處理後的 Input Tensor，確認真正送進模型的數值完全一致。
2. 核對模型權重、結構、`eval()`、精度、環境版本。
3. 比較 Logits 而非只有 `argmax`，計算最大絕對誤差、相對誤差及依驗收條件設定的 `torch.allclose()`。
4. 差異超標時逐層比較中間 Tensor，找出首次出現差異的位置。
5. 以代表性測試集檢查整體預測一致率、指標變化，而不是只看單一圖片。

**原始追問：**

| | Class 0 | Class 1 | Prediction |
|---|---:|---:|---|
| GPU A | 2.501 | 2.499 | 0 |
| GPU B | 2.498 | 2.502 | 1 |

兩個 Logit 很接近，微小數值變化就可能讓 `argmax` 翻轉；**分類不一致不一定是部署 Bug**。`allclose` 必須搭配事先定義的容許誤差及其他驗證證據，不能單憑 True/False 下結論。

### Q6 延伸：GPU 利用率 15%、CPU 95%，該怎麼查？

**回答：** 優先懷疑 CPU 前處理、I/O 或資料供應鏈使 GPU 等待，但使用率只是線索，不是證明。先量測再下結論。

**對照實驗：**

- A：Disk → CPU Decode/Preprocess → CPU-to-GPU → GPU Forward，平均 120 ms/batch。
- B：同 Shape/Dtype/Batch Size 的 Tensor 預載 GPU → GPU Forward，平均 25 ms/batch。

實驗差為 95 ms，但**不能宣稱 CPU 前處理獨自耗費 95 ms**；差異可能包含讀圖、前處理、資料傳輸、同步與調度成本，且 Pipeline 可能重疊執行。下一步個別量測各階段、分析 `torch.profiler` Trace 或 CUDA Events，並持續核對端到端測量。

**另一組獨立階段測量：**

| 階段 | 時間 |
|---|---:|
| 資料讀取 | 5 ms |
| CPU 前處理 | 75 ms |
| CPU → GPU | 12 ms |
| GPU Forward | 25 ms |

優先檢查 75 ms 的 CPU 前處理：可能透過調整 DataLoader Workers、減少重複運算、快取結果或改善最耗時的轉換操作。之後在相同條件下重新量測 Latency／Throughput，**同時驗證輸出正確性、順序及筆數沒有退步**。注意加 Worker 可能改善吞吐量，但不保證單一請求 Latency 一定下降。

**當日學習缺口：** 最早只能說「看 Profiler」，仍不熟悉具體要量哪些階段、如何設計對照實驗，以及 CUDA 非同步計時方式。

## 4. PyTorch Batch Inference 實作

### Q7. 輸入 `[N,3,224,224]`，模型輸出 `[N,10]` Logits，回傳 `list[int]`

**原始要求：** 模型／輸入放相同 Device、`eval()`、停用梯度圖、一次處理 Batch、`argmax(dim=1)`、支援 N=0、不要執行權重更新。

**當日修正後 AC 程式（根據原碼及最後一行修正合併）：**

```python
import torch

def predict_classes(model, images, device):
    model.to(device)
    model.eval()
    if len(images) == 0:
        return []
    images = images.to(device)
    with torch.no_grad():
        logits = model(images)
        predictions = torch.argmax(logits, dim=1)
    return predictions.cpu().tolist()
```

**錯誤與修正：**
- `model.to_device(device)` 不是一般 PyTorch `nn.Module` API → `model.to(device)`。
- `images.to(device)` 未接住回傳值，原變數仍可能指向 CPU → `images = images.to(device)`。
- `for image in images` 每次取得 `[3,224,224]`，失去 Batch 維度；改一次傳 `[N,3,224,224]`。
- `softmax(output)` 得機率，不是 Class Index；`argmax(dim=1)` 找每列最大值索引，不必先做 Softmax。
- `predictions.cpu().tolist()` 回傳 Python `list[int]`；`N=0` 時直接回 `[]`。
- `model.to(device)` 可改變模型放置位置；`model.eval()` 改模式，但不代表學習到的權重數值被 optimizer 更新。假設模型是一般無額外 Forward 狀態更新的分類模型。

## 5. CPU/GPU、Batch Latency 與 Throughput

### Q8. 為什麼原始程式會 Device Mismatch？

```python
model = MyModel()
model.load_state_dict(torch.load("model.pth", map_location="cpu"))
model = model.cuda()
images = torch.randn(8, 3, 224, 224)  # 預設在 CPU
model.eval()

for i in range(100):
    outputs = model(images)
    print(outputs.shape)
```

**答案：** 模型在 CUDA、圖片在 CPU；先將 `images = images.to("cuda")`。若純推論也應考慮 `no_grad()`／`inference_mode()`。若要做 Benchmark，需 Warm-up、重複計時並正確處理 CUDA 非同步。

**當日誤解：** 以為這是「逐張推論」。事實上 `images` 已是 **8 張一個 Batch**，`for i in range(100)` 是**同一批 8 張重複推論 100 次**。

如果寫：

```python
for image in images:
    output = model(image)
```

此時 `image.shape == (3,224,224)`，少了模型要求的 N 維；應直接傳入 `model(images)`。

### Q9. Batch Size 增大為何平均單張成本下降？

**回答：** 大 Batch 可能提高 GPU 平行資源利用率、分攤 Kernel Launch 等固定成本，因此每 Batch 總時間通常增加但未必按圖片張數等比例增加。不能說「顯存夠，1 張和 16 張一定相同時間」。

已量測資料：

| Batch Size | Batch Latency | 平均每張成本 | Throughput |
|---|---:|---:|---:|
| 1 | 8 ms | 8 ms | 125 images/s |
| 16 | 32 ms | 2 ms | 500 images/s |

- **Throughput** 是單位時間處理量；穩態吞吐量較高的是 Batch 16。
- **單張平均成本 != 單張請求回應延遲**。若必須單張在 10 ms 內回應，Batch 1 的 8 ms 較符合要求；Batch 16 要等整批約 32 ms，還可能有 Batch 等待。
- CUDA 操作常是非同步；測 GPU Latency 應先 Warm-up，再以 CUDA Events 或正確的 `torch.cuda.synchronize()` 配合計時，重複測多次，並標示 Batch Size、硬體與精度。

## 6. AI Middleware 交付驗證

### Q10. RD 說模型能跑且 Accuracy 不錯，如何證明 Middleware 可交付？

**最初使用者提出：** 環境、電腦配置、模型輸入輸出、延遲（初答 4/10）。11/22 追問後可提出 Ground Truth 比對、異常 Shape、重複測量（7/10）。其他兩項由教練補充，不算獨立作答。

**完整面試參考答案：**

| 驗證項目 | 如何測試 | 事先設定的 Pass / Fail |
|---|---|---|
| 1. 模型正確性 | 獨立、具代表性的有標籤測試集，比對 Prediction/Ground Truth；計算 Accuracy、Precision/Recall 等適當指標 | 指標達要求，且重要類別／情境沒有不可接受的退化 |
| 2. 異常輸入與容錯 | 錯誤 Shape（`[8,1,224,224]`）、Dtype、空輸入、缺欄位、不合法格式 | 可預期地拒絕或處理、回報明確錯誤、不發生未預期 Crash |
| 3. 效能 | 固定硬體、版本、Batch Size、輸入；Warm-up 後多次量測 Latency、P95/P99、Throughput、資源使用量 | 符合事先定義的 SLO/SLA；不可只看一次測量或單一平均值 |
| 4. 環境相容性 | 指定 GPU/CPU、Driver、CUDA、PyTorch 等支援環境矩陣逐一部署、跑同一批資料 | 每個要求支援的環境都能正常執行、輸出符合容差且效能達標 |
| 5. Regression Testing | 模型／Middleware 更新後重跑固定測試集、曾修正 Bug 的測試、輸入輸出契約與效能測試 | 既有功能不退步，新舊輸出變動符合批准的驗收標準 |

**面試 60–90 秒口頭回答重點：** 從正確性、異常輸入、效能、相容性、回歸測試五方面建立案例、量化標準與報告；每個檢查都說清楚「測什麼、怎麼測、何時 Pass/Fail」，不能只說「我會看輸入輸出」。

**當日追問的關鍵：**
- 有 Ground Truth 就直接比 Prediction，這是正確性驗證起點；還需有代表性資料與驗收門檻。
- Shape 不合法應在模型前檢查並回報可預期錯誤，不能只說「進不了 model」。
- 單測 10 次取平均值仍不足以驗證延遲要求；需 Warm-up、計時正確性、分位數與超時比例，視規格而定。

## 7. 面試前重點清單

- [ ] 能口述 `model.eval()`、`torch.no_grad()`、`inference_mode()` 的獨立功能，不再混淆梯度圖與權重更新。
- [ ] 看懂 NCHW、`permute`、`reshape`、`argmax(dim=1)`，知道 Loop over Batch 會少 N 維。
- [ ] 寫出 `model.to(device)`、`images = images.to(device)`、`predictions.cpu().tolist()`。
- [ ] 能區分 Batch Latency、平均每張處理成本及 Throughput，知道 CUDA 非同步計時。
- [ ] 遇到跨 GPU Logits 差異，先固定輸入和環境，再量化差異並逐層定位。
- [ ] 效能瓶頸必須靠實驗量測，不能只憑 CPU/GPU 使用率或硬碟型號下結論。
- [ ] 模型「跑得動」不代表 Middleware「可交付」，每項驗證要有案例與 Pass/Fail 標準。
