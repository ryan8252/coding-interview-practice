# Coding Interview 練習進度

## 2026-09-09 — Day 1

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Two Sum | Brute Force → Hash Map | Easy | A | 6:17 | 完全自己完成並 Accepted。目前使用雙層迴圈，時間複雜度為 O(n²)。下一個目標是不看題目解答，自己想出 O(n) 的 Hash Map 解法。 | 2026-09-10 |
| Valid Parentheses | Stack | Easy | B+ | 7:37 | 自己想到要使用 Stack，只查了 Python Stack 的使用方式，之後獨立完成並 Accepted。目前寫法正確，之後可以再學習如何用括號 Mapping 簡化程式。 | 2026-09-12 |
| Best Time to Buy and Sell Stock | One Pass / Running Minimum | Easy | A | 19:17 | 完全自己找到 O(n) 的核心想法：一路保留目前最好的買入點，並更新最大 profit。Accepted。 | 2026-09-16 |

### Day 1 觀察

目前的基礎比一開始預期的好：基本的程式邏輯與解題能力是有的，主要問題比較像是常見 Coding Interview Pattern 還沒有形成直覺。

因此現階段不需要追求大量刷 Easy 題。重點是建立常見 Pattern 的辨識能力、理解時間複雜度，以及練習把思考過程說出來。

---

## 2026-09-10 — Day 2

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Two Sum（第二次） | Hash Map | Easy | A | 10:24 | 成功把昨天的 O(n²) 雙層迴圈改成 O(n) Hash Map。每次先計算 complement `target - nums[i]`，檢查是否已存在於 dictionary；若不存在再存入目前數字與 index。只查詢 `python check key in dictionary` 的語法，沒有查題目解法。 | 2026-09-17 |
| Contains Duplicate | Hash Map / Set concept | Easy | A | 5:06 | 一次掃描 nums；如果數字已存在於 dictionary 就立即回傳 True，否則記錄它。獨立完成並 Accepted。這題其實只需要判斷「是否看過」，之後要理解為什麼 Set 比 Dictionary 更符合語意。 | 2026-09-17 |
| Valid Palindrome | Two Pointers | Easy | A | 11:53 | 先自己清理字串，只保留英文字母與數字，並把大寫轉成小寫；接著使用左右兩個 pointer 從兩端往中間比較。只查詢 Python lowercase 語法。獨立完成並 Accepted。 | 2026-09-18 |

### Day 2 觀察

今天三題都能獨立找到核心演算法，只查 Python 語法／API，因此都記為 A。特別重要的是 Two Sum：一天後已經能把 O(n²) 解法主動改成 O(n) Hash Map，表示 Hash Map「記住已看過資訊、避免重複搜尋」的概念開始建立。

Contains Duplicate 也自然沿用了相同概念；下一步要區分 Dictionary 與 Set 的使用情境。Valid Palindrome 則成功第一次實際使用 Two Pointers。

---

## 2026-09-11 — Day 3

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Valid Anagram | Hash Map / Frequency Counting | Easy | A | 12:53 | 使用 dictionary 計算第一個字串各字元出現次數，再用第二個字串逐一扣除；計數歸零就刪除 key，最後確認 dictionary 為空。查詢 `python unordered_map`、`dict del`、`dict empty`，屬於資料結構／語法查詢，沒有查題目解法。 | 2026-09-18 |
| Move Zeroes | Queue-based in-place tracking | Easy | B | 18:25 | 自己設計出以 deque 記錄目前 zero index 的方法，遇到 non-zero 時搬到最早的 zero 位置，再把新的 zero 位置加入 queue，成功 Accepted。查詢 Stack / Queue。解法可行且時間約 O(n)，但額外 Queue 最壞需要 O(n) 空間，尚未達到這題想訓練的 O(1) space Two Pointers 解法，因此安排較早重做。 | 2026-09-13 |
| Two Sum II - Input Array Is Sorted | Two Pointers | Medium | A | 12:40 | 根據「已排序」與題目前提供的左右 pointer 提示，從兩端開始：sum 太大就右 pointer 左移，太小就左 pointer 右移，相等則回傳 1-based indices。獨立完成程式並 Accepted，O(n) time / O(1) extra space。 | 2026-09-19 |

### Day 3 觀察

Hash Map / Counting 已開始形成直覺，Valid Anagram 能自行設計 frequency counter。Two Sum II 也能把 sorted array 與左右 Two Pointers 的移動方向連結起來。

今天最值得複習的是 Move Zeroes：目前的 Queue 解法不是錯誤，而且能 Accepted，但它額外保存所有等待填補的 zero index。下一次重做時，目標是不使用 deque / list / 額外陣列，只用兩個整數 pointer，在 O(n) time、O(1) extra space 下完成。

### 接下來要加強

- Frequency Counting：熟悉「增加計數 → 減少計數 → 判斷是否一致」的模式。
- Two Pointers：區分「左右夾逼」與「同方向 fast/slow pointer」兩種常見形式。
- Move Zeroes 在 9/13 重做時，不使用 Queue，嘗試 fast/slow pointer。
- 每題能寫出來後，仍要練習口頭說出 Time Complexity 與 Space Complexity。
