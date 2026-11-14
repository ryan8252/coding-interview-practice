# 系統軟體面試問答整理（OS + C/C++ 基礎）

> 複習用途：群暉 Product Developer 等系統軟體職缺。依 2026/11 前幾天的口頭模擬問答與複習主題重新整理為「面試官提問 → 建議回答」，不是逐字對話紀錄。  
> 範圍：Process、Thread、Synchronization、Deadlock、Memory Management、Virtual Memory、C/C++ Pointer 與記憶體生命週期。**不包含尚未學習的物件導向／Virtual Function。**

## CH03：Process 與作業系統基礎

### Q1. Process 和 Thread 有什麼差別？
**建議回答：** Process 是正在執行的程式及其資源集合，通常擁有獨立的虛擬位址空間。Thread 是 Process 內的執行單位。同一個 Process 的 Threads 共享 Code、Data、Heap 及開啟的資源，但各自擁有 Program Counter、Registers 和 Stack。Thread 間共享資料方便、建立與切換通常較輕量，但需要處理同步與 Race Condition。

### Q2. Process 有哪些主要狀態？I/O 完成後去哪裡？
**建議回答：** 常見狀態是 New、Ready、Running、Waiting/Blocked、Terminated。執行中的 Process 若等待 I/O，會由 Running 進入 Waiting；I/O 完成後通常進入 **Ready**，等待 Scheduler 分派 CPU，而不是直接變成 Running。

### Q3. Context Switch 是什麼？為什麼有成本？
**建議回答：** OS 切換執行中的 Process 或 Thread 時，需保存舊執行單位的 CPU Context，例如 Registers、Program Counter，並恢復新執行單位的狀態。這段時間通常不直接完成應用程式工作，也可能造成 Cache 與 TLB 命中率下降，所以有額外成本。不能把 Context Switch 直接等同於把 PCB 複製到磁碟。

### Q4. PCB 是什麼？保存哪些資訊？
**建議回答：** PCB（Process Control Block）是 OS 管理 Process 的資料結構，記錄 PID、Process State、Program Counter、CPU Registers、Scheduling、Memory Management 與 I/O 等相關資訊。OS 依此追蹤及恢復 Process 的執行狀態。

### Q5. Text、Data、BSS、Heap、Stack 通常存什麼？
**建議回答：** Text 放程式指令；Data 放已初始化的全域與靜態變數；BSS 放未明確初始化或零初始化的全域與靜態變數；Heap 用於動態配置；Stack 通常用於函式呼叫紀錄與自動儲存期的區域變數。實際位置受平台、編譯器與最佳化影響，不能僅憑「是不是 local」判斷所有情況，例如 local static 不是一般 Stack 區域變數。

### Q6. fork() 是什麼？呼叫三次會產生幾個 Process？
**建議回答：** 在 Unix 類系統中，fork() 建立 Child Process，Parent 與 Child 會從 fork() 返回的位置繼續執行；Parent 得到 Child PID，Child 得到 0。若每個 Process 都無條件執行三次 fork()，最後共有 **2³ = 8 個 Process（含原本的 Parent）**。現代系統通常使用 Copy-on-Write，並非立即完整複製所有實體記憶體頁。

### Q7. fork() 之後 Child 修改變數，Parent 會跟著變嗎？
**建議回答：** 一般不會。fork() 後兩者各有自己的邏輯位址空間；即使初期因 Copy-on-Write 共用實體頁面，寫入時也會建立適當的私有副本。若要交換資料，需要 IPC 或刻意建立的 Shared Memory 等機制。

### Q8. fork() 和 exec() 有什麼差別？
**建議回答：** fork() 建立新的 Process；exec 系列函式則用新程式映像取代目前 Process 的程式內容，通常不建立新的 Process。exec 成功後不會返回原本的呼叫位置；只有失敗時才返回。

