# C++

## 優先主題

- [x] Pointer vs Object
- [x] Pointer vs Reference
- [x] Object lifetime
- [ ] Stack vs Heap
- [x] `new` / `delete`（基礎 lifetime / memory leak 概念）
- [x] Pass by value / reference（基礎）
- [ ] `const`
- [ ] `vector`
- [ ] `unordered_map`
- [ ] `set` / `unordered_set`
- [ ] `queue` / `stack`
- [ ] Iterator 基礎

## Pointer / Reference / Object Lifetime

### 核心概念

```cpp
ListNode dummy;                 // 建立 ListNode object
ListNode* p;                    // 只建立 pointer，沒有建立 ListNode object
ListNode* p2 = &dummy;          // pointer 指向既有 object
ListNode* p3 = new ListNode();  // new 建立 dynamic object，p3 存它的 address
```

`ListNode` 不是 C++ 內建關鍵字，而是程式先用 struct/class 定義的型別。

```cpp
int x = 10;
int* p = &x;   // &x：取得 x 的 address
*p = 50;       // *p：dereference，存取 p 指向的 object
```

對 struct/class pointer，`p->member` 等價於 `(*p).member`。

### 多個 Pointer 指向同一 Object

```cpp
Student* p = &a;
Student* q = p;
```

這不是 q 指向 p，而是把 p 裡存的 address 複製給 q，因此 p、q 都指向 a。若要取得 pointer p 本身的 address，才是 `&p`。

### Reference

```cpp
int x = 10;
int& r = x;
```

`r` 是 x 的 alias。reference 建立時需要綁定 object；`r = b` 是把 b 的值 assign 給原本綁定的 object，不是讓 reference 改綁 b。

### Function Parameter

```cpp
void f(vector<int> nums);   // copy
void f(vector<int>& nums);  // reference，不複製整個 vector
void f(int* p);             // 接收 int*
```

pointer parameter 需要傳相符的 address，例如 `f(&x)`；reference parameter 呼叫時直接傳 `x`。

### Object Lifetime / Dangling Pointer

```cpp
int* p;
{
    int x = 10;
    p = &x;
}
// x lifetime 已結束，p 成為 dangling pointer
```

dangling pointer 可能仍保存原本 address，但 object 已不存在，不能安全 dereference。這與 `nullptr`（沒有指向 object）不同。

### `new` / `delete` 基礎

```cpp
ListNode* p = new ListNode();
delete p;
```

`p` 是 pointer；`new ListNode()` 才建立 dynamic object。raw `new` 配置的 object 不會因離開目前 scope 自動消失，若沒有適當釋放可能造成 memory leak。

### Dummy Node 常見錯誤

錯誤：

```cpp
ListNode* dummy;
ListNode* tail = dummy;
tail->next = head;
```

只有 pointer，沒有有效的 ListNode object；`tail->next` 需要 dereference tail，因此是 undefined behavior。

可改為：

```cpp
ListNode dummy;
ListNode* tail = &dummy;
tail->next = head;
return dummy.next;
```

## 本次容易搞混 / 答錯

- 一開始漏判 `ListNode* d = new ListNode();` 中 d 本身也是 pointer；真正的 object 是 `new ListNode()` 建立的。
- 一開始對 `b->next` 的描述是「b 沒有 next」，後來修正為：pointer 本身沒有 member；`b->next` 是存取 b 指向的 object 的 next。
- 曾把 `Student* q = p` 認成 q 指向 p；經 tracing 後已能正確解釋為 p、q 存同一個 object address。
- 能正確區分 nullptr 與 dangling pointer。
- Stack vs Heap 尚未完整教學與 Active Recall，不標記完成。

## 自測

- `ListNode* p;` 到底建立了什麼？
- `p`、`*p`、`&x` 分別代表什麼？
- 為什麼 `p->next` 等價於 `(*p).next`？
- `T* q = p` 是否代表 q 指向 p？為什麼？
- nullptr 與 dangling pointer 有什麼差別？
- pass-by-value 與 pass-by-reference 對大型 vector 有什麼差異？

## 複習紀錄

| 日期 | 主題 | 評價 | 待補強 |
|---|---|---|---|
| 2026-10-01 | Pointer / Reference / Object Lifetime | A | 約一週後短測；之後補 Stack vs Heap、const 與更完整的 resource management |
