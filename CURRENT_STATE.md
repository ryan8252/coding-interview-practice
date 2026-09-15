# Coding Interview Practice — Current State

這份檔案用來讓新的 ChatGPT 對話可以快速接續目前的訓練狀態。

## 目前訓練規則

- 每天至少 3 題 **全新題目**。
- 複習題不計入每天 3 題的新題額度。
- 出題時只給：題號、題名、難度。
- **不要事前告訴 Topic / Pattern / 解法方向。**
- 可以查 Python / C / C++ 語法、API、資料結構怎麼使用。
- 不可以直接搜尋題目 solution 或「這題要用什麼演算法」。
- 卡住約 10～20 分鐘後，使用者會主動要求 `Hint 1`；提示要逐層給，不要一次透露核心答案。
- 每題完成後，根據是否拿提示、查了什麼、程式碼品質與時間，記錄 A/B/C/D。
- 練習紀錄以中文為主，演算法術語可保留英文。

## 評分概念

- A：演算法核心自己想出，只查語法/API。
- B：拿到小提示或部分演算法方向後完成。
- C：需要主要解題結構／核心技巧提示後才能完成。
- D：看過解法後仍沒有理解。

## 目前能力觀察

相對較穩：

- Array 基本操作
- Hash Map / Frequency Counting
- Stack
- Binary Search（已出現無提示成功）
- Sliding Window（已出現無提示成功）
- Two Pointers / in-place array 操作（已有數次無提示成功）
- Running Minimum / One Pass

目前最需要補強：

- **Linked List 基礎與 pointer 操作**
  - traversal 曾忘記 `cur = cur.next`
  - `ListNode` class 定義不熟
  - Reverse Linked List 已能複習成功
  - Merge Two Sorted Lists 新題仍會卡住，dummy node / tail 是剛學的新技巧
  - Linked List Cycle 已學過 Set 與 Floyd slow/fast，但第一次自己做時利用 constraint workaround

## 最近重要紀錄

### Day 5 — 2026-09-13

- 35 Search Insert Position：A，11:59
- 206 Reverse Linked List：B，15:29（查了需要幾個 ptr）
- 643 Maximum Average Subarray I：A，4:45
- 283 Move Zeroes 複習：A，17:53，已從 queue 解法進步到 O(1) extra space

### Day 6 — 2026-09-14

- 704 Binary Search：完成
- 141 Linked List Cycle：需要 Hint，最後先利用題目最多 10000 nodes 的 constraint 做 workaround；之後討論 Set 與 Floyd slow/fast
- 977 Squares of a Sorted Array：完成
- Linked List traversal 基礎補強

### Day 7 — 2026-09-15

- 21 Merge Two Sorted Lists：C，43:22。前 40 分鐘卡住，之後學 `dummy` + `tail`，理解 `return dummy.next`
- 448 Find All Numbers Disappeared in an Array：B，16:16。先獨立完成 O(n) extra-space 解法；O(1) space 的正負號 in-place marking 需要提示
- 88 Merge Sorted Array：A，15:50。無提示，自己從尾端往前原地合併
- 206 Reverse Linked List 複習：A，10:44，用 C 自己重做
- 1213 Intersection of Three Sorted Arrays 因為 Premium 未做，已用 88 替換

## 出題策略

接下來仍以 Easy 為主，但逐步擴充題型；每天至少 3 題新題。Linked List 可以持續安排短小基礎練習或新題，但不要一次塞太多，因為目前是明顯弱區。

要持續驗證：

- Binary Search 是否能換題後仍無提示辨認
- Sliding Window 是否能再次無提示辨認
- Two Pointers 是否能在新題無提示使用
- Linked List 的 traversal、dummy、tail、slow/fast、reverse 是否逐步內化

## 新對話接續方式

在新的 ChatGPT 對話中，可以直接說：

> 請讀取 GitHub repo `ryan8252/coding-interview-practice` 的 `CURRENT_STATE.md`、`progress.md` 和最近的 `days/` 紀錄，然後繼續我的每日 coding interview 練習。

這樣即可從目前進度接續，不需要重新解釋整個訓練背景。
