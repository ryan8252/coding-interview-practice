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
- 219 Contains Duplicate II 已能無提示使用 last-seen index 解出；但 705 Design HashSet 顯示底層 hash function / bucket / collision handling 尚未獨立掌握
- Stack
- Running Minimum / One Pass
- Two Pointers / in-place array 操作（已有數次無提示成功）
- DP / recurrence：70、746、198、64、120、931 已有多次無提示成功。322 Coin Change 已於 2026-10-04 用 C++ 無演算法提示重做成功並解除複習；377 Combination Sum IV 也能無 Hint 自行建立 counting DP。91 Decode Ways 仍顯示遇到新的字串 DP 時，state definition / recurrence 需要提示；152、416 仍需持續驗證。
- Binary Tree：100 首次需要查 traversal；226 已能無查詢自行 traversal；543 在 bottom-up depth aggregation 上需要主要提示；104 Maximum Depth 與 112 Path Sum 已能無提示完成；110 Balanced Binary Tree 更進一步自行用 iterative stack + dictionary 完成 child -> parent depth aggregation；94 Inorder Traversal 也能無提示完成，但目前 iterative inorder 仍額外使用 visited dictionary，可再優化
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
- **跨語言 object / container initialization 基礎**
  - 2026-10-07 的 705 複習確認 HashSet 原理本身已理解，但從 C / C++ / Python 空殼開始時，常卡在 struct/class、constructor/create function、container 初始化。
  - 1143 也出現 Python 2D list aliasing：`[[0]*(m+1)]*(n+1)` 多列共用同一 inner list。
  - 後續應獨立練習 C `typedef struct` + `malloc/create/free`、C++ constructor / `vector<T>(n)`、Python `__init__` 與 nested mutable container 初始化，而不是只靠重刷 705。

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

> 744 與 1290 雖實際提交跨到 9/26 00:xx，但依使用者指定仍算 9/25。2026-09-26 Day 18 已完成；2026-09-27 今日練習尚未開始。

新題：
- 120 Triangle：A，20:22；原題 2D DP 無提示自行完成。O(n) space follow-up 在 Accepted 後由 GPT 直接提供完整解法，optimization 另列學習內容
- 744 Find Smallest Letter Greater Than Target：A，9:43；核心自行完成，只因不熟 Python 語法詢問 GPT
- 1290 Convert Binary Number in a Linked List to Integer：A，13:02；完全自己完成

複習：
- 35 Search Insert Position：A（複習），7:12，C++；過去已用 Python 做過
- 643 Maximum Average Subarray I：A（複習），4:40，C++；過去已用 Python 做過

### Day 18 — 2026-09-26

> 58、111、62 雖有部分實際提交跨到 9/27，但依使用者指定全部算 9/26。2026-09-27 尚未開始。

新題：
- 58 Length of Last Word：A，2:10；無提示、無查詢
- 111 Minimum Depth of Binary Tree：A，25:14；無提示、無查詢，自行 BFS
- 62 Unique Paths：A，5:15；無提示、無查詢，自行用組合數完成

### Day 19 — 2026-09-27

> 931 雖實際提交跨到 9/28 00:06，但這一組依規則仍算 9/27。2026-09-28 尚未開始。

新題：
- 680 Valid Palindrome II：C，37:55；有看解答，列入複習
- 374 Guess Number Higher or Lower：A，3:47；自己完成
- 931 Minimum Falling Path Sum：A，30:24；只問 `list.copy()` 語法，演算法與 O(n) space 狀態壓縮自行完成

### Day 20 — 2026-09-28

新題：
- 94 Binary Tree Inorder Traversal：A，9:00；自己完成，但用 visited dictionary，額外 O(n) space
- 136 Single Number：B，4:29；有看提示並查 Python XOR 語法
- 300 Longest Increasing Subsequence：C，40:05；先自行想到 O(n²) DP，O(n log n) tails + binary search 經多層提示後完成，列入複習

### Day 21 — 2026-09-29

新題：
- 1413 Minimum Value to Get Positive Step by Step Sum：A，9:59；自己完成
- 237 Delete Node in a Linked List：C，14:47；因看不懂題目直接問 GPT，核心技巧由 GPT 解釋，列入複習
- 455 Assign Cookies：A，13:35；自己完成

### Day 22 — 2026-09-30

新題：
- 219 Contains Duplicate II：A，12:32；自己完成
- 705 Design HashSet：C，23:22；詢問 GPT modulo / collision / chaining / linear probing 等核心 Hash Table 設計
- 152 Maximum Product Subarray：B，43:23；先自行嘗試，之後拿到 max/min ending product 關鍵提示，再自行完成 recurrence

### Day 23 — 2026-10-01

