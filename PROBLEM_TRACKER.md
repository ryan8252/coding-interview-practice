# Coding Interview Problem Tracker

> **用途：這是出題去重與複習安排的主要索引。**
>
> 每次安排「全新題目」前，**必須先讀這份檔案**。已出現在「已完成題目總表」中的題目，不得再當成全新題目；若要再次安排，只能明確標成「複習題」，且不計入每天至少 3 題的新題額度。
>
> 更新日期：2026-09-26  
> 目前進度：Day 17（2026-09-25）完成；**2026-09-26 / Day 18 尚未開始**。

## 已完成題目總表

| # | 題目 | 難度 | 首次完成 | 目前最佳評價 | 備註 |
|---:|---|---|---|---|---|
| 1 | Two Sum | Easy | 2026-09-09 | A | 9/10 Hash Map O(n) 重做；9/16 C++ 複習 |
| 3 | Longest Substring Without Repeating Characters | Medium | 2026-09-19 | B | 目前版本 O(n²)；列入複習，目標 O(n) |
| 14 | Longest Common Prefix | Easy | 2026-09-18 | A |  |
| 20 | Valid Parentheses | Easy | 2026-09-09 | A | 9/12 C++ 無提示重做 |
| 21 | Merge Two Sorted Lists | Easy | 2026-09-15 | A | 初次 C；9/18 C++ 複習 A，但 dummy pointer 初始化仍需驗證 |
| 26 | Remove Duplicates from Sorted Array | Easy | 2026-09-12 | A |  |
| 27 | Remove Element | Easy | 2026-09-24 | A |  |
| 35 | Search Insert Position | Easy | 2026-09-13 | A | 9/25 C++ 複習 |
| 64 | Minimum Path Sum | Medium | 2026-09-24 | A |  |
| 69 | Sqrt(x) | Easy | 2026-09-19 | C | Binary Search boundary 曾需 Hint 2 |
| 70 | Climbing Stairs | Easy | 2026-09-17 | A |  |
| 83 | Remove Duplicates from Sorted List | Easy | 2026-09-23 | A |  |
| 88 | Merge Sorted Array | Easy | 2026-09-15 | A |  |
| 100 | Same Tree | Easy | 2026-09-19 | B | 首次 Tree，曾查 traversal；後續 Tree 已明顯進步 |
| 104 | Maximum Depth of Binary Tree | Easy | 2026-09-22 | A |  |
| 110 | Balanced Binary Tree | Easy | 2026-09-24 | A |  |
| 112 | Path Sum | Easy | 2026-09-23 | A |  |
| 120 | Triangle | Medium | 2026-09-25 | A | 2D DP 自行完成；O(n) extra-space follow-up 看完整解法 |
| 121 | Best Time to Buy and Sell Stock | Easy | 2026-09-09 | A | 9/12 C、9/16 Java 複習成功 |
| 125 | Valid Palindrome | Easy | 2026-09-10 | A | 9/19 C++ 複習 |
| 141 | Linked List Cycle | Easy | 2026-09-14 | A | 初次 B；9/17 C++ Floyd 無提示重做 |
| 160 | Intersection of Two Linked Lists | Easy | 2026-09-17 | B | 核心方向自行想到；traversal 曾漏 pointer 前進 |
| 167 | Two Sum II - Input Array Is Sorted | Medium | 2026-09-11 | B | 當時事前得到 Two Pointers 方向；後續 Two Pointers 已多次 A |
| 169 | Majority Element | Easy | 2026-09-17 | A |  |
| 198 | House Robber | Medium | 2026-09-20 | A |  |
| 202 | Happy Number | Easy | 2026-09-21 | A |  |
| 203 | Remove Linked List Elements | Easy | 2026-09-16 | A | 9/20 C++ 複習時 dummy pointer 初始化再次出錯 |
| 206 | Reverse Linked List | Easy | 2026-09-13 | A | 初次 B；9/15 C 無提示複習 A |
| 209 | Minimum Size Subarray Sum | Medium | 2026-09-21 | A |  |
| 213 | House Robber II | Medium | 2026-09-22 | C | case split 需 Hint 2；需無提示重做 |
| 217 | Contains Duplicate | Easy | 2026-09-10 | A |  |
| 226 | Invert Binary Tree | Easy | 2026-09-20 | A |  |
| 242 | Valid Anagram | Easy | 2026-09-11 | A |  |
| 278 | First Bad Version | Easy | 2026-09-20 | A |  |
| 283 | Move Zeroes | Easy | 2026-09-11 | A | 初次 B；9/13 O(1) extra space 複習 A |
| 322 | Coin Change | Medium | 2026-09-23 | C | Google 演算法後完成；需無提示重做 |
| 367 | Valid Perfect Square | Easy | 2026-09-22 | A |  |
| 392 | Is Subsequence | Easy | 2026-09-16 | A |  |
| 448 | Find All Numbers Disappeared in an Array | Easy | 2026-09-15 | B | O(1) marking 需要提示 |
| 543 | Diameter of Binary Tree | Easy | 2026-09-21 | C | bottom-up depth 結構需主要提示；110 已顯示進步 |
| 643 | Maximum Average Subarray I | Easy | 2026-09-13 | A | 9/25 C++ 複習 |
| 704 | Binary Search | Easy | 2026-09-14 | B | 當時搜尋 binary search implementation；後續 Binary Search 已多次 A |
| 724 | Find Pivot Index | Easy | 2026-09-16 | A |  |
| 744 | Find Smallest Letter Greater Than Target | Easy | 2026-09-25 | A | 只查 Python 語法 |
| 746 | Min Cost Climbing Stairs | Easy | 2026-09-18 | A |  |
| 876 | Middle of the Linked List | Easy | 2026-09-18 | A |  |
| 977 | Squares of a Sorted Array | Easy | 2026-09-14 | A |  |
| 1290 | Convert Binary Number in a Linked List to Integer | Easy | 2026-09-25 | A |  |

