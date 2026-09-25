# Coding Interview Practice — Current State

這份檔案用來讓新的 ChatGPT 對話可以快速接續目前的訓練狀態。

## 目前訓練規則

- **每次出題前先讀 `PROBLEM_TRACKER.md`。它是題目去重與複習安排的主要索引。**
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
- DP / recurrence：70、746、198 都能無提示完成，基礎 recurrence 已開始穩定；64 Minimum Path Sum 與 120 Triangle 也已能無提示完成 min-DP，顯示 state / transition 能力開始擴展；213 House Robber II 在「環狀 constraint -> 拆兩個線性 case」上仍需要核心提示；322 Coin Change 對多 transition / unbounded min-DP 仍需無提示重做。120 的 O(n) space follow-up 最後看了 GPT 完整解法，因此空間壓縮尚不能算已獨立掌握
- Binary Tree：100 首次需要查 traversal；226 已能無查詢自行 traversal；543 在 bottom-up depth aggregation 上需要主要提示；104 Maximum Depth 與 112 Path Sum 已能無提示完成；110 Balanced Binary Tree 更進一步自行用 iterative stack + dictionary 完成 child -> parent depth aggregation，表示 postorder / bottom-up 能力已有無提示成功紀錄
- Binary Search：278 First Bad Version 與 367 Valid Perfect Square 都能無查詢自行完成，較 69 Sqrt(x) 時的 boundary 問題已有明顯進步

正在建立中的能力：

- **Linked List**
  - Reverse Linked List 已能無提示複習成功
  - Remove Linked List Elements 新題已能無提示完成
  - Linked List Cycle 已從第一次需要 Hint / constraint workaround，進步到能用 C++ 無提示寫出 Floyd slow/fast
  - Middle of the Linked List 已能把 slow/fast 遷移到新情境
  - Intersection of Two Linked Lists 核心方向能自己想到，但 traversal 時曾漏掉 pointer 前進
  - Merge Two Sorted Lists 的 `dummy + tail` 複習已能自行重現
  - 1290 Convert Binary Number in a Linked List to Integer 已能無提示完成 traversal，且正確維護 `head = head.next`，再次驗證基本 traversal 已較穩
- **Sliding Window**
  - 固定長度 Easy 已無提示成功
  - 3 Longest Substring Without Repeating Characters 已能自己維護合法 window，但目前是 O(n²) / O(1) 版本
  - 後續要練習用額外資料結構把內層掃描消掉，提升到 O(n)
- **Binary Search boundary**
  - 69 Sqrt(x) 曾需要 Hint 2 才辨認 Binary Search，且最後回傳 boundary 出錯
  - 278 First Bad Version 已能無提示自行完成 first-true 類 binary search
  - 還需要持續驗證不同 boundary 形式
- **C++ pointer / object 基礎**
  - 21 Merge Two Sorted Lists 與 203 Remove Linked List Elements 的演算法核心都能自行重現
  - 但兩次都曾先寫出未初始化 `ListNode* dummy;`，之後才詢問 GPT debug
  - 已理解：
    - `ListNode dummy;` 會建立 local object
    - `ListNode* p = &dummy;` 讓 pointer 指向該 object
    - `ListNode* p = new ListNode();` 會建立 dynamic object 並回傳 pointer
    - 單純 `ListNode* p;` 只宣告 pointer，沒有建立 object
  - 之後仍需再次無查詢驗證是否真正內化

目前最需要注意的基本錯誤：

- Linked List traversal 不要漏掉 `cur = cur.next`
- `ListNode` 的 identity 與 `node.val` 不同；intersection / visited node 類題應比較或儲存 node 本身
- C++ 中宣告 pointer 不代表已建立 object；使用 `ptr->member` 前要先確認 pointer 已指向有效 object
- Binary Search 不要機械式 `return mid`；要理解 loop invariant 與 `start/end` 最後各代表什麼

## 最近重要紀錄

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

### Day 12 — 2026-09-20

新題：
- 226 Invert Binary Tree：A，11:17，Python，無查詢、無 Hint；自行用 stack traversal 完成
- 278 First Bad Version：A，16:15，Python，無查詢、無 Hint；自行寫出 first-true binary search
- 198 House Robber：A，9:41，Medium，Python，無查詢、無 Hint；自行得到 `m[i] = max(nums[i] + m[i-2], m[i-1])`

複習：
- 203 Remove Linked List Elements：A，6:28，C++。演算法與 dummy/tail 使用自行完成；先寫錯 `ListNode* dummy;` 後才詢問 GPT「如何建立 dummy node」，再次暴露 pointer/object 初始化仍未完全內化