新題：
- 733 Flood Fill：A，13:14；Idea 2:57，11:14 第一版程式有 bug，13:14 自行修正 Accepted。核心 traversal 自行辨認；可再優化 Python queue 與 visited/染色時機。
- 349 Intersection of Two Arrays：A，7:52；0:20 讀完，Idea 1:00。自行使用 sorting + two pointers 完成；原本用 dictionary 去重，Accepted 後理解排序下可用 `ans[-1]` 去重。
- 139 Word Break：B，47:25；0:50 讀完，6:05 有初步想法但偏 greedy；22:30 H1 提示改從「哪些 index 可到達」建模，之後自行發展 reachable-position queue 並 Accepted。只問過 Python slicing 語法。列入高優先複習。

Day 23 觀察：
- Easy 題的 pattern recognition 很快：733 在 2:57 有主要方向，349 在 1:00 有主要方向。
- 139 再次顯示目前 Medium 的主要瓶頸偏向 **state / model 建立**，不是單純 implementation；一旦把問題改寫為 reachable index，後續能持續自行推進。
- Python list 的 `pop(0)` 與 `x in list` 都可能造成 O(n) 操作；之後可逐步熟悉 `collections.deque` 與 set。
- 139 後續複習時，除了無提示重建 BFS/reachable 解法，也要能自己說出 `dp[i]` 的語意，而不是直接背 recurrence。

### Day 24 — 2026-10-02

新題：
- 205 Isomorphic Strings：A，10:08；0:38 讀完、Idea 3:00、3:39 第一版有 bug、10:08 Accepted。雙向 map 自行完成。
- 572 Subtree of Another Tree：B，38:10；0:29 讀完，2:10 原始 idea 是 traversal 找候選 root 再比 subtree；3:04 看 LeetCode Topic「string matching」後被帶偏，12:13 自己判斷不成立，14:00 發現 node value 可重複後要求 H1。H1 後回到 traversal + Same Tree；超過 Easy 硬上限後由 GPT 補完整 sameTree 核心，38:10 Accepted。
- 416 Partition Equal Subset Sum：B，21:58；0:30 讀完，1:05 自行想到總和奇數 False、偶數轉成 subset sum = total/2；1:57 判斷可能是 DP，3:21 想到記 reachable sum；H1 後定義 dp[x]，20:24 主體完成但 forward update 會重複使用同一元素，debug 提示改成 reverse update，21:58 Accepted。

Day 24 觀察：
- 205 顯示 Hash Map mapping 類 Easy 已相對穩定。
- 572 的主要問題不是 traversal，而是比較 tree structure 時沒有保留 None；另外外部 Topic 會把原本正確的思路帶偏，之後應優先相信自己先驗證過的 reasoning。
- 416 顯示 Medium 的 problem reduction 已能很快完成，但 DP state definition / transition 仍是主要弱點；尤其要理解 0/1 類問題為何需要反向更新。
- 新增複習：416 高優先；572 中優先。

### Day 26 — 2026-10-04
- 101 Symmetric Tree：A，10:07；0:19 先想到左右子樹比較，9:32 發現題意要求 mirror of itself，將 Same Tree 比較方向改成 left-vs-right / right-vs-left 後 AC。
- 409 Longest Palindrome：A，6:44；Idea 1:46；自行統計字元頻率，偶數全取、奇數取 count-1，最後若有任一奇數再加 1。
- 55 Jump Game：A，8:04；1:21 先想到 reachable positions，4:08 主動簡化為只維護 farthest reachable index，無 Hint AC。這是 greedy reasoning 的正向證據。
- 複習 322 Coin Change：A（複習），15:32，C++。核心 recurrence 自行重建；只詢問 `vector<int> dp(amount+1, amount+1)` 初始化與 sentinel return 寫法，依規則不算演算法提示。高優先複習狀態解除。

### Day 27 — 2026-10-05
- 225 Implement Stack using Queues：C，13:01；核心解法完全問 AI。列入複習。
- 257 Binary Tree Paths：C，24:36；看答案完成 traversal + path state。列入複習。
- 91 Decode Ways：B，23:17；12:11 H1 後建立 dp state，需複習新的字串 DP state/recurrence。
- 複習 213 House Robber II：C++，20:49 時核心 case split 已自行重建；後續主要是 DP indexing debug。本日未明確回報 Accepted time，因此暫不解除複習狀態。

### Day 28 — 2026-10-06
- 1046 Last Stone Weight：B，15:58；14:37 H1 後辨認 heap；heapq API 查詢不算額外 Hint。列入複習。
- 700 Search in a Binary Search Tree：A，8:16；Idea 0:24，正確利用 BST ordering。
- 238 Product of Array Except Self：A，30:45；5:07 注意到不能除法，之後自行重建 prefix × suffix，無 Hint。
- 今日 238 的總時間雖長，但屬重新建模後獨立完成；不是單純 implementation 卡住。

