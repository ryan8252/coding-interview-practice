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
- 從 Day 11 起開始逐步混入 **基礎 Medium**；原則上可朝 2 Easy + 1 Medium 前進，但遇到全新領域時先用 Easy 建基礎。

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
- Sliding Window：Easy 固定長度題已無提示成功；Medium 3 已能自己維護合法 window，但目前是 O(n²) / O(1) 版本
- DP / recurrence：70、746 連續兩天無提示成功，開始形成能力

正在建立中的能力：

- **Linked List**
  - Reverse Linked List 已能無提示複習成功
  - Remove Linked List Elements 新題已能無提示完成
  - Linked List Cycle 已從第一次需要 Hint / constraint workaround，進步到能用 C++ 無提示寫出 Floyd slow/fast
  - Middle of the Linked List 已能把 slow/fast 遷移到新情境
  - Intersection of Two Linked Lists 核心方向能自己想到，但 traversal 時曾漏掉 pointer 前進
  - Merge Two Sorted Lists 的 `dummy + tail` 複習已能自行重現
- **Binary Search**
  - Search Insert Position 曾無提示成功
  - 69 Sqrt(x) 需要 Hint 2 才辨認 Binary Search
  - 能寫 `start/end/mid` 主體，但 boundary、最大合法值 / 最小合法值、loop 結束後應回傳 `start` / `end` / `mid` 還不穩
- **Binary Tree**
  - Day 11 第一次正式接觸
  - 100 Same Tree 查過 tree traversal 與 Python stack 後完成
  - 目前要先建立 `node.val` / `node.left` / `node.right`、DFS/stack、`None` handling
- **Medium 題**
  - 3 Longest Substring Without Repeating Characters：B，50:30
  - Hint 1 後自行設計 O(n²) / O(1) space 的 sliding-window 解法並 Accepted
  - 還需要學會用額外資料結構把內層掃描消掉，提升到 O(n)
- **C++ pointer / object 基礎**
  - 21 Merge Two Sorted Lists 複習時，演算法核心可自行重現
  - 但曾寫出 `ListNode* dummy;` 後直接令 `tail=dummy`，顯示「宣告 pointer 不等於建立 object」仍不熟
  - 後續需複習 stack object + `&`、heap object + `new`、使用 `->` 前 pointer 必須指向有效 object

目前最需要注意的基本錯誤：

- Linked List traversal 不要漏掉 `cur = cur.next`
- `ListNode` 的 identity 與 `node.val` 不同；intersection / visited node 類題應比較或儲存 node 本身
- C++ 中宣告 pointer 不代表已建立 object；使用 `ptr->member` 前要先確認 pointer 已指向有效 object
- Binary Search 不要機械式 `return mid`；要先理解 loop 結束時 `start` / `end` 各代表什麼

## 最近重要紀錄

### Day 9 — 2026-09-17

新題：
- 160 Intersection of Two Linked Lists：B，19:20
- 169 Majority Element：A，11:59
- 70 Climbing Stairs：A，9:39

複習：
- 141 Linked List Cycle：A，7:56，C++，Floyd slow/fast

### Day 10 — 2026-09-18

新題：
- 876 Middle of the Linked List：A，5:50
- 14 Longest Common Prefix：A，11:18
- 746 Min Cost Climbing Stairs：A，7:23

複習：
- 21 Merge Two Sorted Lists：A，10:22，C++。dummy/tail 核心自行重現；C++ pointer 初始化需補強

### Day 11 — 2026-09-19

新題：
- 3 Longest Substring Without Repeating Characters：B，50:30，Medium；Hint 1 後自行完成 O(n²) / O(1) window 解
- 100 Same Tree：B，26:27；第一次 Binary Tree，查 tree traversal / Python stack 後完成
- 69 Sqrt(x)：C，19:27；Hint 2 明確指出 Binary Search，之後 boundary / return end 再需說明

複習：
- 125 Valid Palindrome：A，12:48，C++

## 出題策略

- 每天至少 3 題新題；開始逐步採用 **2 Easy + 1 基礎 Medium**，但全新領域第一次接觸時可以先用 Easy。
- Medium 卡約 20～30 分鐘後可開始 Hint；不要求第一次就完全獨立解出。
- 3 Longest Substring Without Repeating Characters 之後安排重做，目標是自行從 O(n²) 改成 O(n) sliding window。
- Binary Tree 接下來安排短小 Easy 題，確認 traversal 是否能不再查資料自行重現。
- Binary Search 安排 boundary 類練習，特別是 first/last valid 與 loop 結束後 `start/end` 語意。
- Linked List 繼續用不同題型驗證 dummy / tail、traversal、slow/fast。
- 安排 C++ pointer 初始化 / object vs pointer 的短複習，不算每日 3 題新題。
- 複習可刻意換 Python / C++ / C / Java；語法可查，但演算法核心仍需自己完成。

## 新對話接續方式

在新的 ChatGPT 對話中，可以直接說：

> 請讀取 GitHub repo `ryan8252/coding-interview-practice` 的 `CURRENT_STATE.md`、`progress.md` 和最近的 `days/` 紀錄，然後繼續我的每日 coding interview 練習。

這樣即可從目前進度接續，不需要重新解釋整個訓練背景。
