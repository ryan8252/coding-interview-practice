# Coding Interview 練習進度

## 2026-09-09 — Day 1

| 題目 | Pattern | 難度 | 結果 | 時間 | 紀錄 | 重做日期 |
|---|---|---|---|---:|---|---|
| Two Sum | Brute Force → Hash Map | Easy | A | 6:17 | 完全自己完成並 Accepted。目前使用雙層迴圈，時間複雜度為 O(n²)。下一個目標是不看題目解答，自己想出 O(n) 的 Hash Map 解法。 | 2026-09-10 |
| Valid Parentheses | Stack | Easy | B+ | 7:37 | 自己想到要使用 Stack，只查了 Python Stack 的使用方式，之後獨立完成並 Accepted。目前寫法正確，之後可以再學習如何用括號 Mapping 簡化程式。 | 2026-09-12 |
| Best Time to Buy and Sell Stock | One Pass / Running Minimum | Easy | A | 19:17 | 完全自己找到 O(n) 的核心想法：一路保留目前最好的買入點，並更新最大 profit。Accepted。 | 2026-09-16 |

### Day 1 觀察

目前的基礎比一開始預期的好：基本的程式邏輯與解題能力是有的，主要問題比較像是常見 Coding Interview Pattern 還沒有形成直覺。

因此現階段不需要追求大量刷 Easy 題。重點是：

- 建立常見 Pattern 的辨識能力。
- 理解自己的解法為什麼是 O(n)、O(n²) 等複雜度。
- 同一題如果有更好的解法，要理解「為什麼可以省掉重複工作」。
- 練習在面試時把思考過程說出來。

### 下一個任務

重新做 **Two Sum**，目標把時間複雜度從 **O(n²) 改成 O(n)**。

規則：

- 不搜尋 `Two Sum solution`。
- 可以查 Python Dictionary / Hash Map 的語法，例如如何新增 key、如何判斷 key 是否存在。
- 如果想了約 20 分鐘還是沒有方向，直接回來問 ChatGPT，只拿一層 Hint，不直接看完整答案。
