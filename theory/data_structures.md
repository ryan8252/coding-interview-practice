# Data Structures

## 優先主題

- [ ] Hash Table
  - [x] Hash function
  - [x] Bucket
  - [x] Collision
  - [x] Separate Chaining
  - [x] Linear Probing
  - [ ] Load Factor
- [ ] Array / Dynamic Array
- [ ] Linked List
- [ ] Stack
- [ ] Queue / Deque
- [ ] Heap / Priority Queue
- [ ] Binary Tree / BST
- [ ] Graph
- [ ] Trie（低優先）

## 目前已知弱點

### Hash Table

2026-10-02 已完成 Hash Table 基礎概念複習：
- 能說明 hash function 將 key 映射到 bucket/index。
- 能說明 collision：不同 key 可能映射到相同 bucket。
- 能區分 Separate Chaining 與 Linear Probing。
- 能說明平均 lookup 接近 O(1)，碰撞嚴重時最差可到 O(n)。
- Linear Probing 搜尋時：遇到 EMPTY 可停止；遇到 DELETED/tombstone 必須繼續。
- 理解刪除不能直接改成 EMPTY，否則會切斷 probing search path。
- Load Factor / resize 尚未學。

實作仍需補強：
- 固定 probe 次數，避免 table full 時 infinite loop。
- 正確處理 duplicate key。
- tombstone 不能看到就立刻重用：新增時要先記住第一個 tombstone，繼續確認後面沒有相同 key。
- Python sentinel 可用 `self.deleted = object()`，用 identity 區分 EMPTY / DELETED / OCCUPIED。
- Python `for...else` 可處理「完整掃完且沒有 break」的情況。

## 筆記

### Hash Table 基本流程

`hash(key)` 決定起始 bucket。Collision handling 常見方式：
- Separate Chaining：同一 bucket 存多個元素，例如 list / linked list。
- Linear Probing：bucket 被占用時依 probing sequence 往後找，並用 modulo wrap around。

Linear Probing 的三種 slot state：
- EMPTY：從未使用；search 遇到可直接判定不存在。
- OCCUPIED：存放有效 key。
- DELETED：曾經使用但已刪除；search 不能停止，add 可在確認沒有 duplicate 後重用。

### 2026-10-02 實作錯誤紀錄

1. `while slot != None or slot != deleted` 會永遠為 True；要理解 AND / OR 的布林條件。
2. 無上限的 `while` 在 table full 時會 infinite loop；固定大小 table 最多 probe SIZE 次。
3. probing index 應由固定 `start` 計算：`(start + step) % SIZE`，不要在每輪累加已變動的 index。
4. remove / contains 遇到 EMPTY 可提前停止；DELETED 必須繼續。
5. add 遇到 DELETED 不能立刻插入，否則後面已有同 key 時會製造 duplicate；先記第一個 tombstone。
6. Python 的 tombstone 可用獨立 `object()` sentinel，而不是和正常 key 共用值。

## 自測

- Hash table 為什麼平均可以做到 O(1) lookup？
- Collision 為什麼一定可能發生？
- Chaining 和 Linear Probing 的差異？
- Linear Probing 為什麼需要 tombstone？
- add 遇到 tombstone 為什麼不能一定立刻插入？
- Load factor 太高會發生什麼？（待學）
- Heap 和 sorted array 的用途差在哪？

## 複習紀錄

| 日期 | 主題 | 評價 | 待補強 |
|---|---|---|---|
| 2026-10-02 | Hash Table basics + Linear Probing HashSet implementation | B | 從零重寫 add/remove/contains；duplicate + tombstone reuse；Load Factor / resize |