### Q9. Zombie 與 Orphan Process 有什麼差別？wait() 的用途？
**建議回答：** Zombie 是 Child 已結束，但 Parent 尚未收取其結束狀態，因此仍保留少量核心紀錄。Parent 可以用 wait()/waitpid() 回收狀態。Orphan 則是 Parent 先結束、Child 還在執行，Child 會由系統指定的其他 Process 收養及處理回收。

## CH04：Multithreading

### Q10. 為什麼要使用 Multithreading？風險是什麼？
**建議回答：** 多執行緒能提升程式回應能力、重疊 I/O 與計算，並在多核心上平行執行。Threads 共享記憶體，溝通效率高，但同時修改 Shared Data 可能產生 Race Condition，需要 Mutex、Atomic 等同步方式；也可能發生 Deadlock。

### Q11. Concurrency 和 Parallelism 有何不同？
**建議回答：** Concurrency 是多個工作在時間上交錯推進，不要求真正同一瞬間執行；Parallelism 是同時在不同執行資源上執行。單核心可以有 Concurrency，但通常無法同時平行執行多段 CPU 指令；多核心才有真正 CPU Parallelism 的條件。

### Q12. User-Level Thread 和 Kernel-Level Thread 差在哪？常見映射模型是什麼？
**建議回答：** User-Level Thread 的管理主要由使用者空間 Runtime 負責；Kernel-Level Thread 由核心排程。Many-to-One 把多個 User Threads 對應一個 Kernel Thread，通常無法利用多核心同時執行，而且 Blocking Call 可能阻塞整個映射；One-to-One 每個 User Thread 對應一個 Kernel Thread；Many-to-Many 將多個 User Threads 映射到多個 Kernel Threads，在彈性與管理成本間取捨。

### Q13. 兩個 Threads 只讀 Shared Variable，需要 Mutex 嗎？
**建議回答：** 若確定所有存取都是讀取且物件已安全初始化，一般不需為讀取本身加 Mutex。但如果另一個 Thread 可能同時寫入，就必須用適當同步機制避免 Data Race；不能只看「目前這個 Thread 是讀取」便判定安全。

## CH06：Synchronization

### Q14. Race Condition 和 Critical Section 是什麼？
**建議回答：** Race Condition 指結果會因並行執行的時序而改變。Critical Section 是存取共享且需協調狀態的程式區域，例如讀取、加一、寫回 Shared Counter 的整個操作；只把最後一行寫入上鎖，通常不能保護整個 Read–Modify–Write。

### Q15. 為什麼 counter++ 不是天然 Thread-Safe？
**建議回答：** counter++ 在一般情況下可視為讀取舊值、計算新值、寫回等步驟。兩個 Threads 可能讀到同一舊值，之後各自寫回而遺失更新。C++ 若多個 Threads 未同步地存取同一非 Atomic 變數，且至少一方寫入，會形成 Data Race，屬 Undefined Behavior。

### Q16. Critical Section 問題的三個要求？
**建議回答：** Mutual Exclusion：同時最多只有一個執行單位在 Critical Section。Progress：無人在 Critical Section 時，需要進入者不能無限期遭到無關延遲。Bounded Waiting：提出進入要求後，其他人搶先進入的次數應有上限，以避免 Starvation。

### Q17. Mutex 和 Semaphore 有什麼差別？
**建議回答：** Mutex 主要用於互斥保護共享資源，通常有鎖定者與解鎖者的所有權語意。Semaphore 維護一個計數值，wait/P 消耗可用額度，signal/V 釋放額度，可用於資源數量管理或事件通知。Binary Semaphore 計數最多 1，但語意不一定與有 Owner 的 Mutex 完全相同。

### Q18. Counting Semaphore 能怎麼用？
**建議回答：** 若同時只允許 3 個工作使用某資源，可把 Semaphore 初始化為 3。每個工作進入前 wait、離開後 signal；當可用額度耗盡，後續工作必須等待。它很適合限制並行工作數或可用資源實例數。

