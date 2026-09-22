# Coding Interview 練習進度

## 2026-09-09 — Day 1

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Two Sum | Brute Force → Hash Map | Easy | A | 6:17 | 完全自己完成並 Accepted。目前使用雙層迴圈，時間複雜度為 O(n²)。下一個目標是不看題目解答，自己想出 O(n) 的 Hash Map 解法。 | 2026-09-10 |
| Valid Parentheses | Stack | Easy | B+ | 7:37 | 自己想到要使用 Stack，只查了 Python Stack 的使用方式，之後獨立完成並 Accepted。目前寫法正確，之後可以再學習如何用括號 Mapping 簡化程式。 | 2026-09-12 |
| Best Time to Buy and Sell Stock | One Pass / Running Minimum | Easy | A | 19:17 | 完全自己找到 O(n) 的核心想法：一路保留目前最好的買入點，並更新最大 profit。Accepted。 | 2026-09-16 |

---

## 2026-09-10 — Day 2

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Two Sum（第二次） | Hash Map | Easy | A | 10:24 | 成功把昨天的 O(n²) 雙層迴圈改成 O(n) Hash Map。只查詢 Python dictionary 語法，沒有查題目解法。 | 2026-09-17 |
| Contains Duplicate | Hash Map / Set concept | Easy | A | 5:06 | 一次掃描 nums；如果數字已存在於 dictionary 就立即回傳 True，否則記錄它。獨立完成並 Accepted。 | 2026-09-17 |
| Valid Palindrome | Two Pointers | Easy | A | 11:53 | 先清理字串，再使用左右 pointer 從兩端往中間比較。只查詢 Python lowercase 語法。獨立完成並 Accepted。 | 2026-09-18 |

---

## 2026-09-11 — Day 3

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Valid Anagram | Hash Map / Frequency Counting | Easy | A | 12:53 | 使用 dictionary 計算字元頻率，再用第二個字串逐一扣除。查詢 `python unordered_map`、`dict del`、`dict empty`，沒有查題目解法。 | 2026-09-18 |
| Move Zeroes | Queue-based in-place tracking | Easy | B | 18:25 | 自己設計 deque 記錄 zero index 的方法並 Accepted，但最壞需要 O(n) 額外空間，尚未掌握 O(1) space 的標準做法。 | 2026-09-13 |
| Two Sum II - Input Array Is Sorted | Two Pointers | Medium | B | 12:40 | 成功 Accepted，但事前提示已明確指出左右 pointer 以及 sum 太大／太小的移動方向，因此不視為獨立辨認 Pattern。之後需要用另一題在無提示下重新測試。 | 2026-09-19 |

---

## 2026-09-12 — Day 4

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Valid Parentheses（第二次） | Stack | Easy | A | 13:15 | 這次沒有事前 Pattern 提示，且改用 C++ 完成。自己使用 `vector<char>` 模擬 Stack，以 `push_back`、`back`、`pop_back` 配對括號。只查詢 C++ vector 用法，屬於語法/API 查詢。成功 Accepted。 | 2026-09-20 |
| Remove Duplicates from Sorted Array | Two Pointers / Fast-Slow | Easy | A | 16:47 | 在沒有任何 Pattern 提示下，自己使用 `i`、`j` 兩個 index：`j` 掃描陣列，遇到新值時推進 `i` 並覆寫 `nums[i]`。成功 Accepted，O(n) time / O(1) extra space。這是第一次在無提示下自行做出典型同方向 Two Pointers。 | 2026-09-20 |
| Best Time to Buy and Sell Stock（第二次） | One Pass / Running Minimum | Easy | A | 22:17 | 改用 C 完成。一路維護目前最低買入價 `b`，並用當前價格計算 profit、更新最大值 `p`。沒有查解法，成功 Accepted，O(n) time / O(1) space。相較 Day 1，已能用不同語言重現相同核心演算法。 | 2026-09-21 |

### Day 4 觀察

