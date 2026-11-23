# Coding Interview Problem Tracker

> **用途：這是出題去重與複習安排的主要索引。**
>
> 每次安排「全新題目」前，**必須先讀這份檔案**。已出現在「已完成題目總表」中的題目，不得再當成全新題目；若要再次安排，只能明確標成「複習題」，且不計入每天至少 3 題的新題額度。
>
> 更新日期：2026-11-07  
> 目前進度：截至 2026-11-06，僅保留有實際作答、提示互動或已完成的題目；僅出題未作答的紀錄依使用者要求移除。

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

**目前已確認 AC：107 題不同 LeetCode 題目。另 #33 已參考完整答案並提供正確程式，提交狀態未確認。**

| 15 | 3Sum | Medium | 2026-10-19 | B | 41:08 AC |
| 46 | Permutations | Medium | 2026-10-19 | C | 13:30 AC；參考完整答案，需複習 |
| 231 | Power of Two | Easy | 2026-10-19 | A | 04:09 AC |
| 17 | Letter Combinations of a Phone Number | Medium | 2026-10-20 | B | 30:32 回報 AC；參考前題遞迴寫法，貼出的版本缺少空輸入判斷 |
| 102 | Binary Tree Level Order Traversal | Medium | 2026-10-20 | A | 06:10 AC |
| 383 | Ransom Note | Easy | 2026-10-20 | A | 09:13 AC |

| 22 | Generate Parentheses | Medium | 2026-10-21 | B | 24:43 AC；參考 #17 寫法，獨立構建括號遞迴 |
| 118 | Pascal's Triangle | Easy | 2026-10-21 | A | 05:51 AC；獨立完成 |

| 113 | Path Sum II | Medium | 2026-11-06 | A（暫定） | C++ DFS + path 回溯，33:36 AC；獨立性待確認 |
| 721 | Accounts Merge | Medium | 2026-11-06 | C（暫定） | 43:45 AC；完整抄答案，需驗證理解 graph modeling |
| 459 | Repeated Substring Pattern | Easy | 2026-11-06 | 待確認 | 23:40 AC；特殊字串技巧，需確認獨立性 |

| 79 | Word Search | Medium | 2026-10-22 | C | 44:57 AC；自行嘗試 DFS 後參考完整答案；需複習 visited 與 Undo |

**已確認完成：117 題不同 LeetCode 題目（含參考答案後 AC；#33 未確認 AC 不計入）。**

| 78 | Subsets | Medium | 2026-11-09 | A | 16:10，完全獨立 C++ Backtracking AC |
| 2264 | Largest 3-Same-Digit Number in String | Easy | 2026-11-09 | A | 06:54 AC；獨立性未明確回報 |

| 39 | Combination Sum | Medium | 2026-11-10 | A | 17:46，完全獨立 C++ Backtracking AC |
| 268 | Missing Number | Easy | 2026-11-10 | A | 04:22 AC，sum difference |

| 684 | Redundant Connection | Medium | 2026-11-10 | C | 22:37 Union-Find AC，曾詢問 GPT 核心實作；第一版 16:43 演算法有誤 |

| 841 | Keys and Rooms | Medium | 2026-11-11 | A | 07:48，獨立 C++ BFS AC |

| 785 | Is Graph Bipartite? | Medium | 2026-11-18 | B | 20:55 AC；外部查 BFS/DFS coloring，實作獨立 |
| 387 | First Unique Character in a String | Easy | 2026-11-18 | A | 03:11 AC，字元頻率統計 |

| 875 | Koko Eating Bananas | Medium | 2026-11-19 | A（暫定） | 21:54 AC；C++ binary search |
| 338 | Counting Bits | Easy | 2026-11-19 | A（暫定） | 19:47 AC；C++ DP |

| 740 | Delete and Earn | Medium | 2026-11-20 | C | 35:56 AC；Gemini 提示 House Robber 核心模型，後獨立 DP 實作 |

| 399 | Evaluate Division | Medium | 2026-11-20 | C | 49:47 AC；Graph/DFS 重要提示後獨立實作 |

