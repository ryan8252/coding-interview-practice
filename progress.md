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

### 接下來要加強

- Hash Map / Set：看到「是否出現過、是否重複、查找 complement」時開始主動想到。
- Two Pointers：不只會寫左右 pointer，也要練習在原字串上跳過無效字元，避免一定要先建立清理後的新字串。
- 每題 Accepted 後練習口頭說明 Time Complexity 與 Space Complexity。
