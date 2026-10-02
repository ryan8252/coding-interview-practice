# Theory Review Progress

## 使用規則

- 每天原則上複習 **1 個小主題，約 20～30 分鐘**。
- 一次不要同時塞 OS、C++、Networking 等多個大主題。
- 完成後以 A / B / C / D 評分。
- B / C / D 主題要安排之後的 active recall 複習。
- 如果某個 coding 題暴露出資料結構或語言基礎缺口，優先加入這裡。
- 每次理論複習最後加一題小型程式實作，實作表現也納入評分。

## 評分

| 等級 | 定義 |
|---|---|
| A | 不看筆記能完整解釋，並能回答延伸問題 |
| B | 主概念懂，但部分細節或例子需要提醒 |
| C | 看過、聽得懂，但不能自己完整解釋 |
| D | 基本概念仍不理解 |

## 複習紀錄

| 日期 | 類別 | 主題 | 時間 | 評價 | 主要弱點 / 學到什麼 | 下次複習 |
|---|---|---|---:|---|---|---|
| 2026-10-01 | C++ | Pointer / Reference / Object Lifetime | 約 25–30 分鐘 | A | 能分辨 object、pointer、reference；理解 `T* p` 只建立 pointer、不建立 T object；理解 `&x`、`*p`、`p->member`；理解 pass-by-value / reference；能解釋 dangling pointer 與 local/dynamic object lifetime。中途曾把 `Student* q = p` 誤認為 q 指向 p，經 tracing 後已修正。 | 2026-10-08 左右做一次短 Active Recall |
| 2026-10-02 | Data Structures | Hash Table basics：hash function / bucket / collision / Separate Chaining / Linear Probing / tombstone | 約 45–60 分鐘 | B | 概念題能自行解釋平均 O(1)、最差 O(n)、chaining vs probing，以及 EMPTY 與 DELETED 的差異。完成固定大小 Linear Probing HashSet 實作，但實作過程需要多次 Hint 修正 OR/AND、probe 上限、index 計算、duplicate key、tombstone reuse 與 sentinel；另學到 Python `for...else` 與 `object()` sentinel。Load Factor 尚未學。 | 2026-10-05～10-07：不看筆記重新實作 Linear Probing HashSet，特別測 deletion + duplicate add |

## 下一個優先主題

優先候選：
1. C++ — Stack vs Heap / dynamic allocation（補完 10/01 尚未完整測過的部分）
2. Operating System — Process vs Thread
3. Data Structures — Hash Table 複習：從零實作 Linear Probing + tombstone；之後補 Load Factor / resize
4. C++ — STL containers / const / pass-by-value vs pass-by-reference
5. Data Structures — Stack / Queue / Heap 的操作與 complexity
