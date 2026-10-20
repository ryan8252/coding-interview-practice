# Coding Interview Problem Tracker

> **用途：這是出題去重與複習安排的主要索引。**
>
> 每次安排「全新題目」前，**必須先讀這份檔案**。已出現在「已完成題目總表」中的題目，不得再當成全新題目；若要再次安排，只能明確標成「複習題」，且不計入每天至少 3 題的新題額度。
>
> 更新日期：2026-10-20  
> 目前進度：Day 39（2026-10-20）完成。

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
| 58 | Length of Last Word | Easy | 2026-09-26 | A | 無提示、無查詢 |
| 62 | Unique Paths | Medium | 2026-09-26 | A | 無提示、無查詢；使用組合數解法 |
| 64 | Minimum Path Sum | Medium | 2026-09-24 | A |  |
| 69 | Sqrt(x) | Easy | 2026-09-19 | C | Binary Search boundary 曾需 Hint 2 |
| 70 | Climbing Stairs | Easy | 2026-09-17 | A |  |
| 83 | Remove Duplicates from Sorted List | Easy | 2026-09-23 | A |  |
| 88 | Merge Sorted Array | Easy | 2026-09-15 | A |  |
| 94 | Binary Tree Inorder Traversal | Easy | 2026-09-28 | A | 自己完成；目前使用 visited dictionary，額外 O(n) space |
| 100 | Same Tree | Easy | 2026-09-19 | B | 首次 Tree，曾查 traversal；後續 Tree 已明顯進步 |
| 104 | Maximum Depth of Binary Tree | Easy | 2026-09-22 | A |  |
| 110 | Balanced Binary Tree | Easy | 2026-09-24 | A |  |
| 111 | Minimum Depth of Binary Tree | Easy | 2026-09-26 | A | 無提示、無查詢；BFS |
| 112 | Path Sum | Easy | 2026-09-23 | A |  |
| 120 | Triangle | Medium | 2026-09-25 | A | 2D DP 自行完成；O(n) extra-space follow-up 看完整解法 |
| 121 | Best Time to Buy and Sell Stock | Easy | 2026-09-09 | A | 9/12 C、9/16 Java 複習成功 |
| 125 | Valid Palindrome | Easy | 2026-09-10 | A | 9/19 C++ 複習 |
| 136 | Single Number | Easy | 2026-09-28 | B | 有看提示；查 Python XOR 語法 |
| 1413 | Minimum Value to Get Positive Step by Step Sum | Easy | 2026-09-29 | A | 自己完成 |
| 141 | Linked List Cycle | Easy | 2026-09-14 | A | 初次 B；9/17 C++ Floyd 無提示重做 |
| 152 | Maximum Product Subarray | Medium | 2026-09-30 | B | 取得 max/min ending product 關鍵提示後自行完成 recurrence |
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
| 219 | Contains Duplicate II | Easy | 2026-09-30 | A | 自己完成；last-seen index |
| 226 | Invert Binary Tree | Easy | 2026-09-20 | A |  |
| 237 | Delete Node in a Linked List | Medium | 2026-09-29 | C | 因看不懂題意直接問 GPT；核心技巧由 GPT 解釋 |
| 242 | Valid Anagram | Easy | 2026-09-11 | A |  |
| 278 | First Bad Version | Easy | 2026-09-20 | A |  |
| 283 | Move Zeroes | Easy | 2026-09-11 | A | 初次 B；9/13 O(1) extra space 複習 A |
| 300 | Longest Increasing Subsequence | Medium | 2026-09-28 | C | O(n²) DP direction 自行想到；O(n log n) tails + binary search 經主要提示完成 |
| 322 | Coin Change | Medium | 2026-09-23 | A | 初次 C；2026-10-04 C++ 複習 15:32，核心 recurrence 無演算法提示重建成功；只查初始化與 sentinel return 語法 |
| 367 | Valid Perfect Square | Easy | 2026-09-22 | A |  |
| 374 | Guess Number Higher or Lower | Easy | 2026-09-27 | A | 自己完成 |
| 392 | Is Subsequence | Easy | 2026-09-16 | A |  |
| 448 | Find All Numbers Disappeared in an Array | Easy | 2026-09-15 | B | O(1) marking 需要提示 |
| 455 | Assign Cookies | Easy | 2026-09-29 | A | 自己完成 |
| 543 | Diameter of Binary Tree | Easy | 2026-09-21 | C | bottom-up depth 結構需主要提示；110 已顯示進步 |
| 643 | Maximum Average Subarray I | Easy | 2026-09-13 | A | 9/25 C++ 複習 |
| 680 | Valid Palindrome II | Easy | 2026-09-27 | C | 有看解答；需無提示重做 |
| 704 | Binary Search | Easy | 2026-09-14 | B | 當時搜尋 binary search implementation；後續 Binary Search 已多次 A |
| 705 | Design HashSet | Easy | 2026-09-30 | C | 詢問 GPT modulo / bucket / collision / chaining / linear probing 等核心概念 |
| 724 | Find Pivot Index | Easy | 2026-09-16 | A |  |
| 744 | Find Smallest Letter Greater Than Target | Easy | 2026-09-25 | A | 只查 Python 語法 |
| 746 | Min Cost Climbing Stairs | Easy | 2026-09-18 | A |  |
| 876 | Middle of the Linked List | Easy | 2026-09-18 | A |  |
| 931 | Minimum Falling Path Sum | Medium | 2026-09-27 | A | 只查 list.copy() 語法；O(n) space optimization 自行完成 |
| 977 | Squares of a Sorted Array | Easy | 2026-09-14 | A |  |
| 1290 | Convert Binary Number in a Linked List to Integer | Easy | 2026-09-25 | A |  |