**目前已完成：48 題不同 LeetCode 題目。**

## 需要複習的題目

> 複習題不計入每日 3 題新題額度。完成複習後更新「最近複習 / 結果 / 狀態」，確認已穩定者可改成「已解除」。

| 優先度 | # | 題目 | 為什麼需要複習 | 下次複習目標 | 狀態 |
|---|---:|---|---|---|---|
| 高 | 3 | Longest Substring Without Repeating Characters | 第一次拿 Hint 1，完成的是 O(n²) window | 無提示自行做到 O(n) | 待複習 |
| 高 | 213 | House Robber II | circular constraint → case split 需 Hint 2 | 無提示自行想到拆成兩個 linear case | 待複習 |
| 高 | 322 | Coin Change | 完全沒方向後 Google 演算法 | 無提示自行定義 state / transition，完成 min-DP | 待複習 |
| 中 | 120 | Triangle | 原題 A，但 O(n) extra-space follow-up 由 GPT 直接給完整解法 | 無提示把 2D DP 壓成 O(n) space | 待複習 |
| 中 | 21 | Merge Two Sorted Lists | 演算法已 A，但 C++ 曾寫未初始化 `ListNode* dummy;` | 用 C++ 無查詢正確建立 dummy object / pointer | 待複習 |
| 中 | 203 | Remove Linked List Elements | C++ 複習時再次出現未初始化 dummy pointer | 用 C++ 無查詢完成，且不再犯 pointer/object 初始化錯誤 | 待複習 |
| 中 | 69 | Sqrt(x) | 曾需 Hint 2 才辨認 Binary Search，且 final boundary 出錯 | 無提示完成並正確解釋 loop 結束後 boundary | 待複習 |
| 低 | 448 | Find All Numbers Disappeared in an Array | O(1) marking 技巧曾需要提示 | 無提示自行做到 O(1) extra space | 待複習 |
| 低 | 543 | Diameter of Binary Tree | bottom-up depth aggregation 曾需主要提示 | 無提示完成 child → parent aggregation | 待複習 |
| 低 | 160 | Intersection of Two Linked Lists | traversal / node identity 曾卡住 | 無提示完成並避免漏 pointer 前進 | 待複習 |

## 已出過但未完成／跳過

> 這些題**不要誤記成已完成**。除非明確要重試，否則也不要拿來當隨機的新題。

| # | 題目 | 狀態 | 備註 |
|---:|---|---|---|
| 234 | Palindrome Linked List | 未完成 | 9/23 曾出題但未作答 |
| 243 | Shortest Word Distance | 跳過 | LeetCode Premium，需要付費 |
| 1213 | Intersection of Three Sorted Arrays | 跳過 | LeetCode Premium，需要付費 |

## 維護規則

- 每完成一個**第一次做的新題**：加入「已完成題目總表」。
- 同一題重做：不要新增第二列；更新備註與最佳評價即可。
- 需要再次驗證的題：加入「需要複習的題目」。
- 複習成功且能力已穩定：把狀態改為「已解除」，不要再頻繁安排。
- 每日出題前：
  1. 先讀本檔案。
  2. 新題不得出現在「已完成題目總表」。
  3. 「已出過但未完成／跳過」也不要隨機再次安排。
  4. 複習題必須明確標成複習，且**不計入每天至少 3 題新題**。
  5. 完成當天紀錄後，同步更新本檔案、`progress.md`、`CURRENT_STATE.md` 與對應 `days/YYYY-MM-DD.md`。
