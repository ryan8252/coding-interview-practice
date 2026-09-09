# Progress Log

## 2026-09-09 — Day 1

| Problem | Pattern | Difficulty | Result | Time | Notes | Retry |
|---|---|---|---|---:|---|---|
| Two Sum | Brute Force → Hash Map | Easy | A | 6:17 | Independently solved with an O(n²) nested-loop approach. Next goal: derive the O(n) hash-map solution without looking up the problem solution. | 2026-09-10 |
| Valid Parentheses | Stack | Easy | B+ | 7:37 | Independently identified the stack idea; looked up how to use a stack in Python. Accepted. Current implementation is correct but can later be simplified with a bracket mapping. | 2026-09-12 |
| Best Time to Buy and Sell Stock | One Pass / Running Minimum | Easy | A | 19:17 | Independently found the O(n) idea: keep the best buy point seen so far and update maximum profit. | 2026-09-16 |

### Day 1 observation

The baseline is stronger than initially expected: basic problem-solving logic is present, but common interview patterns are not yet automatic. The immediate focus should be pattern recognition and explaining why an approach has the desired time complexity, rather than simply accumulating many Easy problems.

### Next task

Re-solve **Two Sum** in O(n) time without searching for the Two Sum solution. Looking up Python dictionary syntax/API is allowed.