### Q19. Spinlock 和 Blocking Mutex 差在哪？
**建議回答：** Spinlock 取得鎖失敗時持續 Busy Waiting，適合持鎖極短且不適合睡眠的特定情境，但會占用 CPU。Blocking Mutex 在競爭時可讓 Thread 等待、由系統排程其他工作，較適合等待可能較久的情況。實際效能依鎖實作與競爭程度而定。

### Q20. std::atomic 和 Mutex 差在哪？
**建議回答：** std::atomic 提供對單一 Atomic 物件操作的原子性及記憶體順序控制，例如 atomic counter 的 fetch_add。Mutex 可把跨多個變數、數個步驟組成的整段操作當成 Critical Section。即使每個變數都是 Atomic，也不代表跨多個 Atomic 操作的業務不變條件自然成立。

### Q21. 為什麼 volatile 不能取代 Mutex 或 Atomic？
**建議回答：** C/C++ volatile 主要影響對特定物件存取的最佳化行為，常見於 Memory-Mapped I/O 等用途；它**不保證 Thread Synchronization、原子性或必要的跨執行緒記憶體順序**。多執行緒同步應使用 Atomic、Mutex 等適當工具。

### Q22. 為什麼不能只用一個普通的 global flag 當鎖？
**建議回答：** 單純 if(flag == 0) 然後 flag = 1 的「檢查再設定」不是單一不可分割操作，兩個 Threads 可能同時看到 0 而進入 Critical Section。此外，普通變數的跨 Thread 讀寫若缺乏同步也可能造成 Data Race。應採用正確的原子操作或 OS 同步原語。

### Q23. Message Queue 和 Event 有何差別？
**建議回答：** Message Queue 傳遞有內容的訊息，可依序緩衝多筆資料，常用於工作派送與 Process/Thread 間通訊。Event 主要表示某個條件或事件已發生，通常不承載完整的工作資料；是否保留、重置及合併通知取決於具體 API。選擇時要看是否需要攜帶資料、排隊與保留每個事件。

### Q24. Deadlock 是什麼？怎麼避免？
**建議回答：** Deadlock 是多個執行單位互相等待彼此持有的資源，導致沒有進展。典型必要條件包含 Mutual Exclusion、Hold and Wait、No Preemption、Circular Wait。常見預防方法是所有 Threads 依一致順序取得多把鎖，或使用 std::lock / scoped_lock 等正確地一次取得多把鎖的方式。

## CH08–09：Memory Management / Virtual Memory

### Q25. Virtual Address 和 Physical Address 的差別？MMU 做什麼？
**建議回答：** CPU 執行程式時通常使用 Virtual Address；MMU 透過 Page Table 等資訊將其轉換為 Physical Address，並配合權限與有效性檢查。每個 Process 通常擁有自己的 Virtual Address Space，提供隔離和彈性配置；但有虛擬位址不代表該位址一定合法或已配置實體頁框。

### Q26. Page、Frame、Page Number、Offset 是什麼？
**建議回答：** Page 是 Virtual Memory 的固定大小區塊，Frame 是 Physical Memory 的對應區塊。Virtual Address 可拆成 Page Number 和 Page Offset。以 4 KiB Page 為例，offset 佔 12 bits；Page Number = 位址整數除以 4096，Offset = 位址對 4096 取餘數。位址轉換後 Offset 不變，只將 Page Number 對應到 Frame Number。

### Q27. VA = 10000、Page Size = 4096、對應 Frame = 5，PA 是多少？
**建議回答：** Page Number = 10000 // 4096 = 2；Offset = 10000 % 4096 = 1808。Physical Address = 5 × 4096 + 1808 = **22288**。

### Q28. Page Table 和 TLB 差在哪？
**建議回答：** Page Table 保存虛擬頁到實體頁框的映射及相關權限狀態；TLB 是快取最近使用的位址轉換資訊。TLB Hit 可快速取得轉換；TLB Miss 通常需要 Page Table Walk。**TLB Miss 不等於 Page Fault**，因為 Page 仍可能已在 RAM 中。

