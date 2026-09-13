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

### 接下來要加強

- 出題時繼續不提供 Topic / Pattern。
- 每天至少 3 題全新題目，複習題另外計算。
- Reverse Linked List 安排短期無提示重做，確認 Linked List pointer 操作是否真正內化。
- Binary Search 與 Sliding Window 都已出現第一次無提示成功，接下來需要用不同題型驗證是否能重複辨認。
