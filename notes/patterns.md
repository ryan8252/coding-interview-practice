# 演算法 Pattern 筆記

這裡不是用來抄每一題的完整解答，而是記錄之後遇到其他題目也可以重複使用的解題觀念。

## Hash Map

### 什麼時候可能要想到它？

當題目一直需要問：

- 「這個值之前有沒有出現過？」
- 「我要找的另一個值存不存在？」
- 「我是不是一直重複搜尋同一批資料？」

可以想想看是否能用 Hash Map 記住已經看過的資訊，避免重複搜尋。

### 目前的學習目標

**Two Sum：** 第一次 Accepted 使用兩層迴圈，因此時間複雜度是 O(n²)。下一步要思考：如果把已經看過的數字存起來，是否可以不用每次都重新往後搜尋？

---

## Stack

### 什麼時候可能要想到它？

當問題具有「最後放進去的東西，要最先處理」的特性時，可以考慮 Stack。

也就是：

**LIFO（Last In, First Out，後進先出）**

### Python 基本用法

```python
stack = []
stack.append(x)  # push：放進 Stack
x = stack.pop()  # pop：取出最後放進去的元素
```

### 從哪一題學到？

**Valid Parentheses：** 自己判斷出左括號需要先存起來，遇到右括號時再和最近的左括號配對。解題時只查詢了 Python Stack 的語法。

---

## One Pass / Running Minimum

### 什麼時候可能要想到它？

如果目前位置的答案只依賴「前面看過的最佳值」，可以思考是否只需要一邊掃描、一邊維護那個最佳值，而不是把所有組合都比較一次。

### 從哪一題學到？

**Best Time to Buy and Sell Stock：** 一路記住目前為止最低的買入價格／位置，再用現在的價格計算可以得到的 profit，並持續更新最大 profit。這樣可以用 O(n) 完成。

---

## Linked List 基礎

### 最重要的 traversal 骨架

```python
cur = head

while cur is not None:
    # 使用 cur.val
    cur = cur.next
```

目前要先熟悉：

- `node.val`：目前節點儲存的值
- `node.next`：下一個節點
- `None`：Linked List 結尾
- 每一輪如果要往下走，必須做 `cur = cur.next`

如果忘記更新 pointer，while loop 會一直停在同一個 node。

### ListNode 的基本概念

```python
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
```

目前不要求死背 Python class 語法，但要理解建立一個 node 時會保存 value，並透過 `next` 指向下一個 node。

---

## Linked List Cycle

### 方法 1：Set 記錄看過的 node

重點：Set 要存 **node 本身**，不是 `node.val`。

即使兩個 node 的 value 相同，它們仍然是不同 node。

```python
seen = set()
cur = head

while cur is not None:
    if cur in seen:
        return True
    seen.add(cur)
    cur = cur.next

return False
```

- Time: O(n)
- Space: O(n)

### 方法 2：Floyd Slow / Fast Pointer

```python
slow = head
fast = head

while fast is not None and fast.next is not None:
    slow = slow.next
    fast = fast.next.next

    if slow == fast:
        return True

return False
```

直覺：slow 每次走 1 步，fast 每次走 2 步。有 cycle 時兩者進入環後，fast 最終會追上 slow；沒有 cycle 時 fast 會先碰到 `None`。

- Time: O(n)
- Space: O(1)

### Constraint-based workaround

如果題目明確保證最多只有固定數量的 node，也可以利用這個上限：走超過最大可能 node 數仍然沒有遇到 `None`，依 pigeonhole principle 可以推論存在 cycle。

這個方法在特定 constraint 下是合法的，但不夠泛用；如果 Linked List 長度未知，就不能依賴固定 counter。
