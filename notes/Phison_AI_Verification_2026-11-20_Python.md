# 群聯 AI 系統驗證面試訓練｜2026-11-20：Python 字串、Log Parser、邊界條件

> 目標職缺：群聯電子 AI 系統驗證工程師（Middleware）0509。  
> 整理方式：依當日互動練習重構成「面試題目 → 建議答案／程式 → 原本錯誤與修正」。不是逐字聊天記錄。  
> **作答獨立性**：Log Parser 是拆成多個小練習、在引導下逐步完成；`mask_numeric_runs` 則是先自行嘗試狀態追蹤，再根據回饋修正為 AC。不要把引導式 AC 記為初次獨立限時 AC。

## 一、當日核心結果

| 題型 | 結果 | 最重要的學習 |
|---|---|---|
| 字串解析與欄位格式檢查 | 完成 | `split`、`strip`、`count`、`enumerate`、錯誤輸入防護 |
| `parse_sample_id` | AC | 以允許字元的 Set 做驗證，空字串必須拒絕 |
| `parse_status` | AC | `strip().upper()` 產生新字串，必須接住回傳值 |
| `parse_latency` | AC | 字串後綴、ASCII 數字、`int`、非法格式回 `None` |
| `split_log_fields` | AC | 恰好三個欄位、每欄恰好一個 `=`、Key 順序固定 |
| `validate_one_log` | AC | 串接四個函式並保留標準化結果 |
| `parse_inference_logs` | 引導式 AC | 遍歷多筆、過濾 `None`、保留輸入順序 |
| `mask_numeric_runs` | 修正後 AC | 連續區段狀態追蹤、ASCII 限制、`list + join` |

## 二、Log Parser 題目規格

原始 Log 每行由三個欄位組成，順序固定：

```text
sample_id=img001;status=OK;latency=42ms
```

- Key 依序只能是 `sample_id`、`status`、`latency`（大小寫敏感），Key 與 Value 前後可以有空白。
- `sample_id`：非空；只允許 ASCII 英文字母、數字、`_`、`-`。
- `status`：`OK` 或 `ERROR`（輸入大小寫不敏感，回傳時統一大寫）。
- `latency`：非負的 ASCII 十進位整數 + 小寫 `ms`，接受 `0ms` 與 `007ms`。
- 無效 Log 必須跳過；合法資料回傳 `(sample_id, status, latency_int)`。
- 多筆結果保持輸入順序，空 `lines` 回傳 `[]`。

原始練習測資：

```python
lines = [
    "sample_id=img001;status=OK;latency=42ms",
    " sample_id = img002 ; status = error ; latency = 105ms ",
    "sample_id=img003;status=OK;latency=0ms",
    "sample_id=;status=OK;latency=12ms",
    "sample_id=img004;status=FAIL;latency=25ms",
    "sample_id=img005;status=OK;latency=-5ms",
    "sample_id=img006;status=OK",
    "sample_id=img_007;status=ok;latency=007ms",
]
# 預期：
# [('img001', 'OK', 42), ('img002', 'ERROR', 105),
#  ('img003', 'OK', 0), ('img_007', 'OK', 7)]
```

## 三、題目與建議答案

### Q1. 如何驗證 Sample ID 只包含指定 ASCII 字元？

**當日自行完成的核心寫法：**

```python
ALLOWED_CHARS = set(
    "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_-"
)

def parse_sample_id(sample_id):
    sample_id = sample_id.strip()
    if sample_id == "":
        return None
    for c in sample_id:
        if c not in ALLOWED_CHARS:
            return None
    return sample_id
```

- `" img_002 "` → `"img_002"`；`"sample-03"` 合法。
- 空字串、全空白、`"img 004"`、`"img@005"`、`"圖片001"`、`"img.006"` → `None`。
- `set` 成員檢查平均 O(1)；整體掃描 O(n)。不能單靠 `isalnum()`，因為它也可能接受 Unicode，且不接受 `_`、`-`。

### Q2. 如何解析 Status，並統一大小寫？

```python
def parse_status(status):
    status = status.strip().upper()
    if status == "OK" or status == "ERROR":
        return status
    return None
```

- `"error"` → `"ERROR"`；`"  ok  "` → `"OK"`；`"FAIL"` → `None`。
- **當日原錯誤**：只寫 `status.strip().upper()`，沒有把結果指定回 `status`。字串不可變，方法不會就地修改它。

### Q3. 如何解析 Latency，同時拒絕非法格式？

```python
def parse_latency(latency):
    if not latency.endswith("ms"):
        return None
    num = latency[:-2]
    if num.isascii() and num.isdecimal():
        return int(num)
    return None
```

- `"105ms"` → `105`、`"0ms"` → `0`、`"007ms"` → `7`。
- `"ms"`、`"-5ms"`、`"1.5ms"`、`"abcms"`、`"12MS"` → `None`。
- `isdecimal()` 單獨使用時可接受某些非 ASCII 數字，因此需搭配 `isascii()`。
- 在完整 Parser 中，前一步已對 Value 做 `strip()`；若獨立使用此函式，輸入預設已經移除外側空白。

### Q4. 如何驗證欄位數量、等號數量與 Key 順序？

**使用者完成的 `split_log_fields`（排版稍作整理）：**