### Q29. Page Fault 是什麼？發生後會怎樣？
**建議回答：** 存取的頁面目前沒有可用的有效映射時，硬體可能觸發 Page Fault Exception，由 OS Handler 判斷原因。若是合法的 Demand Paging 且頁面不在 RAM，OS 將頁面載入可用 Frame，必要時選 Victim Page 並在 Dirty 時先回寫，更新 Page Table/TLB 狀態，通常再重新執行造成 Fault 的指令。若是非法存取，則不會當作正常缺頁載入，而可能終止程式。並非所有 Page Fault 都需要磁碟 I/O。

### Q30. Dirty Page 和 Clean Page 有什麼差別？
**建議回答：** Dirty Page 表示自載入或上次同步後內容被修改；替換時若要保存修改內容，可能需要寫回 Backing Store。Clean Page 沒有需要保存的修改，通常可直接捨棄並在未來重新取得，因此替換成本可能比較低。

### Q31. FIFO 與 LRU Page Replacement 差別？
**建議回答：** FIFO 淘汰最早被載入的 Page；LRU 淘汰**最久沒有被存取**的 Page。LRU 並不是「存取次數最少」；以存取頻率決策的是 LFU。LRU 並非保證對每個 Reference String 都比 FIFO 少 Fault。

### Q32. 3 個 Frames、Reference String 1 2 3 1 4 2 5 1 2 3：FIFO 和 LRU 各幾次 Page Fault？
**建議回答：** 一開始 Frames 全空，首次載入也算 Fault。FIFO 為 **8 次**；LRU 也是 **8 次**。兩者可能在不同步驟換出不同頁面，不能單看總 Fault 次數判斷替換過程相同。

### Q33. Thrashing 是什麼？大量 Page Fault 為什麼影響效能？
**建議回答：** 當系統可用 Physical Frames 不足以容納程式頻繁使用的 Working Set，可能反覆載入與淘汰 Pages，導致時間主要花在 Paging 而不是有效計算，這稱為 Thrashing。Major Page Fault 需要較慢的儲存裝置 I/O，會增加等待及 Context Switch 等成本；但不是所有 Page Fault 都涉及 Disk，也不是 Fault 多就必然構成 Thrashing。

### Q34. 如果備份程式發生大量 Page Fault，如何診斷和改善？
**建議回答：** 我會先觀察記憶體使用量、Page Fault Rate、Swap 活動、Disk I/O 與 Process 的 Working Set，確認是否為 Memory Pressure，而不是先假設所有慢速都由缺頁造成。若是記憶體不足，可減少同時執行的備份工作、使用分批或串流讀取、降低不必要的記憶體配置、檢查 Memory Leak、改善 Locality，必要時增加 RAM，讓常用 Working Set 留在 Memory。

## C/C++：Pointer、Reference 與資源生命週期

### Q35. Pointer 和 Reference 有什麼差別？
**建議回答：** Pointer 是保存位址的變數，可為 nullptr、可以重新指向其他物件，存取指向的物件需使用 * 進行 Dereference。Reference 是既有物件的別名，宣告時必須初始化，不能再重新綁定。對 Reference 賦值，是修改它所參考的物件，而不是改變綁定。

### Q36. int* p = &x 和 int& r = x 分別代表什麼？
**建議回答：** 前者用 &x 取得 x 的地址，並把地址存入 Pointer p；後者的 int& 是宣告 Reference 型別，r 成為 x 的別名。這兩個 & 出現在不同語法位置，意思不同。

### Q37. 先以 Pointer 把 x 改成 20，再以 Reference 改成 30，最後輸出什麼？
**建議回答：** 輸出 **30**，因為 Pointer 和 Reference 都存取同一個 x，而且後一次賦值將 x 更新為 30。

### Q38. int a=10, b=20; int* p=&a; int& r=a; p=&b; r=b; *p=30; 輸出 a、b、r？
**建議回答：** 輸出 **20 30 20**。p=&b 讓 Pointer 轉而指向 b；r=b 不會重新綁定 Reference，而是把 b 當時的數值 20 寫入 a；最後 *p=30 修改 b，r 仍是 a 的別名。