### Day 29 — 2026-10-07
- 496 Next Greater Element I：B，30:39；7:20 H1 後理解先處理 nums2 建立 next-greater map，最後自行完成 monotonic stack。
- 108 Convert Sorted Array to Binary Search Tree：A，15:31；Idea 4:36，無 Hint，自行 divide and conquer。
- 1143 Longest Common Subsequence：A，24:08；Idea 2:07，自行建立 O(MN) 2D DP；只查 Python 2D list 初始化 aliasing bug。
- 複習 705 Design HashSet：未解除。HashSet / chaining 原理已理解；真正卡點是 C/C++/Python 的 object / class / struct / container 初始化模板。
- 新增基礎弱點：跨語言初始化與 object construction，應獨立放進 theory 練習。

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
- **出新題前必須先檢查 `PROBLEM_TRACKER.md`。** 已完成或有實際嘗試／提示互動的題目不得再當新題；若安排重做只能標成複習，且不計入每日 3 題新題。再搭配 `progress.md` 與最近 `days/` 查看詳細紀錄。35 與 643 在 Day 17 曾誤重複，因此當天只算複習。

## 新對話接續方式

在新的 ChatGPT 對話中，可以直接說：

> 請讀取 GitHub repo `ryan8252/coding-interview-practice` 的 `PROBLEM_TRACKER.md`、`CURRENT_STATE.md`、`progress.md` 和最近的 `days/` 紀錄，然後繼續我的每日 coding interview 練習。出新題前先用 `PROBLEM_TRACKER.md` 去重。

這樣即可從目前進度接續，不需要重新解釋整個訓練背景。


## 2026-10-11 Day 30 能力狀態
- 當日 3 題全部 AC：56 Merge Intervals B（21:18，排序提示後自行實作）、200 Number of Islands A（19:31，演算法獨立想到，曾求助 implementation/debug）、844 Backspace String Compare A（7:48，無提示）。
- 200 的主要弱點是 stack 要存座標及正確維護 visited，並非辨認演算法。迭代實作是 DFS。
- 844 O(1) extra-space follow-up 尚未完成，獲 H1 後仍待驗證；56 應低頻複習。
- 今日題目已列入 tracker，今後不可重複當新題。


## 2026-10-12 Day 31 更新
- 739 Daily Temperatures A (21:14)，1:48 自行使用 stack；207 Course Schedule 暫列 C (26:43)，已辨認 graph/cycle，但 Google 查 DFS cycle detection；67 Add Binary A (5:01)，僅查 Python API。
- 對 207：self.dfs(node)/neighbour 與 return False 縮排是已知原理下的筆誤和 debug 困難；Class Scope 亦已理解，只是在諮詢比較好的設計。不得再錯誤標記為不理解 Scope/DFS。核心 cycle detection 獨立性待 active recall 驗證。
- 67 Python int(base=2)/format 方法已 AC，不強制要求 follow-up。


## 2026-10-13 Day 32 更新
- 133 Clone Graph：C，36:17；DFS / dictionary 初步方向自行想到，但 H2 才取得 graph clone mapping 核心結構；能解釋先記錄再遞迴避免 cycle，列高優先複習。
- 153 Find Minimum in Rotated Sorted Array：A，25:38；1:27 自行辨認 binary search，無提示；邊界分支較繁複但 AC。
- 232 Implement Queue using Stacks：B，23:48；17:10 H1 後完成；理解 push stack / pop stack 分工與攤銷複雜度；之後只需一次無提示複習。
- Day 32 三題均 AC；總計 93 題。


## 2026-10-14 Day 33 更新
- 994 Rotting Oranges A（19:09）：1:12 BFS Idea；15:12 MLE 自行修正 visited，顯示 grid traversal debugging 進步。
- 494 Target Sum C（27:38）：greedy 自行推翻；H1 後暴力列舉 TLE；H2 後得到 sum→ways DP，初版混淆 key/value 與新舊狀態，Gemini 協助 Python defaultdict 與 items。能正確回答 DP 狀態轉移小測驗。列高優先複習。
- 1047 Remove All Adjacent Duplicates In String B（4:59）：看 LeetCode Topic 知道 Stack 後自行實作；只查 join 語法。以新題驗證辨認能力即可。
- Day 33 三題 AC，總計 96 題。


## 2026-10-15 Day 34 更新
- 560 B，34:19，C++；H1 後從不適用負數的 Sliding Window 改成 Prefix Sum + map，列低頻複習。
- 435 B，36:28，C++；H1 後掌握保留較早結束區間的 Greedy，Gemini 僅提供語法與狀態變數建議，列低頻複習。
- 703 A，18:43，C++；11:30 只詢問 Class member / scope 與 vector API，自行改用 min-heap priority_queue，無演算法 Hint，不強制複習。
- 全部 AC，累計 99 題。


