# Linked List

### Definition

![Linked List](https://codeforwin.org/wp-content/uploads/2015/09/Linked-list-nodes.png)

```
A series of nodes. each node contains 2 parts:
    - information (Data)
    - reference to the next node (Address)
    
Linked List vs Array:
    - cannot random access
    - size can grow or shrink at runtime
    - memory allocation
```
<hr>

### Implementation

```c++
// cpp struct
struct ListNode {
    int val;
    ListNode *next;
    
    ListNode() : val(0), next(nullptr) {}
    ListNode(int x) : val(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : val(x), next(next) {}
};
```

<hr>

### Functions on Linked List

| Function                | Linked List | Array |
|-------------------------|-------------|-------|
| get size                | O(n)        | O(1)  |
| random access           | O(n)        | O(1)  |
| append (store the tail) | O(1)        | O(1)  |
| remove last             | O(1)        | O(1)  |
| reverse                 | O(n)        | O(n)  |
| insert/ delete          | O(1)        | O(n)  |

