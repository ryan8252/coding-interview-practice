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


---

## 2026-09-22 — Day 14

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 104. Maximum Depth of Binary Tree | Binary Tree / Depth | Easy | A | 12:43 | Python，無查詢、無 Hint，自行完成。延續 543 後，這次已能獨立處理 Tree depth。 |
| 367. Valid Perfect Square | Binary Search | Easy | A | 13:55 | Python，無查詢、無 Hint，自行完成 Binary Search 判斷 perfect square。 |
| 213. House Robber II | Dynamic Programming / Case Split | Medium | C | 33:31 | Python。Hint 1 指出首尾不能同時選；Hint 2 明確指出拆成「不搶第一間」與「不搶最後一間」兩次普通 House Robber，再取最大值。核心轉換由提示提供，因此記 C；DP 實作自行完成。 |

### Day 14 觀察

104 與 367 都無提示完成，顯示 Binary Tree depth 與 Binary Search 的基礎穩定度持續提升。

213 的主要弱點不是 recurrence，而是遇到額外 constraint 時如何做 case split。後續應安排重做，確認能否自行把 circular problem 轉成兩個 linear subproblems。

### 接下來要加強

- House Robber II 之後安排無提示重做。
- Binary Tree 可逐步增加 postorder / recursive 變化。
- Binary Search 持續用不同 boundary 類型驗證。
- Sliding Window 之後重做 3，目標 O(n)。
- 保留 C++ pointer / object 初始化短複習。


---

## 2026-09-23 — Day 15

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 83. Remove Duplicates from Sorted List | Linked List | Easy | A | 7:10 | Python，無查詢、無 Hint，自行完成並 Accepted。 |
| 322. Coin Change | Dynamic Programming | Medium | C | 23:17 | 一開始完全沒有方向，後來 Google 演算法後才掌握 DP transition，最後自行寫出 `dp[i] = min(dp[i], dp[i-c] + 1)` 並 Accepted。因核心演算法是查到的，記 C；後續需無提示重做。 |
| 112. Path Sum | Binary Tree / Path State | Easy | A | 17:20 | Python，無查詢、無 Hint。自行用 iterative traversal 維護 path sum，leaf 時判斷 target，成功 Accepted。 |

### Day 15 觀察

83 與 112 都能無提示完成，顯示 Linked List 與 Tree 的基礎操作已逐漸穩定。

322 顯示 DP 能力目前仍偏向熟悉的 recurrence 類型；遇到「多個 coin transition + 取最小值」的 state design 時還無法自行推導。後續應安排 Coin Change 無提示重做，或用相似 min-DP 題驗證。

### 接下來要加強

- 322 Coin Change 無提示重做。
- DP 擴展到 min/max transition 與多來源 transition。
- Tree 繼續加入 path / postorder 類題型。
- Sliding Window 之後重做 3，目標 O(n)。
- 保留 C++ pointer / object 初始化短複習。


---

## 2026-09-24 — Day 16

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 110. Balanced Binary Tree | Binary Tree / Bottom-up Depth | Easy | A | 13:25 | Python，無 Hint，自行完成。使用 stack + dictionary 模擬 postorder，先處理 child，再計算 parent depth 並檢查左右高度差。543 曾卡住的 child -> parent aggregation 這次已能獨立完成。 |
| 27. Remove Element | Two Pointers / In-place Array | Easy | A | 39:15 | Python，無 Hint，自行完成並 Accepted。使用左右 pointer 把要移除的值往後處理，O(n) time / O(1) extra space。控制流程較繞，但核心自行完成。 |
| 64. Minimum Path Sum | Dynamic Programming / Grid Min DP | Medium | A | 約 25:00 | Python，無 Hint，自行完成。忘記一開始按計時，實際約 25 分鐘。自行建立 2D DP，第一列/第一行分開處理，其餘位置取上方與左方較小值再加目前格子。 |

### Day 16 觀察

110 是重要進展：Tree 已從 traversal / path-state 進一步到能無提示完成 bottom-up depth aggregation。

64 則顯示在 322 Coin Change 卡住後，已能自行完成另一種 minimum DP，表示 DP state / transition 能力開始擴展。

### 接下來要加強

- Tree 繼續用不同 postorder / bottom-up 題驗證。
- DP 繼續 min/max transition 類題，並保留 322 Coin Change 無提示重做。
- 出題前檢查歷史紀錄，避免把已做過的題當新題。

---

## 2026-09-25 — Day 17