| 605 | Can Place Flowers | Easy | 2026-11-20 | A（暫定） | 12:33 AC，C greedy 正確；無演算法提示回報 |

| 1091 | Shortest Path in Binary Matrix | Medium | 2026-11-21 | B | 35:30 AC；BFS 獨立，Hint 1 Debug visited 時機 |

| 279 | Perfect Squares | Medium | 2026-11-21 | C | 24:06 AC；Hint 2 提供核心 DP 轉移 |

| 2215 | Find the Difference of Two Arrays | Easy | 2026-11-21 | A（暫定） | 05:39 AC；C++ set 差集 |

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

| 高 | 547 | Number of Provinces | 35:27 未 AC，單層掃描漏掉間接連通；DFS 草稿 visited 條件反向 | 無提示完整辨認並走訪連通分量 | 待複習 |

| 高 | 684 | Redundant Connection | 第一版端點 visited 無法代表相同連通分量，Union-Find 版依 GPT 且 parent[n] 未初始化 | 無提示實作 DSU / 或獨立 graph connectivity，對照 edge cases | 待複習 |

| 高 | 518 | Coin Change II | 35:01 未解；自行嘗試 DP 但組合計數狀態建模錯誤 | 不看提示重新建立計數模型並解釋重複組合問題 | 待複習 |

| 中 | 399 | Evaluate Division | 49:47 AC，C（重要 Hint 2/3 後完成） | 不看提示重建 weighted Graph 與 DFS | 待複習 |

## 2026-10-21 有實際練習，AC 尚未確認
- 33 Search in Rotated Sorted Array：已參考完整答案，提供正確程式；尚未回報 Accepted 與時間；評 C，不再當新題，列高優先無提示複習。

## 維護規則

- 每完成一個**第一次做的新題**：加入「已完成題目總表」。
- 同一題重做：不要新增第二列；更新備註與最佳評價即可。
- 需要再次驗證的題：加入「需要複習的題目」。
- 複習成功且能力已穩定：把狀態改為「已解除」，不要再頻繁安排。
- 每日出題前：
  1. 先讀本檔案。
  2. 新題不得出現在「已完成題目總表」。
  3. 已經實際嘗試或取得 Hint 而未完成的題目，只能安排為複習；單純出題但未作答者不列入封鎖清單。
  4. 複習題必須明確標成複習，且**不計入每天至少 3 題新題**；Premium 題目仍不得安排。
  5. 完成當天紀錄後，同步更新本檔案、`progress.md`、`CURRENT_STATE.md` 與對應 `days/YYYY-MM-DD.md`。

## 2026-11-06 Day 56 更新
- #113 Path Sum II：33:36 AC，暫 A（獨立性待確認）。
- #721 Accounts Merge：43:45 AC，暫 C；答案完整參考，graph 建模列高優先複習；若仍無法理解核心需重新評估。
- #459 Repeated Substring Pattern：23:40 AC；評價需確認是否獨立想到 s+s 技巧。
- 2026-10-31～11-05 只有出題、無作答紀錄的題目已移除。

## 已嘗試但未確認 Accepted
- #33 Search in Rotated Sorted Array：已看完整答案並提供程式，AC 未確認，列複習。
- #34 Find First and Last Position of Element in Sorted Array：11:54 自行嘗試，未達 O(log n)，尚未 AC，列複習。
- #128 Longest Consecutive Sequence：已要求 Hint 1，尚無完整解答，列複習。

> 依 2026-11-07 使用者要求，單純出題卻沒有實際作答或互動的題目已從 GitHub 追蹤清單移除；不影響已完成題數與歷史解題成績。

## 2026-11-09 Day 59 更新
- #78 Subsets：Medium，16:10 AC，A；C++ 完全獨立 backtracking，正確 push/pop，O(n·2^n) time。
- #547 Number of Provinces：Medium，35:27 未 AC，D；已嘗試，單層鄰接掃描漏掉間接連通，屬演算法錯誤；DFS 草稿 visited 判斷反向。高優先複習，不能再作新題。
- #2264 Largest 3-Same-Digit Number in String：Easy，06:54 AC，A（無提示資訊未明確回報）；C++ 線性掃描正確。
- 明確 AC 不同題目累計 113（先前 111 + #78、#2264）。