今天三題都沒有事前告知 Pattern，而且三題都能自行完成，因此比有提示時的 Accepted 更能反映實際能力。

最重要的進展是 Remove Duplicates from Sorted Array：在不知道題型名稱的情況下，自行寫出典型 fast/slow pointer 結構。這表示同方向 Two Pointers 已開始從「看過提示才會」轉成可以自行推導。

---

## 2026-09-13 — Day 5

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Search Insert Position | Binary Search | Easy | A | 11:59 | 沒有事前 Topic 提示，自己使用 `i`、`j`、`m` 縮小搜尋範圍，找到 target 就回傳 `m`，找不到時回傳插入位置 `i`。成功 Accepted，核心為 O(log n) 搜尋。 | 2026-09-21 |
| Reverse Linked List | Linked List Pointer Reversal | Easy | B | 15:29 | 成功使用 `prev`、`cur`、`nxt` 逐步反轉 `next` 指向並 Accepted。不過有查「需要幾個 ptr」，這已經屬於演算法方向提示，不單純是語法查詢，因此不算完全獨立辨認。之後要在不查 pointer 數量的情況下重做一次。 | 2026-09-17 |
| Maximum Average Subarray I | Sliding Window | Easy | A | 4:45 | 沒有事前 Topic 提示，先算前 `k` 個元素的總和，之後每往右移一格就減掉離開視窗的元素、加上新元素，並更新最大平均值。成功 Accepted，O(n) time。這是第一次在無提示下自行做出典型 Sliding Window。 | 2026-09-22 |

### 複習題（不計入每日 3 題新題）

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 下次複習 |
|---|---|---|---|---:|---|---|
| Move Zeroes（第二次） | In-place compaction / Fast-Slow concept | Easy | A（複習） | 17:53 | 這次不用 deque，改成先把 non-zero 依序寫到前面，再把剩餘位置補 0。成功做到 O(n) time / O(1) extra space，代表已修正 Day 3 的空間問題。 | 2026-09-24 |

### Day 5 觀察

今天的新題比前幾天更能顯示 Pattern 遷移能力。Search Insert Position 能自行做出 binary search；Maximum Average Subarray I 更是在 4:45 內自己做出 sliding window，代表你不只是記住既有 Pattern，也開始能從題目條件自行設計高效率的一次掃描方法。

Reverse Linked List 目前要保守看待：程式本身是正確的，但「查需要幾個 pointer」已經透露了核心結構，所以先記 B，之後安排無提示重做。

Move Zeroes 的第二次解法則是很好的複習成果：從 Day 3 的 O(n) 額外 queue，進步到 O(1) extra space，表示前一天在 Remove Duplicates 學到的 in-place index 操作有成功遷移。

---

## 2026-09-14 — Day 6

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 704. Binary Search | Binary Search | Easy | B | 8:44 | Accepted。程式能正確縮小搜尋範圍，但當時有搜尋 `Binary search implementation`，因此不算完全獨立完成。 |
| 141. Linked List Cycle | Linked List / Cycle Detection | Easy | B | 18:28 | 約 10 分鐘沒有方向後拿 Hint 1。最後先利用最多約 10,000 nodes 的 constraint 做 workaround，之後再學 Set 與 Floyd slow/fast。 |
| 977. Squares of a Sorted Array | Two Pointers | Easy | A | 10:44 | 沒有提示，平方後從左右兩端比較較大值，依序放入結果。 |

另外補強 Linked List traversal，曾漏掉 `cur = cur.next`，因此把 pointer 往後移列為近期需要特別注意的基本動作。

---

## 2026-09-15 — Day 7

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 21. Merge Two Sorted Lists | Linked List / Dummy + Tail | Easy | C | 43:22 | 前 40 分鐘卡住，之後拿到核心提示 `dummy` + `tail` 才完成。理解 `return dummy.next` 的原因。 |
| 448. Find All Numbers Disappeared in an Array | In-place Marking | Easy | B | 16:16 | 先自己做出 O(n) extra-space 解法；要做到 O(1) extra space 時，正負號 marking 需要提示。 |
| 88. Merge Sorted Array | Two Pointers / Backward Merge | Easy | A | 15:50 | 沒有提示，自行從尾端往前原地合併，O(m+n) time / O(1) extra space。 |