## 2026-10-19 Day 38 更新
- 15 3Sum：B，41:08 AC。初版 35:45 TLE，Hint 1 處理重複及固定第一個數字的搜尋方向後，自行完成排序＋雙指標 O(n²)；中優先無提示複習。
- 46 Permutations：C，13:30 AC。知道 Backtracking 規則但看完整答案才寫出來；可理解現有遞迴碼，無法從零建立 recursion/backtrack structure。高優先補強 State、Choices、Base Case、Undo，採小單位獨立編寫與 Active Recall。
- 231 Power of Two：A，04:09 AC；無 Hint，以 n>0 並反覆除 2 判定，O(log n) / O(1)。
- 今日 3 題 AC；累計 **102 題不同題目**。2026-10-16～18 僅出題無作答，已按使用者要求從 tracker 移除。
- 使用者對部分邏輯推理題與 Backtracking 建構較缺乏信心；已有多次獨立完成其他 Medium 的證據，避免概括為天生邏輯差。每日 2 Medium + 1 Easy 不因卡關降低難度。


## 2026-10-20 Day 39 更新
- 17 Letter Combinations of a Phone Number：B（暫定），30:32 回報 AC；參考昨天 46 的程式碼記起遞迴形式後自行實作 first-digit + suffix 組合；沒有上網查題解。貼出的版本缺少 empty string input 的處理，需確認版本是否真的 AC。這是遞迴分解合併，尚不能算獨立掌握典型 Backtracking 的 Undo。
- 102 Binary Tree Level Order Traversal：A，06:10，自行 BFS 按層數切分，無提示。
- 383 Ransom Note：A，09:13，自己寫 dict 次數統計，無提示。
- Day 39 三題回報 AC，累計 105 題不同題目。46 高優先複習仍保留，肯定參考已做題後能遷移遞迴的進展。


## 2026-10-21 Day 40 更新
- 22 Generate Parentheses：B，24:43 AC。參考 17 的遞迴程式但獨立建構 backtrack(r,l,comb) 分支與合法約束，遞迴實作能力進步；仍需檢驗無參考從零建構。
- 33 Search in Rotated Sorted Array：C，參考完整答案，程式正確；Accepted 與耗時未回報。關鍵弱點為 sorted-half 推理及 start/mid/end 邊界，安排高優先 Active Recall。
- 118 Pascal's Triangle：A，05:51 AC；獨立完成。
- 明確 AC 累計至少 107 題不同 LeetCode；若 33 也已 AC 則 108 題。保留 Day 40 2 Medium +1 Easy 難度；22 進展可視為舊題寫法遷移，不誤記完全無參考 A。


## 2026-11-06 Day 56 更新
- 113 Path Sum II：33:36 AC，C++，暫 A（獨立性待確認）；DFS path push，左右子樹回來由父層 pop，合法葉節點才記錄 path。
- 721 Accounts Merge：43:45 AC，C++，暫 C。使用者明確表示完全抄答案、原本想不出來；下一步驗證能否自己說明 email graph 的連通分量及以首個 email 連接同帳戶內所有 email 的正確性。若仍不能理解核心，依評分標準可能為 D。列高優先複習。
- 459 Repeated Substring Pattern：23:40 AC，C++；s+s 去首尾後 find(s) 的技巧正確，獨立性未說明，尚不評 A/B/C。
- 3 題回報 AC。保留 721 的 graph modeling 弱點及 46/79 的 Backtracking 建構復習方向，不因一次抄答案就降整體每日難度。


## 2026-11-07 未作答紀錄清理
- 依使用者要求清理「僅出題、無作答」紀錄；移除 2026-10-23～31 的九份 assignment-only days/ 檔，並清理 tracker、progress 和本檔的相應待作答內容。
- 保留真正已完成的題目與評分、#33 的參考答案學習、#34 的 11:54 嘗試、#128 的 Hint 1，以及 #79 等 AC 紀錄。
- 後續新題去重以實際完成或已開始嘗試／看 Hint 的題目為準；未作答僅被安排過的題目不再封鎖。Premium 仍排除，複習題不計每日三題。

## 2026-11-09 Day 59 更新
- #78 Subsets：16:10，A，獨立 C++ backtracking AC；比 #46、#79 時能更穩定從零建構 state/undo，但舊題複習仍保留。
- #547 Number of Provinces：35:27 未解，D。將直接鄰接誤當完整連通分量，DFS 草稿 visited 條件反向；屬演算法正確性問題而非純 typo。列高優先複習，不提供完整解法。
- #2264 Largest 3-Same-Digit Number in String：06:54 AC，A（獨立性未特別說明）；O(n) / O(1)。
- 今日 2/3 AC，58:31，明確 AC 累計 113 題。後續保持 2 Medium + 1 Easy，不因 #547 失敗降難度。