> 744 與 1290 實際提交已跨到 2026-09-26 00:xx，但使用者明確指定這組仍算 9/25；2026-09-26 的每日練習尚未開始。

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 120. Triangle | Dynamic Programming | Medium | A | 20:22 | Python，原題無 Hint、自行完成 2D DP 並 Accepted。Accepted 後才研究 O(n) extra space follow-up；空間壓縮解法最後由 GPT 直接提供，所以原題仍記 A，optimization 另列學習內容。 |
| 744. Find Smallest Letter Greater Than Target | Ordered Scan | Easy | A | 9:43 | Python。核心演算法自行完成；因不熟 Python 語法詢問 GPT，屬語法/API 查詢，不算演算法提示。線性掃描找到第一個大於 target 的字元，否則 wrap-around 回傳第一個。 |
| 1290. Convert Binary Number in a Linked List to Integer | Linked List / Running Value | Easy | A | 13:02 | Python，完全自己完成。逐 node traversal，使用 `n = n * 2 + head.val` 累積值，並正確執行 `head = head.next`。 |

### 複習題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 35. Search Insert Position | Binary Search | Easy | A（複習） | 7:12 | 之前已用 Python 做過，本次改用 C++ 重做並 Accepted，不計入今日新題。 |
| 643. Maximum Average Subarray I | Sliding Window | Easy | A（複習） | 4:40 | 之前已用 Python 做過，本次改用 C++ 重做 fixed-size window，Accepted，不計入今日新題。 |

### Day 17 觀察

120 是連續第二天出現 min-DP 無提示成功（前一天 64），顯示 DP 類型正在擴展；但 O(n) space optimization 不是自行完成，之後仍需新題驗證空間壓縮能力。

1290 再次驗證 Linked List traversal 已穩定。35、643 因出題重複，這次只算複習，不列入每日 3 題新題。

### 接下來要加強

- 出新題前先查 `progress.md` / 最近 `days/`，避免重複。
- 120 的 O(n) space follow-up 之後可無提示重做。
- 322 Coin Change 仍需無提示重做。
- 3 Longest Substring Without Repeating Characters 仍保留 O(n) 重做目標。
- 2026-09-26 尚未開始每日練習。


---

## 2026-09-26 — Day 18

> 58、111、62 的實際提交有部分跨到 2026-09-27，但依使用者指定全部算在 9/26；2026-09-27 的練習尚未開始。

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 58. Length of Last Word | String | Easy | A | 2:10 | Python，完全自己完成，沒有查資料、沒有拿 Hint。 |
| 111. Minimum Depth of Binary Tree | Binary Tree / BFS | Easy | A | 25:14 | Python，完全自己完成，沒有查資料、沒有拿 Hint。自行使用 level-order traversal，遇到第一個 leaf 回傳 depth。 |
| 62. Unique Paths | Combinatorics | Medium | A | 5:15 | Python，完全自己完成，沒有查資料、沒有拿 Hint。自行由路徑所需的固定步數推導組合數解法並 Accepted。 |

### Day 18 觀察

今天 3 題新題全部 A。111 驗證 Tree BFS；62 顯示 grid path 題也能從組合數角度自行解出。

### 接下來要加強

- Tree 可繼續混合 BFS / DFS。
- DP / recurrence 持續不同型態，322、213 仍保留複習。
- 2026-09-27 尚未開始每日練習。


---

## 2026-09-27 — Day 19

> 931 實際提交跨到 2026-09-28 00:06，但依既有規則仍算在 9/27；2026-09-28 練習尚未開始。

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 680. Valid Palindrome II | Two Pointers | Easy | C | 37:55 | Python，有看解答，因此核心結構不是完全自行推出。之後需無提示重做。 |
| 374. Guess Number Higher or Lower | Binary Search | Easy | A | 3:47 | Python，自行完成並 Accepted。 |
| 931. Minimum Falling Path Sum | Dynamic Programming / Space Optimization | Medium | A | 30:24 | Python，只詢問 `list.copy()` 語法/API；演算法核心自行完成。使用 previous/current row 一維狀態，依三個上一列來源的最小值更新。 |

### Day 19 觀察

374 再次驗證 Binary Search 已穩定。931 是第一次在沒有取得演算法提示的情況下，自行完成明確的一維 DP space optimization，因此這方面能力有新的正向證據。

680 因看解答記 C，列入後續複習。


---

## 2026-09-28 — Day 20

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 94. Binary Tree Inorder Traversal | Binary Tree / Iterative Traversal | Easy | A | 9:00 | Python，自己完成。使用 stack + dictionary 記錄 visited node，因此額外 O(n) space；核心 inorder traversal 自行完成。 |
| 136. Single Number | Bit Manipulation / XOR | Easy | B | 4:29 | Python，有看提示，並查 Python XOR 語法；最後 Accepted。 |
| 300. Longest Increasing Subsequence | DP / Binary Search | Medium | C | 40:05 | Python。先自行想到 O(n²) DP state；之後主動挑戰 O(n log n)，經多層提示理解 tails / 最小結尾值，最後 Binary Search 更新完整寫法由 GPT 提供。 |