| 139 | Word Break | Medium | 2026-10-01 | B | 6:05 有初步切字想法；22:30 H1 後改成保存多個 reachable index，47:25 Accepted；需無提示重做 state/model |
| 349 | Intersection of Two Arrays | Easy | 2026-10-01 | A | 排序 + two pointers 自行完成；Idea 1:00，Accepted 7:52；之後補出去重可直接利用排序後 ans[-1] |
| 733 | Flood Fill | Easy | 2026-10-01 | A | 自行辨認 traversal；Idea 2:57，第一次程式 11:14，Accepted 13:14；implementation 可再改 deque / enqueue 時標記 |

| 205 | Isomorphic Strings | Easy | 2026-10-02 | A | Idea 3:00，Accepted 10:08；雙向 mapping 自行完成 |
| 290 | Word Pattern | Easy | 2026-10-03 | A | Idea 1:11，Accepted 9:00；split + 雙向 mapping 自行完成 |
| 377 | Combination Sum IV | Medium | 2026-10-03 | A | Idea 3:17，Accepted 15:43；無 Hint 自行建立 1D counting DP |
| 416 | Partition Equal Subset Sum | Medium | 2026-10-02 | B | 1:05 自行完成 target=sum/2 reduction；H1 後建立 subset-sum DP，21:58 Accepted |
| 530 | Minimum Absolute Difference in BST | Easy | 2026-10-03 | A | Idea 1:00，Accepted 9:07；inorder 後比較相鄰值 |
| 572 | Subtree of Another Tree | Easy | 2026-10-02 | B | 2:10 原始方向正確；H1 後回到 traversal + Same Tree；38:10 Accepted |