## 2026-11-10 Day 60 更新
- #684 Redundant Connection：Medium，16:43 第一版回報 AC、22:37 Union-Find 版回報完成，暫 C；第一版僅根據端點出現過判環，會誤判不同連通分量之間的邊，且 edges[-1] 越界；第二版向 GPT 問 Union-Find 寫法，parent[n] 未初始化。使用者回報 AC 但貼出的兩版均有正確性問題，標記「回報 AC、提交版本待核對」。列高優先複習，不再作新題。
- #39 Combination Sum：Medium，17:46 AC，A，獨立 C++ backtracking，正確允許重複選擇、start 防重複、push/pop。
- #268 Missing Number：Easy，04:22 AC，A（未明確回報是否查提示），C++ 數學總和差，O(n)/O(1)。
- 明確無程式正確性疑慮的 AC 不同題目累計 115（原 113 + #39、#268）；若使用者 #684 實際提交 AC 經確認則 116。今日 3 題均已嘗試，不再列新題。

## 2026-11-10 #684 AC 核對更正
- 使用者再次確認貼出的 Union-Find 版本在 LeetCode **AC（22:37）**，評 C（核心實作向 GPT 請教）。`parent[n]` 預設為 0，因節點只在 1..n，0 可作為 n 的代表根，於本題條件下仍能正確運作；但建議使用 `i<=n` 作清楚、標準的初始化。不應將此 AC 判為失敗。累計 **116 題不同題目已回報 AC**。

## 2026-11-11 Day 61 更新（重複出題修正）
- #841 Keys and Rooms：Medium，07:48 AC，A；完全獨立 C++ queue traversal，O(V+E) time，queue 可含重複待處理項；**首次完成，新題**。
- #416 Partition Equal Subset Sum：Medium，32:55 AC，**複習 C**；2026-10-02 已 AC（當時 B），本次無法自行重建，查看舊程式後完成。保持歷史最佳 B，列高優先無參考重做。
- #242 Valid Anagram：Easy，06:59 AC，**複習 A**；2026-09-11 已 AC，僅查 unordered_map API，無演算法提示。最佳 A 不變。
- 本日錯誤安排兩題舊題，僅 #841 計入全新題目；另外兩題不得算新題。累計 **117 題不同 LeetCode 已確認 AC**，不是 119 題。後續出題須先與 tracker 完成表比對。


## 2026-11-17 已嘗試／已參考答案，AC 待確認
三題已實際練習及抄完整答案，從此不得當全新題。暫 C（理解尚未驗證），不以參考程式正確推定已 AC；累計已確認 AC 維持 117，待三題確認後才可增至 120。

| 優先度 | # | 題目 | 狀態 | 本次紀錄與複習目標 |
|---|---|---|---|---|
| 高 | 2316 | Count Unreachable Pairs of Nodes in an Undirected Graph | 待複習；AC 待確認 | 15:28，想到 DFS/Union-Find 但無法實作，抄完整答案。驗證連通分量大小、不可達配對計數，以及從空白建立遍歷。 |
| 高 | 162 | Find Peak Element | 待複習；AC 待確認 | 受挫後抄答案。驗證區間排除理由與邊界，不假定原始卡點。 |
| 中 | 66 | Plus One | 待複習；AC 待確認 | 受挫後抄答案。驗證進位與全 9 處理；一次表現不代表整體 Easy 退步。 |

#162、#66 自述思考超過 10／15 分鐘，未確認逐題對應及 Accepted time。三題均未驗證看解後理解程度。完整程式與審閱見 days/2026-11-17.md。