### Day 20 觀察

94 顯示 Tree traversal 已熟，但 iterative inorder 還可進一步去掉 visited 結構。

300 顯示 O(n²) DP 思路已能自行建立，但 O(n log n) tails + lower_bound 還需要主要提示，因此列入複習。


---

## 2026-09-29 — Day 21

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 1413. Minimum Value to Get Positive Step by Step Sum | Prefix Sum | Easy | A | 9:59 | Python，自己完成。 |
| 237. Delete Node in a Linked List | Linked List / Node Mutation Trick | Medium | C | 14:47 | Python。因看不懂題意直接問 GPT；解釋已涵蓋核心技巧：copy next value + skip next node，因此記 C。 |
| 455. Assign Cookies | Greedy / Sorting | Easy | A | 13:35 | Python，自己完成。 |

### Day 21 觀察

1413 與 455 都是無提示完成。237 的主要問題是題意與資料結構限制的理解，而不是語法；之後應無提示重做。


---

## 2026-09-30 — Day 22

### 新題

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 |
|---|---|---|---|---:|---|
| 219. Contains Duplicate II | Hash Map / Last Seen Index | Easy | A | 12:32 | Python，自己完成；記錄每個值最近一次出現的位置並檢查 index distance。 |
| 705. Design HashSet | Hash Table Design | Easy | C | 23:22 | Python。詢問 GPT modulo、bucket、collision、separate chaining、linear probing 等核心設計概念，因此記 C。 |
| 152. Maximum Product Subarray | Dynamic Programming / Max-Min State | Medium | B | 43:23 | Python。先自行嘗試；之後拿到同時維護 max/min ending product 的關鍵提示，再自行完成 recurrence 並 Accepted。 |

### Day 22 觀察

219 的 Hash Map 應用已能獨立完成。705 需要補 Hash Table 底層設計。152 對 max/min 雙狀態 DP 已有初步理解，但仍需無提示重做確認。


---

## 2026-10-01 — Day 23

### 新題

| 題目 | Pattern | 難度 | 結果 | Idea | Hint | Accepted | 紀錄 |
|---|---|---|---|---:|---:|---:|---|
| 733. Flood Fill | Graph/Grid Traversal | Easy | A | 2:57 | 無 | 13:14 | 2:57 讀題後形成主要方向；11:14 第一版程式完成但有 bug；13:14 自行修正 Accepted。演算法核心完全自行辨認。Python implementation 使用 list + `pop(0)`，且在 dequeue 後才染色，之後可改 deque 並在 enqueue 時標記以避免重複加入。 |
| 349. Intersection of Two Arrays | Sorting / Two Pointers | Easy | A | 1:00 | 無 | 7:52 | 0:20 讀完題目，1:00 想到解法，7:52 Accepted。自行排序兩陣列並使用 two pointers；原本以 dictionary 防重複。Accepted 後詢問不用 dictionary 的方式，理解排序後可比較 `ans[-1]` 去重。沒有查演算法。 |
| 139. Word Break | Reachability / BFS-State Modeling | Medium | B | 6:05（初步） | H1 22:30 | 47:25 | 0:50 讀完。6:05 有「找到字就從剩餘字串繼續」的想法，但本質上仍是單一路徑 greedy，且不知道如何實作。22:30 H1 提示改思考「哪些 index 可以到達」，之後自行用 reachable positions 建立 queue 式 traversal 並 Accepted。只詢問 Python slicing 語法，不算演算法提示。後續又理解 `pop(0)`、list membership 的成本，以及 deque / set 可改善 implementation。 |

### Day 23 觀察

- 733、349 的 Idea time 分別為 2:57、1:00，Easy 題的辨認與建模速度良好。
- 139 的主要卡點不是語法，而是 **如何把字串切割問題轉成 state / reachability model**。在 H1 後能自行延伸出 queue 式解法，因此評 B 而非 C。
- 139 列入高優先複習：目標是無提示自行說明為何 greedy 不成立、建立 reachable/DP state，並完成解法。
- 今日再次確認：之後分析單題表現時，要區分 Idea time 與 Accepted time。733 雖總共 13:14，但主要想法在 2:57 已形成，後段主要是 implementation/debug。

### 後續複習

- 高優先新增：139 Word Break。
- 139 下次重做時，不先告知 BFS / DP；要求先自行定義 state，再驗證能否無提示完成。