## 2026-11-10 Day 60 更新
- #684 Redundant Connection：16:43 第一版自寫，22:37 向 GPT 詢問 Union-Find 寫法，暫 C。兩版貼碼存在問題：endpoint seen 不等於同一 connected component；第二版 parent[n] 未初始化。使用者回報 AC，但需核對實際提交版本；高優先複習 Union-Find from scratch / graph connectivity。
- #39 Combination Sum：17:46，A，完全獨立 C++ backtracking AC；接續 #78 16:10 A，回溯建模已有連續正向證據。
- #268 Missing Number：04:22，A，C++ sum difference AC，O(n) time / O(1) space。
- 3/3 題回報 AC，#684 程式碼無法據此確認 AC；不含 #684 的已確認不同題目累計 115 題，待核對後可達 116。保持 2 Medium + 1 Easy。

## 2026-11-10 #684 確認更正
- #684 使用者再次明確確認第二版 Union-Find 程式在 LeetCode AC，22:37，C（有向 GPT 請教核心實作）。先前誤將 parent[n]=0 判為必然出錯：節點標籤為 1..n，0 不是真正節點，可充當 n 的集合代表；因此本題可 AC，建議改 i<=n 以便閱讀及泛化。累計 **116 題不同題目 AC**，今天 3/3 AC。保留 Union-Find 獨立實作複習。

## 2026-11-11 Day 61 更新
- #841 Keys and Rooms：7:48 C++ 完全獨立 AC，A；Graph BFS / visited 實作進步。
- #416 Partition Equal Subset Sum：32:55 AC，複習 C；看 10/02 舊程式後才完成。核心 DP state/transition 尚無法從零獨立重建，保留高優先 active recall；歷史最佳 B 不覆寫。
- #242 Valid Anagram：6:59 AC，複習 A；只查 C++ unordered_map 語法。歷史最佳 A 不變。
- 今日出題疏失：#416、#242 已在 tracker 完成表中，錯誤再作為新題安排。當日 3/3 AC，但只有 1 題全新，累計 117 題。下次須確實去重，維持 2 Medium+1 Easy 新題原則，不因休息或弱項降低難度。


## 2026-11-17 最新能力與訓練規則更新（優先於前文舊策略）
- #2316 15:28：自行辨認 DFS/Union-Find 候選，但寫不出而抄完整答案；有方向辨認能力，獨立建構仍不穩，不能直接歸類純語法 bug。計數模型是否自行想到尚未知。
- #162、#66：自述心態受挫、各思考超過 10／15 分鐘後抄答案；時間逐題對應未確認。缺少原始嘗試，不能斷言卡點一定是邊界或進位。
- 三題暫 C（理解待驗證），程式演算法邏輯正確但尚未明確回報 AC；不算無提示完成，累計已確認 AC 維持 117。詳細見 days/2026-11-17.md。
- Graph 連通性建模與從零實作仍高優先；Binary Search 區間排除推理繼續補強；DP 狀態設計依 #416 最近複習仍高優先。#78、#39 連續獨立回溯及 #841 獨立 BFS 的進步仍保留，不因今天受挫抹除。
- 分開追蹤 Concept、Algorithm Design、Implementation、Debug、Complexity。今天無法從參考碼證明使用者理解，亦無證據認定看解後不懂，因此先暫評再驗證。
- 維持每日 2 Medium + 1 Easy 全新免費題，分散題型；休息或失敗不自動降難度、不補題。已嘗試／看提示或答案者只能複習，未作答僅安排過者不永久排除。出題僅日期與題號／題名／難度／連結，不透露解法方向。
- 出題前讀 tracker、current state、progress、theory/progress、近 7–14 天 days；不足則往前找最近 5–10 次實際練習。主要 C++、亦可 Python。
- 使用者明確要求才給漸進 Hint，明確要求完整答案才給完整程式。不把語法/API/Debug 與演算法提示混為一談；可讓使用者先說卡在哪，不因時間一到直接公布答案。
- 只有實際回報或 Hint 互動才建立 days；同步維護紀錄、不寫空白排程檔。重做不增加不同題數、最佳評價與當次表現分開。以最近 10–20 題 Medium 無提示 AC 率達至少 60% 為方向，未知獨立性或未確認 AC 不虛構為成功。

## 2026-11-18 實際練習更新
- #785 Medium 20:55 AC，B：Google 提供 BFS/DFS coloring 核心方向，使用者獨立實作 BFS、跨 disconnected component 著色與矛盾檢測；分開記錄 Algorithm Design 外部提示、Implementation 獨立。最壞 O(V²+E)，因外層尋找下個未染色節點每輪重掃。
- #518 Medium 35:01 未解，D（本次）：有自行嘗試 amount-based DP 與 used，但組合數建模錯誤。未索取 Hint，禁止主動透露核心轉移。高優先後續複習。
- #387 Easy 03:11 AC，A：C++ char frequency and first unique index，O(n)/O(1) alphabet bound。
- 今日 2/3 AC、59:07，累計不同 LeetCode 明確 AC **119**（11/17 #2316 #162 #66 均僅參考答案且未明確回報 AC）。需關注最近 10–20 題 Medium 無演算法提示 AC 率，不能把 #785 當無提示；保留 2 Medium+1 Easy，不降難度。