### Q39. int x=5, y=10; int& a=x; int& b=y; a=b; b=20; 最後 x、y、a、b？
**建議回答：** 分別是 **10、20、10、20**。a=b 等同把 y 當時的值 10 指派給 x，a 始終是 x 的別名；後續 b=20 只修改 y。

### Q40. 回傳區域變數地址有什麼問題？
**面試題：**
```cpp
int* createNumber() {
    int x = 100;
    return &x;
}
```
**建議回答：** x 具有自動儲存期，函式結束時生命週期結束。回傳其地址後，Pointer 會變成 Dangling Pointer；解參考它是 Undefined Behavior，不保證印出 100。最簡單的修正是直接 `int createNumber() { return 100; }`，若必須由函式修改呼叫者的資料，也可接受 Pointer 或 Reference 參數。

### Q41. Stack 和 Heap 在 C++ 中有什麼差別？
**建議回答：** 自動儲存期的區域物件通常在 Stack 上，離開作用域時生命週期結束。動態配置的物件通常由 Heap/Free Store 管理，生命週期不隨建立它的函式結束而自動結束，需由正確的資源管理機制釋放。new/delete 與 malloc/free 屬不同配置介面，不應混用；現代 C++ 優先利用容器與 RAII 避免手動管理。

### Q42. int* p = new int(10); int* q = p; delete p; 接著 *q 和 delete q 有什麼問題？
**建議回答：** p 和 q 是不同 Pointer 變數，但原本指向同一個動態配置物件。delete p 釋放該物件後，兩者都成為 Dangling Pointers；*q 是 Use-After-Free，delete q 是 Double Delete，都是 Undefined Behavior。必須只釋放一次，且不能在釋放後再存取。

### Q43. delete p; p = nullptr; 會使原本指向同位置的 q 一起變成 nullptr 嗎？
**建議回答：** 不會。p 和 q 是不同的 Pointer 變數；將 p 改成 nullptr 不會修改 q。q 仍是無效的 Dangling Pointer，不能解參考。也不能以「某個指標已設為 nullptr」推論其他 Alias 就安全。

### Q44. Memory Leak、Dangling Pointer、Double Free 各是什麼？
**建議回答：** Memory Leak 是動態配置的資源未被正常釋放且程式已失去可管理它的途徑；Dangling Pointer 指向生命週期已結束或已失效的物件；Double Free/Delete 是重複釋放同一配置資源，可能破壞記憶體管理狀態。應明確管理 Ownership，盡量使用標準容器、RAII 與合適的 Smart Pointer。

### Q45. Pass by Value、Pass by Pointer、Pass by Reference 有什麼不同？
**建議回答：** Pass by Value 傳入值的副本，修改參數一般不影響呼叫者變數；Pass by Pointer 傳入地址的副本，經由 *p 可修改呼叫者的物件，但在函式內改變 p 本身不會改變呼叫者的 Pointer；Pass by Reference 讓參數成為呼叫者物件的別名，直接對參數賦值會修改原物件。

### Q46. C 語言裡 volatile 可以拿來做 Thread Synchronization 嗎？
**建議回答：** 不行。volatile 不等同原子操作，也不構成互斥鎖。需要同步共享狀態時，應使用平台/語言提供的 Atomic 或 Mutex 等機制。若是在 Embedded 中讀寫 Memory-Mapped Device Register，volatile 的目的則是避免編譯器省略必要存取。

---

## 面試前快速複習

**最優先背熟的區分：** Process vs Thread、Concurrency vs Parallelism、Mutex vs Semaphore、Atomic vs Mutex、TLB Miss vs Page Fault、FIFO vs LRU、Pointer vs Reference、Dangling Pointer vs Memory Leak vs Double Free。

**答題習慣：** 先用一句話定義 → 解釋機制 → 給一個例子 → 如果是 Debugging 題，再補診斷或改善方式。遇到不會的觀念可先描述自己確定的部分，不要把不熟悉的細節說得太肯定。