## 2026-11-18 實際作答更新
- #785 Is Graph Bipartite?：Medium，20:55 AC，**B**；Google 查詢如何判斷 Bipartite，看到 BFS/DFS 著色法（演算法方向外部提示），之後自行 C++ 實作，含 disconnected components。程式正確；外層反覆掃描未著色節點最壞 O(V²+E)，Space O(V)。不得再作新題。
- #518 Coin Change II：Medium，35:01 未解出，**D（本次）**；自行嘗試 amount-based dp 與 used map，但無法正確計算組合，有重複計數風險，核心 DP state/transition 未建立。未看核心提示／完整解法；高優先複習，不得再作新題。
- #387 First Unique Character in a String：Easy，03:11 AC，**A（依本次貼碼，無外部提示回報）**；C++ frequency map + ordered scan，O(n) time/O(1) alphabet-bound space。不得再作新題。
- 本日 2/3 AC、59:07，三題均第一次實際作答；已確認不同 AC 數量從 117 增為 **119**。#2316、#162、#66 於 11/17 仍待 AC 確認，不計數。不得把 #518 算 AC。

## 2026-11-18 #518 Hint 1
- #518 已實際嘗試 35:01 未解，之後明確要求 H1；提示內容聚焦組合與排列的差異、dp state 如何避免順序重複，不透露完整解法。之後只能複習，不能作新題。

## 2026-11-18 #518 完整解答狀態
- #518 Coin Change II：35:01 未解，H1 後使用者要求並已取得**完整 C++ 答案**。本人 AC 未回報，不能算完成新題或累計 AC；以「已看完整答案，待無參考複習」追蹤。當次 D（建模未成功）保留，理解程度需後續驗證。

## 2026-11-19 #210 實際嘗試
- #210 Course Schedule II：Medium，40:25 **未獨立解出**；自行寫 DFS + label + visited 草稿，存在排序與 cycle state 建模錯誤，程式有未宣告 n 與缺回傳問題；使用者後向 Gemini 取得正確程式（未提供 Gemini 版本／未回報 AC）。依本次獨立建模表現暫 D，理解與 AC 待驗證。依 40 分鐘規則，教練已提供 Kahn 完整參考答案。高優先複習，不得再作新題，累計 AC **119** 不變。#875 與 #338 尚未回報，不建立已完成紀錄。

## 2026-11-19 #875、#338 完成回報
- #875 Koko Eating Bananas：Medium，**21:54 AC**，A（暫定，未回報是否查演算法提示）。正確 C++ binary search on answer，ceil_sum O(n)，總 O(n log M) time / O(1) space。已完成，不得再作新題。
- #338 Counting Bits：Easy，**19:47 AC**（使用者再明確確認），A（暫定，未回報是否查演算法提示）。正確 C++ DP，O(n) time / O(n) space（輸出陣列）。已完成，不得再作新題。
- 今日 #210 40:25 未獨立解出、參考完整答案但本人 AC 未確認；#875、#338 AC，當日 **2/3 AC**。累計不同 LeetCode 已確認 AC **121**（前 119 + 兩題）。

## 2026-11-20 部分作答紀錄
- #399 Evaluate Division：Medium，5:04 無方向，已從外部提示得知使用 Graph，但仍不知如何把 equations 轉成 Graph。尚無程式與 AC；未超過 30 分鐘，不再主動透露 Hint。本題已實際嘗試且看過核心演算法方向，之後不得再列全新題；後續需複習 Graph modeling。暫不評 A/B/C/D。
- #740 Delete and Earn：Medium，35:56 **AC**，**C**。最初試 Greedy 未成功，Gemini 提供「可轉成 House Robber」的重要模型提示，後獨立完成 C++ frequency map 與 1D DP；核心轉換非獨立，實作正確。Time O(n+M) average，Space O(M)，M=max(nums)。新完成題 +1，已確認不同 AC **122**。
- #605 Can Place Flowers：排程中但尚未回報實際作答，不記錄為完成或嘗試。

## #399 2026-11-20 Hint 2
- 使用者於知道 Graph 方向後再要求提示；已提供加權 Graph 建模提示（商作為 edge weight、反向邊及多邊查詢），未提供完整程式。AC 未確認，後續複習須記錄已看重要建模提示，不算無提示。