```python
def split_log_fields(line):
    expected_keys = ["sample_id", "status", "latency"]
    parts = line.split(";")
    valid = True
    values = []

    if len(parts) != 3:
        valid = False
    else:
        for i, part in enumerate(parts):
            if part.count("=") != 1:
                valid = False
                break
            p = part.split("=")
            k = p[0].strip()
            v = p[1].strip()
            if k != expected_keys[i]:
                valid = False
                break
            values.append(v)

    if valid:
        return tuple(values)
    return None
```

- 正常輸出：`("img001", "OK", "42ms")`（尚未驗證 Value 的合法性）。
- 缺欄位、額外欄位、`sample_id=a=b`、欄位順序錯誤 → `None`。
- `sample_id=;status=OK;latency=42ms` → `("", "OK", "42ms")` **是此函式的正確結果**：這層只檢查結構，後續 `parse_sample_id` 才拒絕空 ID。

### Q5. 如何串接子函式來驗證單筆 Log？

```python
def validate_one_log(line):
    parts = split_log_fields(line)
    if parts is None:
        return None

    sample_id = parse_sample_id(parts[0])
    status = parse_status(parts[1])
    latency = parse_latency(parts[2])

    if sample_id is None or status is None or latency is None:
        return None
    return (sample_id, status, latency)
```

重要：**一定要使用驗證函式的回傳值**，不要檢查 `parse_status(parts[1])` 後仍回傳原始 `parts[1]`；否則 `"error"` 不會變成 `"ERROR"`。也不能寫 `if not latency`，因為合法的 `0` 會被誤判。

### Q6. 如何把多筆 Log 轉為合法結果 List？

**最終使用者自行寫出的整合部分：**

```python
def parse_inference_logs(lines):
    res = []
    for line in lines:
        result = validate_one_log(line)
        if result is not None:
            res.append(result)
    return res
```

- 多筆逐一處理、忽略 `None`、保留順序；`parse_inference_logs([]) == []`。
- 對輸入總字元數 N，整體時間 O(N)（以一般長度整數轉換為前提）；輸出與必要字串暫存使用 O(N) 空間。
- 這是**在引導下完成的 AC**，下一階段需練習沒有拆解提示的限時題。
- 極長的數字字串可能受 Python `int` 十進位轉換位數限制；若產品規格要求任意長度輸入都不得拋錯，需要額外處理。

### Q7. 如何用 `flag` 將連續 ASCII 數字替換成 `<NUM>`？

題目：不可使用 Regex，`"a12b345c"` → `"a<NUM>b<NUM>c"`；全形數字不要替換；目標 O(n)。

**最終自行修改完成的版本：**

```python
def mask_numeric_runs(text):
    res = []
    flag = 1
    for c in text:
        if "0" <= c <= "9" and flag:
            res.append("<NUM>")
            flag = 0
        elif "0" <= c <= "9":
            pass
        else:
            res.append(c)
            flag = 1
    return "".join(res)
```

- `flag = 1`：目前尚未在數字段落中；遇到首個數字加一次 `<NUM>`、轉 `0`。
- `flag = 0`：目前處於數字段落；後續連續數字全部跳過。
- 遇到非數字，照原樣保留並將 `flag` 重設為 `1`。
- `"img001"` → `"img<NUM>"`；`"12345"` → `"<NUM>"`；`""` → `""`；`"a１２b"` → 原字串。
- 使用 `list.append()` + `"".join()`：時間 O(n)、額外空間 O(n)；避免大量 `str += ...` 在一般情況下造成可能的 O(n²) 複製成本。
- 可讀性改善：用 `in_number: bool` 代替 0/1，但使用者原版邏輯正確。

## 四、當日實際犯過的語法／觀念錯誤

| 原本寫法／想法 | 正確觀念 |
|---|---|
| `print(Invalid)` | 文字要有引號：`print("Invalid")` |
| `part.spilt("=")` | 正確方法為 `split` |
| `len(parts != 3)` | `len(parts) != 3`，先取長度再比較 |
| `if parts in None` | `if parts is None`；`in` 是成員檢查 |
| `if result not None` | `if result is not None` |
| 只呼叫 `validate_one_log(line)` 卻沒有保存／印出 | `return` 值需指派、加入 List 或印出才會被使用 |
| 把 `print` 當作回傳 | `print` 只顯示，`return` 才將值交給呼叫者 |
| 驗證 `status` 合法後回傳原始 `parts[1]` | 使用 `parse_status` 的標準化結果 |
| `flag` 放在 `for` 迴圈裡 | 狀態必須跨字元保留，應在迴圈外初始化 |
| `isdecimal()` 視為只接受 0–9 | 使用 `"0" <= c <= "9"` 或 `isascii() and isdecimal()` |

## 五、面試前 3 分鐘快速複習

1. 檢查格式時，**先檢查欄位數量，再取索引**，避免 `IndexError`。
2. 用 `is None` / `is not None` 判斷「驗證失敗」，不要誤傷合法的 0。
3. 字串 `strip()` / `upper()` 回傳新值；`list.append()` 就地修改 List。
4. 複雜題拆成：結構驗證 → 欄位驗證 → 單筆整合 → 多筆過濾。
5. 字串掃描使用「狀態變數」處理連續區段；大量輸出字串以 `list + join` 組裝。

## 六、建議重做（不看提示）

- 15～20 分鐘內從空白檔案獨立完成 `parse_inference_logs`，自行設計合法／非法／空輸入測試。
- 10 分鐘內獨立寫出 `mask_numeric_runs`，並說出時間、空間複雜度。
- 寫完主動檢查 `split`、`None`、`return`、ASCII、`0` 等錯誤高發點。