| 55 | Jump Game | Medium | 2026-10-04 | A | Idea 1:21；4:08 從 reachable list 簡化為 farthest；8:04 Accepted |
| 91 | Decode Ways | Medium | 2026-10-05 | B | 12:11 H1 後建立 dp state；23:17 Accepted；需複習 state/recurrence |
| 101 | Symmetric Tree | Easy | 2026-10-04 | A | 9:32 發現需 mirror compare；10:07 Accepted |
| 225 | Implement Stack using Queues | Easy | 2026-10-05 | C | 核心解法完全問 AI；13:01 Accepted |
| 238 | Product of Array Except Self | Medium | 2026-10-06 | A | 5:07 發現不能除法後自行重建 prefix × suffix；30:45 Accepted |
| 257 | Binary Tree Paths | Easy | 2026-10-05 | C | 看答案後完成；24:36 Accepted；需複習 traversal + path state |
| 409 | Longest Palindrome | Easy | 2026-10-04 | A | Idea 1:46；6:44 Accepted |
| 700 | Search in a Binary Search Tree | Easy | 2026-10-06 | A | Idea 0:24；8:16 Accepted；利用 BST ordering |
| 1046 | Last Stone Weight | Easy | 2026-10-06 | B | 14:37 H1 指向可反覆取最大值的資料結構；15:58 Accepted；heapq API 查詢不算額外 Hint |

| 108 | Convert Sorted Array to Binary Search Tree | Easy | 2026-10-07 | A | Idea 4:36；15:31 Accepted；無 Hint，divide and conquer 自行完成 |
| 496 | Next Greater Element I | Easy | 2026-10-07 | B | 7:20 H1 後理解一次處理 nums2 建 next-greater map；30:39 Accepted；需複習 monotonic stack |
| 1143 | Longest Common Subsequence | Medium | 2026-10-07 | A | Idea 2:07；24:08 Accepted；只詢問 Python 2D list 初始化 aliasing bug，無演算法 Hint |

| 56 | Merge Intervals | Medium | 2026-10-11 | B | 4:26 H1 提示按 start 排序；7:12 自行形成合併 Idea；21:18 AC；sort API 查詢不算 Hint |
| 200 | Number of Islands | Medium | 2026-10-11 | A | 0:28 自行辨認 Graph Traversal；15:49 TLE 後有 implementation/debug 協助，19:31 AC；無演算法 Hint |
| 844 | Backspace String Compare | Easy | 2026-10-11 | A | 7:48 自行 stack 模擬 AC；O(1) space follow-up 未完成、已拿 H1 |

| 739 | Daily Temperatures | Medium | 2026-10-12 | A | Idea 1:48，自行想到 stack；無 Hint；21:14 AC |
| 207 | Course Schedule | Medium | 2026-10-12 | C | Idea 2:21 自行辨認 graph/cycle；Hint 1；Google DFS cycle detection；AI 協助找 implementation typo/縮排問題，使用者已理解原理與 Scope；26:43 AC |
| 67 | Add Binary | Easy | 2026-10-12 | A | 5:01 AC；僅 Google 二進位轉換的 Python API；使用 int 與 format |

| 133 | Clone Graph | Medium | 2026-10-13 | C | 22:22 H1、28:37 H2，36:17 AC；graph clone mapping 核心需提示，已理解先記錄再遞迴 |
| 153 | Find Minimum in Rotated Sorted Array | Medium | 2026-10-13 | A | 1:27 自行想到 Binary Search，25:38 AC；分支較繁複但可判斷最小值區間 |
| 232 | Implement Queue using Stacks | Easy | 2026-10-13 | B | 17:10 H1 後修正雙 stack 職責與 implementation，23:48 AC |

| 994 | Rotting Oranges | Medium | 2026-10-14 | A | 1:12 BFS Idea；15:12 MLE 自行 debug visited；19:09 AC |
| 494 | Target Sum | Medium | 2026-10-14 | C | H1、H2 後建立 sum→ways DP；27:38 AC；已通過狀態轉移理解測試 |
| 1047 | Remove All Adjacent Duplicates In String | Easy | 2026-10-14 | B | 看 LeetCode Stack Topic 後自行實作；查 join API；4:59 AC |

| 560 | Subarray Sum Equals K | Medium | 2026-10-15 | B | H1 17:11 後用 Prefix Sum + C++ map，34:19 AC |
| 435 | Non-overlapping Intervals | Medium | 2026-10-15 | B | H1 7:25 後懂保留較早結束者；Gemini 提供 C++ 語法及狀態變數，36:28 AC |
| 703 | Kth Largest Element in a Stream | Easy | 2026-10-15 | A | 18:43 AC；自選 min heap；僅查 C++ Class / vector API |