### 複習題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 206. Reverse Linked List | Pointer Reversal | Easy | A（複習） | 10:44 | 使用 C 自己重做 `prev` / `cur` / `nxt`，沒有再查 pointer 數量。 |

---

## 2026-09-16 — Day 8

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 203. Remove Linked List Elements | Linked List | Easy | A | 21:55 | 使用 Python，沒有拿 Hint，Linked List 新題獨立成功。 |
| 724. Find Pivot Index | Prefix Sum / Running Sum | Easy | A | 5:39 | 沒有拿 Hint，快速完成。 |
| 392. Is Subsequence | Two Pointers | Easy | A | 約 5:00 | 使用 Python，沒有拿 Hint；忘記計時，所以時間為估計值。 |

### 複習題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 1. Two Sum | Hash Map | Easy | A（複習） | 約 14:00 有效時間 | 使用 C++；畫面 24:01，但中間約 10 分鐘滑手機。只詢問 `unordered_map` / return 等 C++ 語法，核心演算法自己完成。 |
| 121. Best Time to Buy and Sell Stock | One Pass / Running Minimum | Easy | A（複習） | 約 3:00 | 使用 Java，忘記計時；再次重現 O(n) time / O(1) space 解法。 |

---

## 2026-09-17 — Day 9

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 160. Intersection of Two Linked Lists | Linked List / Hash Set | Easy | B | 19:20 | 使用 Python。已自行想到記錄 A 的 node、再走 B 尋找同一 node，但 traversal 與收尾卡住；Hint 1 後補上 pointer 前進和 return 邏輯。也確認 `dict` / `set` 可以直接存 `ListNode` 物件。 |
| 169. Majority Element | Hash Map / Frequency Counting | Easy | A | 11:59 | 使用 Python，沒有拿 Hint。dictionary 計數並在次數超過 `n/2` 時立即 return。O(n) time / O(n) space。 |
| 70. Climbing Stairs | Dynamic Programming / Recurrence | Easy | A | 9:39 | 使用 Python，沒有拿 Hint，自行得到 `s[i] = s[i-1] + s[i-2]`。O(n) time / O(n) space。 |

### 複習題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 141. Linked List Cycle | Floyd Slow/Fast | Easy | A（複習） | 7:56 | 使用 C++，沒有拿 Hint，直接寫出 Floyd slow/fast，O(n) time / O(1) space。相較 Day 6 已明顯內化。 |

### Day 9 觀察

Linked List 有明顯進步：Reverse、Remove Elements、Cycle 都已有無提示成功紀錄；160 的核心方向也能自己想到。不過 traversal 時漏掉 pointer 前進仍再次出現，因此基礎 pointer 操作仍要持續用短題鞏固。

Climbing Stairs 是目前第一次 recurrence / DP 類型的成功，先視為新能力訊號，之後要用不同題型再次驗證。

### 接下來要加強

- 出題時繼續不提供 Topic / Pattern。
- 每天至少 3 題全新題目，複習題另外計算。
- Linked List 繼續安排短小新題與複習，但不要一天塞太多。
- 特別驗證 dummy/tail 是否能在不同 Linked List 題中自行想到。
- Binary Search、Sliding Window、Two Pointers 需要換題再次確認辨認能力。
- DP / recurrence 才剛出現第一次成功，之後安排 Easy 新題驗證，不事前提示是 DP。


---