## #399 2026-11-20 37:48 進度
- 37:48 未解出，使用者已建構正反向加權邊草稿，DFS 函式未完成；C++ 語法與作用域問題並存。依門檻給 **Hint 3**（DFS 累積權重與 visited 偽碼、STL 語法修正）；未給完整程式。本人 AC 待確認，不得計入不同 AC，也不得當新題。已取得重要 Graph modeling/DFS 實作提示。

## #399 2026-11-20 最終 Accepted 更正
- #399 Evaluate Division：Medium，**49:47 AC，C**。經外部 Graph 方向、Hint 2 加權邊建模與 Hint 3 DFS 搜尋偽碼後，自行寫出完整 C++ 並 AC。正向／反向圖、weighted DFS、visited 與 query 邊界均正確。單次搜尋 O(V+E)，總 O(E+Q(V+E)) time / O(V+E) extra space。不計完全獨立 Medium AC。此最新結果取代前面「尚未 AC／暫不評」的中途記錄。已完成，不得當全新題；保留無提示建模複習目標。累計 **123 題不同 LeetCode 確認 AC**（前 122 + #399）。

## 2026-11-20 #605 AC 及最終日結
- #605 Can Place Flowers：Easy，**12:33 AC，A（暫定）**，C greedy scan、原地種植及頭尾/單格邊界，Time O(m) / Space O(1)；目前未回報任何演算法提示。已完成，不得再當新題。
- 今日 #399 49:47 AC C、#740 35:56 AC C、#605 12:33 AC A（暫），**3/3 AC**，總時間 98:16。累計不同題目確認 AC **124**（前 123 + #605）。兩題 Medium 皆使用重要方向提示，不納入 Medium 無提示成功率分子。

## 2026-11-21 #1091 已實際嘗試與 Hint 1
- #1091 Shortest Path in Binary Matrix：Medium，31:21 TLE；自主 C++ 8 方向 BFS、層級計數、邊界處理，visited 標記設在 dequeue，致使同一格被多次 enqueue。教練已提供 Hint 1（引導觀察多父節點重複入列和標記時機），未提供完整解答。**已嘗試且看 Hint，不得再作全新題；尚未 AC**，後續觀察自行 Debug。#279、#2215 尚無作答回報，累計已確認 AC 124 不變。

## 2026-11-21 #1091 最終 Accepted 更正
- #1091 Shortest Path in Binary Matrix：Medium，**35:30 AC、B**。原 31:21 TLE（visited pop 才標記）；經教練 Hint 1 Debug 引導後，用 `set<pair<int,int>>` 在 enqueue 時插入 visited，自行修正並 AC。核心 BFS 模型原本獨立，僅效率 Debug 需提示；本次不算完全無提示 AC，但 **不是演算法方向錯誤**。Time O(n² log n) / Space O(n²)。最新狀態已完成，不再作全新題。累計已確認不同題 **125**（124 + #1091）。#279、#2215 尚未回報。

## 2026-11-21 #279 已嘗試與 Hint 1
- #279 Perfect Squares：Medium，22:05 未解；C++ 一維 DP 只取最大平方數的貪婪式轉移，n=12 會算 4 而最佳是 3。提供 Hint 1 反例與比較不同平方數的引導；未提供完整公式或答案。**已實際嘗試／看提示，日後只能複習，不得當全新題**。未 AC，累計 125 不變。

## #279 2026-11-21 Hint 2 補充
- 使用者反映 Hint 1 無效且已知 n=12 反例，真正卡在 DP 轉移；後續已給 Hint 2（對每個 i 遍歷全部 j*j<=i，以 dp[i-j*j]+1 取最小），沒有完整 code。#279 尚未 AC，不再當全新題，後續評分須記錄核心演算法提示。

## #279 2026-11-21 最終 AC 更正
- #279 Perfect Squares：Medium，**24:06 AC，C**。使用者原 DP 只取最大平方數；對 Hint 1 的已知反例無助，取得 Hint 2 的核心遍歷全部平方數／最小化轉移後，**自行**補完程式並 AC。不是獨立 Algorithm Design，卻有正確 DP Implementation，Time O(n sqrt n) / Space O(n)。已完成不得當全新題；後續可無提示重建 DP 轉移。累計 **126 題不同 LeetCode 確認 AC**（前 125 + #279）。#2215 未回報。