### Day 13 — 2026-09-21

新題：
- 543 Diameter of Binary Tree：C，51:52；GPT 提供主要 depth / diameter 結構
- 209 Minimum Size Subarray Sum：A，23:20，Medium；無提示自行完成 O(n) Sliding Window
- 202 Happy Number：A，7:41；無提示自行用 visited-state 偵測 cycle



### Day 14 — 2026-09-22

新題：
- 104 Maximum Depth of Binary Tree：A，12:43；無提示、無查詢，自行完成 Tree depth
- 367 Valid Perfect Square：A，13:55；無提示、無查詢，自行完成 Binary Search
- 213 House Robber II：C，33:31；Hint 2 明確指出拆成「不搶第一間」與「不搶最後一間」兩次普通 House Robber，再取最大值



### Day 15 — 2026-09-23

新題：
- 83 Remove Duplicates from Sorted List：A，7:10；無提示、無查詢
- 322 Coin Change：C，23:17；原本完全沒方向，Google 演算法後完成 DP
- 112 Path Sum：A，17:20；無提示、無查詢，自行維護 traversal 中的 path sum

未完成：
- 234 Palindrome Linked List：本次未作答，不計入今日新題額度

### Day 16 — 2026-09-24

新題：
- 110 Balanced Binary Tree：A，13:25；無提示，自行用 iterative stack + dictionary 完成 bottom-up depth aggregation
- 27 Remove Element：A，39:15；無提示，自行完成 O(n) / O(1) in-place 處理
- 64 Minimum Path Sum：A，約 25:00；忘記一開始計時，無提示自行完成 2D min-DP

### Day 17 — 2026-09-25

> 744 與 1290 雖實際提交跨到 9/26 00:xx，但依使用者指定仍算 9/25。2026-09-26 今日練習尚未開始。

新題：
- 120 Triangle：A，20:22；原題 2D DP 無提示自行完成。O(n) space follow-up 在 Accepted 後由 GPT 直接提供完整解法，optimization 另列學習內容
- 744 Find Smallest Letter Greater Than Target：A，9:43；核心自行完成，只因不熟 Python 語法詢問 GPT
- 1290 Convert Binary Number in a Linked List to Integer：A，13:02；完全自己完成

複習：
- 35 Search Insert Position：A（複習），7:12，C++；過去已用 Python 做過
- 643 Maximum Average Subarray I：A（複習），4:40，C++；過去已用 Python 做過

## 出題策略

- 每天至少 3 題新題；可持續採用 **2 Easy + 1 基礎 Medium**。
- Medium 卡約 20～30 分鐘後可開始 Hint；不要求第一次就完全獨立解出。
- 3 Longest Substring Without Repeating Characters 之後安排重做，目標是自行從 O(n²) 改成 O(n) sliding window；209 已證明可以獨立完成 O(n) window。
- Binary Tree 的 traversal、path state、bottom-up depth aggregation 都已有無提示成功紀錄；之後用不同 postorder / child -> parent 題型驗證穩定性。
- Binary Search 278 已顯示 boundary 有進步，之後再用 last-true / first-false 或 search insert 類題驗證。
- DP / recurrence 基礎 recurrence 已相對穩定；64、120 顯示一般 min-DP 已有無提示成功，但 213 的 case split、322 的多 transition/unbounded min-DP 仍需補強。之後安排 House Robber II 與 Coin Change 無提示重做；120 的 O(n) space optimization 也要隔一段時間再無提示驗證。
- Linked List 繼續用不同題型驗證 dummy / tail、traversal、slow/fast。
- **C++ pointer/object 初始化仍需安排短複習**，直到能無查詢分辨 object、address、pointer、`new`。
- 複習可刻意換 Python / C++ / C / Java；語法可查，但演算法核心仍需自己完成。
- **出新題前必須先檢查 `PROBLEM_TRACKER.md`。** 已出現在「已完成題目總表」中的題目不得再當新題；若安排重做只能標成複習，且不計入每日 3 題新題。再搭配 `progress.md` 與最近 `days/` 查看詳細紀錄。35 與 643 在 Day 17 曾誤重複，因此當天只算複習。

## 新對話接續方式

在新的 ChatGPT 對話中，可以直接說：

> 請讀取 GitHub repo `ryan8252/coding-interview-practice` 的 `PROBLEM_TRACKER.md`、`CURRENT_STATE.md`、`progress.md` 和最近的 `days/` 紀錄，然後繼續我的每日 coding interview 練習。出新題前先用 `PROBLEM_TRACKER.md` 去重。

這樣即可從目前進度接續，不需要重新解釋整個訓練背景。