## 2026-09-18 — Day 10

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 876. Middle of the Linked List | Linked List / Slow-Fast | Easy | A | 5:50 | 使用 Python，沒有拿 Hint。直接把 slow / fast pointer 從 Cycle 類題遷移到「找中點」的新情境，O(n) time / O(1) space。 |
| 14. Longest Common Prefix | String / Prefix Scan | Easy | A | 11:18 | 使用 Python，沒有拿 Hint。以第一個字串為基準逐字元檢查其他字串；遇到長度不足或字元不同就停止。演算法正確，控制流程可再簡化。 |
| 746. Min Cost Climbing Stairs | Dynamic Programming / Recurrence | Easy | A | 7:23 | 使用 Python。只請 ChatGPT 將英文題意翻成白話，沒有取得演算法提示；之後自行得到 `s[i] = cost[i] + min(s[i-1], s[i-2])`。這是連續第二天無提示完成 recurrence / DP 類題。 |

### 複習題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 21. Merge Two Sorted Lists | Linked List / Dummy + Tail | Easy | A（複習） | 10:22 | 使用 C++。核心 `dummy + tail`、比較兩條 list、接上剩餘 list 與回傳結果都能自行重現。詢問 GPT 的內容是 debug C++ pointer 初始化：`ListNode* dummy;` 只有宣告未初始化 pointer，`tail=dummy` 後直接 `tail->next` 會存取無效位置。這屬於語言 / pointer 基礎問題，不是演算法提示，因此仍記 A。相較 9/15 第一次 C、43:22，進步明顯。 |

### Day 10 觀察

今天 3 題新題全部 A。slow/fast pointer 已能跨題遷移；DP / recurrence 也連續兩天無提示成功，代表這類能力開始形成。

Merge Two Sorted Lists 的演算法核心已能自行重現；目前暴露出的弱點轉為 **C++ pointer / object 初始化**，之後需要安排獨立短複習，特別確認以下概念：

- 宣告 pointer 不等於建立 object
- `ListNode dummy;` 會建立一個 object
- `ListNode* p = &dummy;` 是讓 pointer 指向既有 object
- `new ListNode()` 會建立 object 並回傳 pointer
- 使用 `ptr->member` 前，`ptr` 必須先指向有效 object

### 接下來要加強

- 安排 C++ pointer 初始化 / object vs pointer 短複習，不計入每日 3 題新題。
- Linked List 繼續用不同題型驗證 dummy / tail，而不是只重做 21。
- DP / recurrence 再用不同型態 Easy 題驗證。
- Binary Search、Sliding Window、Two Pointers 仍需要換題持續驗證 pattern recognition。


---

## 2026-09-19 — Day 11

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 3. Longest Substring Without Repeating Characters | Sliding Window | Medium | B | 50:30 | 第一題正式加入訓練的 Medium。Hint 1 後自行完成 O(n²) / O(1) space 的 window 解法；每次掃描目前合法 window 找重複，沒有直接採用標準 Hash Map / Set O(n) 解。之後安排重做，目標自行消掉內層掃描。 |
| 100. Same Tree | Binary Tree / DFS Traversal | Easy | B | 26:27 | 第一次正式碰 Binary Tree。查詢 tree traversal 與 Python stack；traversal 屬核心基礎，因此記 B。之後自行完成同步 traversal / compare 並 Accepted。 |
| 69. Sqrt(x) | Binary Search / Boundary | Easy | C | 19:27 | Hint 1 後仍無方向，Hint 2 明確指出 Binary Search。主體自行寫出，但最後錯誤回傳 `mid`；經說明後理解 loop 結束時 `end` 是最大合法值，改成 `return end` 後 Accepted。 |

### 複習題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 125. Valid Palindrome | Two Pointers | Easy | A（複習） | 12:48 | 使用 C++，左右 pointer 從兩端往中間比較；本輪未回報查題目解法或拿 Hint。 |

### Day 11 觀察

今天開始把訓練往下一階段推：加入基礎 Medium、第一次正式 Tree、以及需要處理 boundary 的 Binary Search。

- Longest Substring 已能自己維護合法 window，但目前以時間換空間，O(n²) / O(1)；之後要學會用額外結構換成 O(n)。
- Tree traversal 是全新基礎，目前需要查資料屬正常學習階段，下一次換題再驗證能否自行重現。
- Binary Search 主體不是最大問題，真正需要補的是「最大合法值 / 最小合法值」這類 boundary 與 loop 結束後 start/end 的語意。