## 2026-11-18 新增 Hint 規則及 #518 追蹤
- 使用者要求：單題練習達 **35 分鐘以上仍未解出** 時，若在對話中回報該狀態，教練應**主動給 Hint 1**，不必等再次索取；不直接跳到 Hint 2/3 或完整解法。無法在沒有訊息的情況下即時監測計時器或主動發送，依使用者回報的時間判斷。
- #518 在 35:01 未解後要求 H1；已用 combination vs permutation 重複計數差異引導，不提供核心轉移。未解狀態維持，當次 D 暫不改變。

## 2026-11-18 #518 完整答案後狀態
- 35:01 未解 -> 使用者要求 Hint 1 -> 再明確要求完整答案；已提供 1D DP 正向更新 C++ 完整解法。從現在起 #518 屬「已看核心解法／尚未本人 AC」，高優先日後無參考複習；不得算無提示 Medium 或增加 AC。當次 D 保留，理解待驗證。近期計數 DP state 與遍歷順序仍需補強。

## 2026-11-19 #210 實際練習更新
- #210 Course Schedule II：40:25，未獨立解出；DFS + 數字 label 想法不能構成正確拓樸排序，visited 未分 visiting/done，無輸出結果與完整 cycle 判斷，另有 n 未宣告等 implementation 問題。向 Gemini 取得正確程式，未貼該程式也未回報本人 AC；40 分鐘規則下教練提供 Kahn 完整解法。獨立建模暫 D，理解待確認，不算獨立 Medium AC；未確認 AC 總數維持 119。
- 近期 Graph traversal 基礎 (#841) 較穩定，但需排序/依賴約束的 Graph design 仍需加強。#875/#338 未回報，不能推斷已開始或完成。

## 2026-11-19 #875、#338 完成與能力更新
- #875 Koko Eating Bananas：21:54 AC，C++ 自行提供正確 binary search on answer，O(n log M)/O(1)，A 暫定（外部演算法提示資訊未確認）；對 Binary Search 變形提供新的正面證據。
- #338 Counting Bits：19:47 AC，使用者明確確認，C++ 最大 2 次方分段 DP 正確，O(n) time/O(n) output space，A 暫定（外部提示資訊未知）。
- 11/19 #210 未獨立解出 40:25，D，Gemini/教練完整解答已看，但未回報本人 AC。今日 2/3 AC，總時間 82:06，累計已確認 **121 題不同 LeetCode AC**。保留 Graph ordering / DFS state 弱點，不因此降低每日 2 Medium+1 Easy 難度。#875 A 不直接假定完全無演算法提示。

## 2026-11-20 部分練習更新
- #399 Evaluate Division：5:04 未解，已知外部 Graph 方向但不會將式子轉換為圖，反映 Graph modeling 卡點；沒有程式或 AC，暫不評分。未到 30 分鐘，不主動再給 Hint；已實際嘗試不得列新題。
- #740 Delete and Earn：35:56 AC，C。獨立 Greedy 嘗試無法完成；向 Gemini 問到 House Robber 的核心 reduction，再獨立建立 counting map + DP；演算法建模需關鍵提示，但 C++ 實作正確，O(n+M) time/O(M) space。保留轉換式 DP 高優先複習方向。
- #605 尚未回報。明確不同 LeetCode AC 累計 122（121 + #740）。此次不是 3 題全部完成，不應記當日完整 AC 率。維持 30 分鐘未解經回報給 Hint、40 分鐘給答案規則。

## 2026-11-20 #399 Hint 2
- Graph 方向仍無法自行轉成模型，使用者要求更具體提示；已提供 weighted graph modeling 的重要 Hint 2：除法關係為有向加權邊，從反向邊及連乘路徑例子思考。尚無 AC／實作回報，不能據此評為獨立解出。

## #399 2026-11-20 37:48 進度更新
- Graph 建模能力有進展：使用者能自行寫正向商權重、反向倒數邊；但 DFS 搜尋目標、visited、路徑乘積與 return 尚無完整架構。另有 C++ unordered_map/pair/push_back/作用域與 Python 語法混用等 implementation 問題。37:48 未 AC；依使用者 30/40 分鐘規則提供 **Hint 3 的 DFS 偽碼 + 語法修正**，尚未提供完整答案。後續須區分 modeling 的改進與依賴重要提示，不能當無提示成功。累計確認 AC 122。

## #399 2026-11-20 最終 AC 更新
- #399 Evaluate Division：**49:47 AC，C**。從 5:04 不知如何建模，到 37:48 自行寫正反向 Graph 草稿，再經 Hint 3 的 DFS 參數與搜尋流程引導，於 49:47 獨立組裝完整 C++ 程式 Accepted。Concept/Algorithm Design 仍依賴重要 Graph 建模與 DFS 方向提示，Implementation、C++ STL/Debug、邊界檢查成功，不應評 D 或無提示 A。Time O(E+Q(V+E))，space O(V+E)。
- 今天 #399 AC C、#740 AC C、#605 尚未回報。累計不同題確認 AC **123**（原 122 + #399）。Graph modeling 仍需無提示再驗證；維持原每日難度。

## 2026-11-20 #605 AC 與完整日結（最新）
- #605 Can Place Flowers：12:33 AC，C 語言 greedy 正確處理 n=0、len=1、頭尾、內部及更新 flowerbed；O(m) time/O(1) extra space，A 暫定（演算法提示資訊未明確回報）。
- 今日 #399 Evaluate Division 49:47 AC C（教練建模／DFS 重要提示）、#740 Delete and Earn 35:56 AC C（Gemini House Robber reduction 提示）、#605 12:33 AC A 暫定。**3/3 AC、98:16、累計已確認不同題 124**。兩題 Medium 並非無提示，核心陌生 Medium modeling 仍需加強；保留適度分散其他題型，不降低 2 Medium + 1 Easy 難度。

## 2026-11-21 #1091 31:21 TLE 實際回報
- #1091 Medium：31:21 TLE，C++ BFS 八方向與 level-based shortest-path 架構已自行建立；重複 enqueue 是 visited 標記過晚的 implementation / performance bug。自行提出從終點往回做的候選想法，但不必換演算法。要求並已取得 Hint 1（觀察多父節點重複入列與 visited 時機）。尚未 AC，不能評 A，也不能判作 Graph algorithm design 完全失敗。優先讓使用者自行 debug，未到 40 分鐘不提供完整程式碼。#279、#2215 尚未作答回報，累計 AC 維持 124。

## 2026-11-21 #1091 35:30 AC 最新狀態
- #1091 Medium：35:30 AC、B，先前 31:21 TLE；自身獨立建立 8-direction level BFS 短路模型，失誤在 visited 於 pop 才設導致重複 enqueue。取得教練 Hint 1 的 Debug 方向後，自行使用 set visited 在 enqueue 時標記，約 4:09 修正 AC。Algorithm Design 正面證據，Implementation/Debug 需少量提示；不要統稱為 Graph modeling 不會。Time O(n² log n)，Space O(n²)；使用 grid 入列即標記可以 O(n²) time。
- 11/21 目前 #1091 AC，其餘 #279/#2215 尚未回報。累計已確認不同 LeetCode AC **125**。維持 2 Medium+1 Easy 及 30/40 分鐘輔助規則。

## 2026-11-21 #279 DP 建模進度
- #279 22:05 未解，能獨立想到一維 DP，但僅以最大平方數做唯一轉移導致不保證最優；教練 Hint 1 提供 n=12 反例，引導比較不同平方數。這是 Algorithm Design 狀態轉移完整性缺口；尚未 AC，最終評分待定。#1091 35:30 B AC、#2215 未回報，累計不同 AC 125。不降低 Medium 難度。

## #279 2026-11-21 Hint 2 及教練互動校正
- 使用者指出知道反例卻不會修改 DP，上一個 Hint 1 不夠具體。已給對症 Hint 2：每個 i 枚舉平方數候選及 dp[i-j*j]+1 最小化；留初始化和寫法讓使用者完成。Algorithm Design 轉移已受重要提示，之後不能以無提示 AC 計。未回報 AC，累計確認 125 不變。

## 2026-11-21 #279 24:06 AC（最新）
- #279 Perfect Squares：24:06 AC，C；原 22:05 只能寫一維 dp + 最大平方數貪婪選擇，知道 12 的反例卻不能自行寫出正確轉移。教練 Hint 2 提供枚舉 j*j<=i 的取最小狀態轉移後，2:01 內自行完成 C++ 並 AC；正確 Implementation，Algorithm Design 依賴重要提示。O(n sqrt n) time / O(n) space，不能算 Medium 無提示 AC。之後複習應由使用者自己從零推導候選枚舉與轉移，提示要針對實際卡點而非重述已知反例。
- 11/21 #1091 35:30 B AC、#279 24:06 C AC、#2215 尚未回報；累計已確認不同 LeetCode AC **126**，不得把 #279 算兩次。

## 2026-11-21 #2215 AC 與最終日結（最新）
- #2215 Find the Difference of Two Arrays：05:39 AC，C++ set 去重、雙向差集正確；O(m log(m+1)+n log(n+1)) time / O(m+n) space，A 暫定（演算法提示資訊未明確回報）。
- 今日 #1091 35:30 AC B（BFS 模型獨立、visited Debug Hint 1）、#279 24:06 AC C（重要 DP 狀態轉移 Hint 2）、#2215 05:39 AC A 暫定；**3/3 AC、65:15、累計不同題明確 AC 127**。重點繼續放在陌生 Medium 的 Algorithm Design 無提示推導，並將 Debug 提示與核心建模提示分開。不因 3/3 AC 自動提高 Medium 無提示 AC 率。


## 2026-11-22 最新能力狀態
- #130 Medium 40:20 AC A（暫定）：自主貼出完整 DFS 連通分量、邊界 flag 與座標集合，O(mn log(mn)) time、O(mn) space。Graph traversal 與 component reasoning 有新正面證據；獨立性仍待確認。
- #983 Medium 30:51 AC A（暫定）：按日 min-cost DP 轉移正確，O(D) time、O(366) space；DP state 設計有新正面證據，外部提示未知。
- #345 Easy 08:54 AC A（暫定）：雙指標交換母音，O(n)/O(1)。
- 今日 3/3 AC，總 80:05；已確認不同 AC **130**。沒有 Idea time、外部查詢、本人 Complexity 解釋與 Debug 歷程，不虛構；嚴格 Medium 無提示 AC 率暫不把 A（暫定）當確證。維持 2 Medium+1 Easy，Graph modeling/DP/Binary Search 動態追蹤。
- 使用者最新規則：**回報單題已超過 30 分鐘且仍未解時直接給提示；超過 40 分鐘且仍未解時直接給完整答案**。無法在使用者未發訊息時自行監測或主動通知。單純花 40 分鐘但已 AC 不須補答案。


### 2026-11-22 後續確認：#130 / #983 獨立性（最新覆蓋先前暫定評價）
- 使用者確認 #130 Surrounded Regions 與 #983 Minimum Cost For Tickets **核心演算法完全獨立想出**，Google **僅查語法**，無演算法提示。兩題本次評價由 **A（暫定）正式改為 A**，計入 Medium 無演算法提示 AC 分子。#130 40:20、#983 30:51，兩題均已 AC；Idea time、Debug 歷程與本人 complexity 解釋仍未知。
- 語法/API 查詢不等於演算法 Hint；#345 獨立性未進一步確認，維持 A（暫定）。不同題 AC 總數仍為 **130**，不得重複加題數。歷史段落保留，依本段最新更正為準。


## 2026-11-23 #802 實際嘗試（最新）
- **#802 Find Eventual Safe States**：Medium，**44:25 未解出，D（本次獨立建模）**；C++ DFS 草稿，已自行想到 visited/state，但用鄰居索引 i 當節點 DFS(i)（應 graph[node][i]）、未正確區分搜尋中/安全/不安全、terminal 未快取、安全節點判斷變數 a 可能未初始化或沿用舊值。
- 依使用者 **40 分鐘以上仍未解直接給完整答案**規則，教練已提供四狀態 DFS C++ 正解與 O(V+E) / O(V) 複雜度。這是外部完整答案，**本人未回報 AC，不可增加不同 AC 題數或計入無提示 Medium AC**；之後僅能作複習，優先驗證 cycle detection 與 memoized DFS 的狀態設計。
- Concept 有 DFS/terminal 概念，Algorithm Design 狀態判定未正確建立，Implementation 鄰居索引及變數使用有錯；Debug、Idea time、本人 Complexity 理解未回報。#1049/#190 尚未回報，不視為完成。**累計確認不同題 AC 仍為 130**。

## #1049 Last Stone Weight II — Medium
- **27:18 AC，C（暫評）**。使用者明確回報「Gemini 教我的」，未具體說明 Gemini 提供到哪一層；保守視為外部核心解法協助，**不得計入 Medium 無提示 AC**。此題已 AC，往後不得列為全新題。
- **使用者提交程式**：先算 total_weight 與 target=total_weight/2；一維 dp[target+1]，逐石頭 s，倒序 i=target..s，dp[i]=max(dp[i],dp[i-s]+s)；return total_weight-2*dp[target]。程式正確，0/1 背包倒序防重複取石頭。
- **Complexity**：O(n*S) time / O(S) space，S=sum(stones)；為教練分析，使用者理解尚未驗證。
- **能力**：Concept 分組最小差值模型是否獨立想出未知；Algorithm Design 受 Gemini 教學，暫 C；Implementation AC；Debug 未回報；本人 complexity 解釋未回報。待確認 Gemini 幫助程度，可修正評分。#190 尚未回報。
- **2026-11-23 更新**：#1049 已確認 AC，與先前 130 題無重複前提下，**不同題 AC 暫更新為 131**；#802 仍未 AC。

### 2026-11-23 #1049 Gemini 協助程度確認（覆蓋先前暫評）
- 使用者明確確認：**Gemini 直接教「分成兩組、轉成 0/1 背包」的核心轉換，並幫忙寫好 DP 轉移式**。因此 #1049 27:18 AC 的 **C 評價正式確認**（非獨立演算法設計、非無提示 Medium AC）。
- Concept 與 Algorithm Design 的核心均由外部協助；Implementation 程式 AC，但使用者獨立編寫程度未確認；Debug 與本人 Complexity 理解未回報。
- #1049 已 AC，累計不同題 AC 仍 **131**，本次只修正獨立性，不重複加題。日後僅當複習，不當新題。
