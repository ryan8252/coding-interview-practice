# Coding Interview Practice — Current State

這份檔案用來讓新的 ChatGPT 對話可以快速接續目前的訓練狀態。

## 目前訓練規則

- 每天至少 3 題 **全新題目**。
- 複習題不計入每天 3 題的新題額度。
- 出題時只給：題號、題名、難度。
- **不要事前告訴 Topic / Pattern / 解法方向。**
- 可以查 Python / C / C++ / Java 語法、API、資料結構怎麼使用。
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
- Running Minimum / One Pass
- Two Pointers / in-place array 操作（已有數次無提示成功）
- Binary Search（已有無提示成功，但仍需要換題持續驗證）
- Sliding Window（已有無提示成功，但仍需要換題持續驗證）

正在建立中的能力：

- **Linked List**
  - Reverse Linked List 已能無提示複習成功
  - Remove Linked List Elements 新題已能無提示完成
  - Linked List Cycle 已從第一次需要 Hint / constraint workaround，進步到能用 C++ 無提示寫出 Floyd slow/fast
  - Intersection of Two Linked Lists 已能自行想到「記錄 A 的 node，再走 B 找同一 node」；但 traversal 時仍再次漏掉 pointer 前進，需要 Hint 1
  - Merge Two Sorted Lists 的 `dummy` + `tail` 是目前最需要再驗證是否真正內化的技巧
- **DP / recurrence**
  - 70 Climbing Stairs 第一次接觸 recurrence 類型就能無提示完成
  - 目前只有一次成功，還不能視為穩定能力，之後需用不同 Easy 題驗證

目前最需要注意的基本錯誤：

- Linked List traversal 不要漏掉 `cur = cur.next`
- `ListNode` 的 identity 與 `node.val` 不同；intersection / visited node 類題應比較或儲存 node 本身

## 最近重要紀錄

### Day 6 — 2026-09-14

- 704 Binary Search：B，8:44；有搜尋 implementation
- 141 Linked List Cycle：B，18:28；拿 Hint，最後先用 node 上限 workaround，之後學 Set 與 Floyd
- 977 Squares of a Sorted Array：A，10:44
- Linked List traversal 基礎補強

### Day 7 — 2026-09-15

- 21 Merge Two Sorted Lists：C，43:22。前 40 分鐘卡住，之後學 `dummy` + `tail`，理解 `return dummy.next`
- 448 Find All Numbers Disappeared in an Array：B，16:16。先獨立完成 O(n) extra-space 解法；O(1) space 的正負號 in-place marking 需要提示
- 88 Merge Sorted Array：A，15:50。無提示，自己從尾端往前原地合併
- 206 Reverse Linked List 複習：A，10:44，用 C 自己重做

### Day 8 — 2026-09-16

新題：

- 203 Remove Linked List Elements：A，21:55，Python，無 Hint
- 724 Find Pivot Index：A，5:39，無 Hint
- 392 Is Subsequence：A，約 5:00，Python，忘記計時，無 Hint

複習：

- 1 Two Sum：A，C++，約 14 分鐘有效時間；只查 `unordered_map` / return 等語法
- 121 Best Time to Buy and Sell Stock：A，Java，約 3 分鐘，忘記計時

### Day 9 — 2026-09-17

新題：

- 160 Intersection of Two Linked Lists：B，19:20，Python。核心方向自己想到，但 traversal / return 邏輯拿 Hint 1 才補完整
- 169 Majority Element：A，11:59，Python。dictionary frequency counting，無 Hint
- 70 Climbing Stairs：A，9:39，Python。自行找到 recurrence，無 Hint

複習：

- 141 Linked List Cycle：A，7:56，C++。無 Hint 寫出 Floyd slow/fast，O(n) time / O(1) space

## 出題策略

接下來仍以 Easy 為主，逐步擴充題型；每天至少 3 題新題。

- Linked List 可以持續安排短小新題或複習，但一天不要塞太多
- 優先驗證 `dummy` / `tail` 是否能在新情境自己想到
- traversal 類題持續注意 pointer 是否真的往後移
- Binary Search、Sliding Window、Two Pointers 要用不同新題再次驗證 pattern recognition
- DP / recurrence 已出現第一次無提示成功，之後安排新的 Easy 題驗證，但不要事前透露是 DP
- 複習可以刻意換 Python / C++ / C / Java，語法可查，但演算法核心仍需自己完成

## 新對話接續方式

在新的 ChatGPT 對話中，可以直接說：

> 請讀取 GitHub repo `ryan8252/coding-interview-practice` 的 `CURRENT_STATE.md`、`progress.md` 和最近的 `days/` 紀錄，然後繼續我的每日 coding interview 練習。

這樣即可從目前進度接續，不需要重新解釋整個訓練背景。
