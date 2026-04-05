---
tags:
  - CSE
  - Synopsys
backlink: "[[DSA 1]]"
---
```table-of-contents
```
### 1. Arrays
Arrays are contiguous blocks of memory with fixed size that store homogeneous data, indexed with integers. Each element is located at a deterministic memory offset from a base address, contiguous block. 

Arrays are cache friendly due to spatial locality. 

##### 1.1 Types of Arrays:
1. **Static Arrays:** Fixed Size of allocation, static memory, performance is critical. 
2. **Dynamic Arrays:** Resizable, backed by static arrays
3. **Multi-dimensional Array**: Arrays of Arrays
4. **Sparse Arrays:** Most of the values are 0’s.
5. **Circular Arrays:** Logical wrap-around indexing. 
6. **Jagged Arrays:** Arrays of arrays of varying lengths


##### 1.2 Array Operations:

| Operation         | Complexity     | Space         | Edge Case       |
| ----------------- | -------------- | ------------- | --------------- |
| Access            | O(1)           | O(1)          | Out-of-Bounds   |
| Append            | O(1) amortized | O(n) (resize) | Resize Trigger  |
| Insert (middle)   | O(n)           | O(1)          | Overflow        |
| Delete (middle)   | O(n)           | O(1)          | Invalid Index   |
| Search (unsorted) | O(n)           | O(1)          | Duplicates      |
| Search (sorted)   | O(log n)       | O(1)          | Requires Sorted |
| Resize            | O(n)           | O(n)          | Memory Failure  |
| Traversal         | O(n)           | O(1)          | Empty Array     |

##### 1.3 Pros and Cons:
**Advantages:** O(1) access, Cache Efficient, Simple Implementation, Support Binary Search
**Disadvantages:** Costly Insertions, Memory waste due to over allocation, Requires Contiguous Memory.

##### 1.4 Applications:
- Buffers and Page Tables in OS: Page Tables in OS map virtual addresses to physical addresses. Buffers are temporary storage for data transfer, file read buffer, network buffer. 
- Columnar storage in DBMS
- Packet Buffers in Networking
- Pixel buffers in Graphics
- Symbol tables, intermediate representations in Compilers: Maps variable names to metadata. Symbol tables: Often implemented using Hash Tables (which internally use arrays)
- Tensors in Machine Learning

##### 1.5 

---

### 2. Stacks:
A stack is a linear, contiguous data structure that supports insertion and deletion operations at one end only, called the top, following the Last-In-First-Out (LIFO) principle.

It maintains the number of elements in the stack, a point at the top. Every push increments the pointer, every pop decrements it.

**Stacks are implicit in recursion: Function Call stack, Each Recursive Call → push frame, Return → Pop Frame**


##### 2.1 Types of Arrays:
- **Array based:** Fixed Size, Contiguous Memory, Fast-Access, Cache Friendly
- **Linked List based:** Dynamic Size, Pointer-based, Slower
- **Dynamic Array Stack:** Amortized O(1), Resizable
- **Specialized:** Min Stack (track min.), Max Stack (track max.), Persistent Stack (functional programming)

##### 2.2 Operations:
| Operation | Description   | Internal Steps               | Time (Best/Avg/Worst) | Space | Edge Cases |
| --------- | ------------- | ---------------------------- | --------------------- | ----- | ---------- |
| Push      | Insert at top | increment top → assign value | O(1)                  | O(1)  | Overflow   |
| Pop       | Remove top    | read value → decrement top   | O(1)                  | O(1)  | Underflow  |
| Peek      | Return top    | access array[top]            | O(1)                  | O(1)  | Empty      |
| isEmpty   | Check empty   | top == -1                    | O(1)                  | O(1)  | —          |
| isFull    | Check full    | top == capacity-1            | O(1)                  | O(1)  | —          |
##### 2.3. Applications:
- Call stack in OS/runtime
- Expression evaluation (compilers)
- Undo/Redo systems
- Backtracking (DFS, maze solving

##### 2.4 Pros and Cons
**Advantages:** Simple, Fast Operations, Natural Recursion Model
**Disadvantages:** Limited Access, Overflow in fixed size

##### 2.5 Cache
| Structure      | Cache Efficiency |
| -------------- | ---------------- |
| Array Stack    | High             |
| Linked Stack   | Low              |

---

### 3. Queues:
A queue is a linear, contiguous data structure that supports insertion at one end (rear) and deletion at another (front), following First-In-First-Out (FIFO).

It maintains 2 pointers: head and tail. 

#### 3.1 Types of Queues:
- **Simple Queue:** Inefficient due to unused space
- **Circular Queue:** Wrap around using modulo, Efficient Memory utilization
- **Dequeue:** Insert/Delete from both ends
- **Priority:** Ordered by priority and not insertion time
- **Blocking**: Concurrent Queue, thread-safe, used in produced-consumer

##### 3.2 When to use what?
| Structure      | Use Case                         |
| -------------- | -------------------------------- |
| Stack          | Recursion, parsing, undo systems |
| Queue          | Scheduling, buffering            |
| Deque          | Sliding window problems          |
| Circular Queue | Fixed memory buffers             |
| Priority Queue | Task scheduling                  |
##### 3.3 Operations:
| Operation | Description       | Internal Steps      | Time (Best/Avg/Worst) | Space              | Edge Cases |
| --------- | ----------------- | ------------------- | --------------------- | ------------------ | ---------- |
| Enqueue   | Insert at rear    | rear++ → assign     | O(1)                  | O(1)               | Overflow   |
| Dequeue   | Remove from front | read → front++      | O(1)                  | O(1)               | Underflow  |
| Peek      | View front        | return array[front] | O(1)                  | O(1)               | Empty      |
| isEmpty   | front == rear     | O(1)                | O(1)                  | —                  |            |
| isFull    | depends on type   | O(1)                | O(1)                  | Circular condition |            |

##### 3.4 Applications
- Task scheduling (OS schedulers)
- Network buffers
- Message queues (Kafka, RabbitMQ)
- BFS traversal in graphs

##### 3.5 Pros and Cons
**Advantages:** Fair Ordering, Useful for streaming
**Disadvantages:** More complex, inefficient if not circular

##### 3.6 Cache
| Structure      | Cache Efficiency |
| -------------- | ---------------- |
| Circular Queue | High             |
| Linked Queue   | Low              |

---