### 接下來要加強

- 逐步採用 2 Easy + 1 基礎 Medium。
- 重做 3，目標 O(n) sliding window。
- 安排 Binary Tree Easy 題驗證 traversal。
- 安排 Binary Search boundary 類短練習。
- 保留 C++ pointer / object 初始化的短複習。


---

## 2026-09-20 — Day 12

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 226. Invert Binary Tree | Binary Tree / Iterative Traversal | Easy | A | 11:17 | Python，完全無查詢、無 Hint。自行用 stack traversal 交換每個 node 的左右 child。相較 Day 11 Same Tree 還需要查 traversal，今天已能無查詢重現。 |
| 278. First Bad Version | Binary Search / First True | Easy | A | 16:15 | Python，完全無查詢、無 Hint。自行寫出 first-true boundary binary search，最後回傳第一個 bad version。相比 Day 11 Sqrt(x) 的 boundary 問題有明顯進步。 |
| 198. House Robber | Dynamic Programming | Medium | A | 9:41 | Python，完全無查詢、無 Hint。自行得到 `m[i] = max(nums[i] + m[i-2], m[i-1])`。目前最乾淨的一次 Medium 無提示成功之一。 |

### 複習題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 203. Remove Linked List Elements | Linked List / Dummy + Tail | Easy | A（複習） | 6:28 | C++。演算法與 dummy/tail 自行完成；先寫出未初始化 `ListNode* dummy;`，程式錯誤後才詢問 GPT 如何建立 dummy node，改為 `new ListNode()`。演算法仍記 A，但 C++ pointer/object 初始化仍需補強。 |

### Day 12 觀察

今天 3 題新題全部 A，而且正好驗證了昨天較弱的 Tree 與 Binary Search boundary，兩者都有明顯改善。House Robber 則顯示 DP / recurrence 已開始穩定遷移到 Medium。

C++ pointer/object 初始化錯誤第二次出現，因此之後要把它當成獨立基礎能力練習，而不是只在 linked-list 題裡順便處理。

### 接下來要加強

- 維持 2 Easy + 1 基礎 Medium。
- 重做 3 Longest Substring Without Repeating Characters，目標 O(n) sliding window。
- Tree 再換一題驗證 traversal。
- Binary Search 再換一種 boundary 形式驗證。
- 安排 C++ pointer/object 初始化短複習。


---

## 2026-09-21 — Day 13

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 543. Diameter of Binary Tree | Binary Tree / Depth Aggregation | Easy | C | 51:52 | Python。先自行嘗試 iterative stack / dictionary，後續詢問 GPT 並取得主要解題結構：child depth、`max(left,right)` 與 `left+right`。因此記 C。顯示 traversal 已較熟，但 bottom-up / postorder thinking 還不穩。 |
| 209. Minimum Size Subarray Sum | Sliding Window | Medium | A | 23:20 | Python，完全自己完成。維護可伸縮 window，右指標單向前進，整體 O(n) time / O(1) extra space。相較 3 題的 O(n²) window 有明顯進步。 |
| 202. Happy Number | Hash / Cycle Detection | Easy | A | 7:41 | Python，完全自己完成。使用 dictionary 記錄已出現狀態來偵測 cycle；若只需 membership 可改用 set。 |

### Day 13 觀察

209 是今天最重要的進步：Medium、無提示、O(n) Sliding Window，代表這個 pattern 已開始內化。

543 顯示 Binary Tree 的新弱點已從「traversal」轉成「如何由 child 的結果回推 parent」，也就是 postorder / bottom-up depth aggregation。後續應用短小 Tree 題驗證。

### 接下來要加強

- Binary Tree：安排 depth / bottom-up 類 Easy 題。
- Sliding Window：之後重做 3，目標自行從 O(n²) 改成 O(n)。
- 維持 2 Easy + 1 基礎 Medium。
- 保留 C++ pointer / object 初始化短複習。
