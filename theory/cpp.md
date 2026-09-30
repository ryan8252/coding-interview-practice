# C++

## 優先主題

- [ ] Pointer vs Object
- [ ] Pointer vs Reference
- [ ] Object lifetime
- [ ] Stack vs Heap
- [ ] `new` / `delete`
- [ ] Pass by value / reference
- [ ] `const`
- [ ] `vector`
- [ ] `unordered_map`
- [ ] `set` / `unordered_set`
- [ ] `queue` / `stack`
- [ ] Iterator 基礎

## 目前已知弱點

### Pointer / Object 初始化

曾在 Linked List 題中寫出：

```cpp
ListNode* dummy;
ListNode* tail = dummy;
```

之後直接使用 `tail->next`。需要持續確認以下差異已真正內化：

```cpp
ListNode dummy;              // 建立 local object
ListNode* p1 = &dummy;       // pointer 指向既有 object
ListNode* p2 = new ListNode(); // 建立 dynamic object
ListNode* p3;                // 只有宣告 pointer，沒有建立 object
```

## 筆記

之後每次複習把整理後的概念補在這裡。

## 自測

- `ListNode* p;` 到底建立了什麼？
- `ListNode dummy;` 的 lifetime 到什麼時候？
- `ListNode* p = &dummy;` 中，誰擁有 object？
- pointer 和 reference 最主要的語意差異是什麼？
- 什麼情況下應避免手動 `new` / `delete`？

## 複習紀錄

| 日期 | 主題 | 評價 | 待補強 |
|---|---|---|---|