**目前已完成：105 題不同 LeetCode 題目。**

| 15 | 3Sum | Medium | 2026-10-19 | B | 41:08 AC |
| 46 | Permutations | Medium | 2026-10-19 | C | 13:30 AC；參考完整答案，需複習 |
| 231 | Power of Two | Easy | 2026-10-19 | A | 04:09 AC |
| 17 | Letter Combinations of a Phone Number | Medium | 2026-10-20 | B | 30:32 回報 AC；參考前題遞迴寫法，貼出的版本缺少空輸入判斷 |
| 102 | Binary Tree Level Order Traversal | Medium | 2026-10-20 | A | 06:10 AC |
| 383 | Ransom Note | Easy | 2026-10-20 | A | 09:13 AC |

## 需要複習的題目

> 複習題不計入每日 3 題新題額度。完成複習後更新「最近複習 / 結果 / 狀態」，確認已穩定者可改成「已解除」。

| 優先度 | # | 題目 | 為什麼需要複習 | 下次複習目標 | 狀態 |
|---|---:|---|---|---|---|
| 低 | 560 | Subarray Sum Equals K | H1 後才由 Sliding Window 轉成 Prefix Sum 計數 | 無提示完成有負數的 Prefix Sum frequency 解法 | 待複習 |
| 低 | 435 | Non-overlapping Intervals | H1 後才掌握保留較早結束的區間 | 無提示解釋 Greedy 選擇及正確實作 | 待複習 |
| 高 | 494 | Target Sum | 暴力枚舉 TLE，需 H2 才轉成 sum→ways 計數狀態 | 無提示定義計數 DP，正確逐輪更新狀態 | 待複習 |
| 高 | 133 | Clone Graph | 需 Hint 2 才建立原始 Node→複製 Node 對應與先記錄再 DFS 的主要結構 | 無提示獨立實作含 cycle 的 graph clone，解釋 mapping 與 neighbors 的正確性 | 待複習 |
| 中 | 232 | Implement Queue using Stacks | 原題需 H1 才修正兩個 stack 的角色與搬移時機 | 無提示實作，說明 amortized O(1) | 待複習 |
| 高 | 207 | Course Schedule | 有 Google 查詢 DFS cycle detection；原程式 debug 是 typo、縮排與 class 變數設計詢問，不代表不理解原理 | 無提示自行完成有向 Graph cycle detection，說明 visiting/visited 差異 | 待複習 |
| 低 | 56 | Merge Intervals | H1 後才建立完整排序＋合併流程 | 無提示自行重做並說明區間端點的更新 | 待複習 |
| 低 | 844 | Backspace String Compare | 原題 A，但 O(1) space Follow-up 尚未完成，已得 H1 | 無提示自行完成 O(1) space 版本 | 待複習 |
| 高 | 225 | Implement Stack using Queues | 第一次核心解法完全問 AI | 無提示自行用 queue 模擬 stack，並能解釋 push-rotation 為何成立 | 待複習 |
| 高 | 257 | Binary Tree Paths | 第一次看答案後完成 | 無提示自行 traversal 並攜帶 path state | 待複習 |
| 中高 | 91 | Decode Ways | H1 後才建立 DP state / recurrence | 無提示自行定義 dp[i]，處理 0、單碼與雙碼合法性 | 待複習 |
| 中 | 496 | Next Greater Element I | H1 後才理解 monotonic stack 用來一次處理 nums2 並建立 next-greater map | 無提示辨認並完成 monotonic stack，能解釋為何每個元素至多 push/pop 一次 | 待複習 |
| 中 | 1046 | Last Stone Weight | 已想到反覆取最大兩個，但 H1 後才辨認 heap | 無提示辨認 max-heap 並完成 | 待複習 |
| 高 | 416 | Partition Equal Subset Sum | problem reduction 很快，但 DP state definition 與 0/1 反向更新仍需提示 | 無提示自行定義 subset-sum state，解釋為何 j 需反向更新並完成 | 待複習 |
| 中 | 572 | Subtree of Another Tree | 原始方向正確，但 Same Tree 結構處理仍需提示 | 無提示拆成 traversal + Same Tree，正確處理 None / tree structure | 待複習 |
| 高 | 139 | Word Break | Medium 時先採單一路徑 greedy，H1 後才建立「多個 reachable index」模型 | 無提示自行定義 reachable / dp state，完成正確解法並解釋為何 greedy 不成立 | 待複習 |
| 高 | 3 | Longest Substring Without Repeating Characters | 第一次拿 Hint 1，完成的是 O(n²) window | 無提示自行做到 O(n) | 待複習 |
| 高 | 213 | House Robber II | circular constraint → case split 需 Hint 2 | 無提示自行想到拆成兩個 linear case | 待複習 |
| 高 | 322 | Coin Change | 初次完全沒方向後 Google 演算法；2026-10-04 已用 C++ 無演算法提示重做成功 | 已能自行定義 state / transition 並完成 min-DP | 已解除 |
| 高 | 300 | Longest Increasing Subsequence | O(n log n) tails + binary search 經多層提示後完成 | 無提示自行完成 O(n log n)，並能解釋 tails 的語意 | 待複習 |
| 高 | 705 | Design HashSet | 初次曾詢問 hash/collision 核心；2026-10-07 複習確認原理已理解，但仍無法從空殼自行完成初始化與 implementation | 不只重刷題目；先補 C/C++/Python class/struct/object/container initialization，再無提示完整實作 | 待複習 |
| 中 | 120 | Triangle | 原題 A，但 O(n) extra-space follow-up 由 GPT 直接給完整解法 | 無提示把 2D DP 壓成 O(n) space | 待複習 |
| 中 | 21 | Merge Two Sorted Lists | 演算法已 A，但 C++ 曾寫未初始化 `ListNode* dummy;` | 用 C++ 無查詢正確建立 dummy object / pointer | 待複習 |
| 中 | 203 | Remove Linked List Elements | C++ 複習時再次出現未初始化 dummy pointer | 用 C++ 無查詢完成，且不再犯 pointer/object 初始化錯誤 | 待複習 |
| 中 | 69 | Sqrt(x) | 曾需 Hint 2 才辨認 Binary Search，且 final boundary 出錯 | 無提示完成並正確解釋 loop 結束後 boundary | 待複習 |
| 中 | 680 | Valid Palindrome II | 第一次作答有看解答 | 無提示自行想到 mismatch 後檢查刪左或刪右 | 待複習 |
| 中 | 237 | Delete Node in a Linked List | 第一次因看不懂題意直接問 GPT，核心技巧已被解釋 | 無提示重做，並自行解釋 copy-next + skip-next 為什麼等價於刪除目前 node | 待複習 |
| 中 | 152 | Maximum Product Subarray | 需要提示才想到同時維護 max/min ending product | 無提示自行推導 max/min recurrence，並解釋負數為何會交換角色 | 待複習 |
| 低 | 448 | Find All Numbers Disappeared in an Array | O(1) marking 技巧曾需要提示 | 無提示自行做到 O(1) extra space | 待複習 |
| 低 | 543 | Diameter of Binary Tree | bottom-up depth aggregation 曾需主要提示 | 無提示完成 child → parent aggregation | 待複習 |
| 低 | 160 | Intersection of Two Linked Lists | traversal / node identity 曾卡住 | 無提示完成並避免漏 pointer 前進 | 待複習 |
| 低 | 94 | Binary Tree Inorder Traversal | 已能自行完成，但目前額外使用 visited dictionary | 不用 visited set/dict，僅用 stack 完成 iterative inorder | 待複習 |

## 2026-10-16～18 已出題、未回報完成
- Day 35: 78, 98, 191。
- Day 36: 347, 518, 268。
- Day 37: 39, 19, 338。
- 以上不可重新當作全新題目。

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