## 2026-11-21 #2215 Accepted 與完整日結
- #2215 Find the Difference of Two Arrays：Easy，**05:39 AC，A（暫定）**。C++ 兩個 set 去重與雙向差集，正確；Time O(m log(m+1)+n log(n+1))，Space O(m+n)。未明確回報演算法提示。已完成，不得再當全新題。
- 11/21 #1091 35:30 AC B（Debug Hint 1）、#279 24:06 AC C（核心 DP Hint 2）、#2215 05:39 AC A（暫），**3/3 AC，總 65:15，累計 127 題不同 LeetCode AC**。上述最新結果取代先前「#2215 尚未回報／126 題」的中途資訊。


## 2026-11-22 新增已完成題目（最新；此段優先於舊總數）
| # | 題名 | 難度 | 首次完成 | 本次評價 | 備註 |
|---|---|---|---|---|---|
| 130 | Surrounded Regions | Medium | 2026-11-22 | A（暫定） | 40:20 AC；DFS 連通分量與邊界判斷，set visited；外部提示未知 |
| 983 | Minimum Cost For Tickets | Medium | 2026-11-22 | A（暫定） | 30:51 AC；按日 DP，三票種成本轉移；外部提示未知 |
| 345 | Reverse Vowels of a String | Easy | 2026-11-22 | A（暫定） | 08:54 AC；雙指標母音交換；外部提示未知 |

**截至 2026-11-22 已確認不同題 AC：130 題**（127 + 3）。上述三題不得再當新題；歷史舊統計保留作時點紀錄。


### 2026-11-22 後續確認：#130 / #983 獨立性（最新覆蓋先前暫定評價）
- 使用者確認 #130 Surrounded Regions 與 #983 Minimum Cost For Tickets **核心演算法完全獨立想出**，Google **僅查語法**，無演算法提示。兩題本次評價由 **A（暫定）正式改為 A**，計入 Medium 無演算法提示 AC 分子。#130 40:20、#983 30:51，兩題均已 AC；Idea time、Debug 歷程與本人 complexity 解釋仍未知。
- 語法/API 查詢不等於演算法 Hint；#345 獨立性未進一步確認，維持 A（暫定）。不同題 AC 總數仍為 **130**，不得重複加題數。歷史段落保留，依本段最新更正為準。


## 2026-11-23 #802 實際嘗試（最新）
- **#802 Find Eventual Safe States**：Medium，**44:25 未解出，D（本次獨立建模）**；C++ DFS 草稿，已自行想到 visited/state，但用鄰居索引 i 當節點 DFS(i)（應 graph[node][i]）、未正確區分搜尋中/安全/不安全、terminal 未快取、安全節點判斷變數 a 可能未初始化或沿用舊值。
- 依使用者 **40 分鐘以上仍未解直接給完整答案**規則，教練已提供四狀態 DFS C++ 正解與 O(V+E) / O(V) 複雜度。這是外部完整答案，**本人未回報 AC，不可增加不同 AC 題數或計入無提示 Medium AC**；之後僅能作複習，優先驗證 cycle detection 與 memoized DFS 的狀態設計。
- Concept 有 DFS/terminal 概念，Algorithm Design 狀態判定未正確建立，Implementation 鄰居索引及變數使用有錯；Debug、Idea time、本人 Complexity 理解未回報。#1049/#190 尚未回報，不視為完成。**累計確認不同題 AC 仍為 130**。

### #802 複習追蹤
| 優先度 | # | 題目 | 狀態 | 複習目標 |
|---|---:|---|---|---|
| 高 | 802 | Find Eventual Safe States | 44:25 未解，已看完整 C++ DFS 解答；本人 AC 未確認 | 無提示獨立設計 DFS 搜尋中／安全／不安全狀態與 cycle 判斷；不當新題 |
