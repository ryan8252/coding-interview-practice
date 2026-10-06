# C++

## 優先主題

- [x] Pointer vs Object
- [x] Pointer vs Reference
- [x] Object lifetime
- [x] Stack vs Heap
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
ListNode dummy;
ListNode* p;
ListNode* p2 = &dummy;
ListNode* p3 = new ListNode();
```

`ListNode` 不是 C++ 內建關鍵字，而是程式先用 struct/class 定義的型別。

```cpp
int x = 10;
int* p = &x;
*p = 50;
```

對 struct/class pointer，`p->member` 等價於 `(*p).member`。

### 多個 Pointer 指向同一 Object

```cpp
Student* p = &a;
Student* q = p;
```

不是 q 指向 p，而是把 p 裡存的 address 複製給 q，因此 p、q 都指向 a。若要取得 pointer p 本身的 address，才是 `&p`。

### Reference

```cpp
int x = 10;
int& r = x;
```

`r` 是 x 的 alias。reference 建立時需要綁定 object；`r = b` 是把 b 的值 assign 給原本綁定的 object，不是讓 reference 改綁 b。

### Function Parameter

```cpp
void f(vector<int> nums);
void f(vector<int>& nums);
void f(int* p);
```

pointer parameter 需要傳相符的 address，例如 `f(&x)`；reference parameter 呼叫時直接傳 `x`。

### Stack vs Heap / Dynamic Allocation

面試常用的簡化模型：一般 local automatic object 通常在 stack；`new` 建立的 dynamic object 通常在 heap。更重要的是 **lifetime 與 ownership**，而不是只背位置。

```cpp
void f() {
    int x = 10;
    int* p = new int(20);
}
```

`x` 與 pointer variable `p` 的 lifetime 會在 scope 結束時結束，但 `new int(20)` 建立的 dynamic object 不會因此自動消失。若失去最後能找到它的 pointer，會造成 memory leak。

```cpp
int* p = new int(10);
delete p;
```

`delete p` 釋放的是 p 指向的 dynamic object，不是刪除 pointer variable p。p 若仍存在且保留舊 address，就成為 dangling pointer；dereference 是 undefined behavior。

pointer variable 與 pointee object 的 lifetime **彼此獨立**：
- pointer 可以先消失，而 dynamic object 還活著。
- object 可以先被 delete，而 pointer 還存在。

### Return Pointer 與 Object Lifetime

```cpp
int* bad() {
    int x = 10;
    return &x;
}
```

function return 後 `x` lifetime 已結束，因此回傳的 pointer dangling。

```cpp
int* create() {
    return new int(10);
}
```

dynamic object 在 function return 後仍活著，回傳的 pointer 可使用；但之後必須由適當 owner 負責 cleanup。

### Dynamic Object 實作

```cpp
Student* createStudent(int score) {
    return new Student(score);
}

void destroyStudent(Student* p) {
    delete p;
}
```

`Student* p` parameter 是 pass-by-value：callee 收到 caller pointer value 的 copy。因此在 function 內做 `p = nullptr` 不會讓 caller 的 pointer 也變成 nullptr。

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

- 2026-10-01：曾把 `Student* q = p` 認成 q 指向 p；經 tracing 後已修正。
- 2026-10-06：一開始把「pointer 消失、dynamic object 還活著」誤答成 dangling pointer，經一次修正後已能穩定區分：這是 memory leak；dangling pointer 是 pointer 還在但 object lifetime 已結束。
- 能正確解釋 `delete` 不會讓 pointer variable 本身消失。
- 能從 object lifetime 解釋 return local address 與 return dynamic object pointer 的差異。
- 能獨立寫出 `createStudent()` / `destroyStudent()`。
- 能正確回答 `destroyStudent(Student* p)` 中 `p = nullptr` 不會修改 caller pointer，因為 pointer parameter 是 pass-by-value。

## 自測

- `ListNode* p;` 到底建立了什麼？
- `p`、`*p`、`&x` 分別代表什麼？
- pointer variable 與它指向 object 的 lifetime 是否綁定？
- memory leak 與 dangling pointer 的差異？
- `delete p` 刪除的是 p 還是 pointee object？
- 為什麼不能安全 return local object 的 address？
- 為什麼 `Student* p` parameter 裡做 `p = nullptr` 不會改到 caller？

## 複習紀錄

| 日期 | 主題 | 評價 | 待補強 |
|---|---|---|---|
| 2026-10-01 | Pointer / Reference / Object Lifetime | A | 約一週後短測；之後補 Stack vs Heap、const 與更完整的 resource management |
| 2026-10-06 | Stack vs Heap / Dynamic Allocation | A | 一開始混淆 memory leak / dangling pointer，但修正後穩定；約 1～2 週後短測 lifetime / ownership 即可 |
