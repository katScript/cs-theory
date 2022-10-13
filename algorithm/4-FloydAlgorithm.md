# Floyd Algorithm - Fast and slow pointer

### Definition
```
- Floyd Algorithm is an algorithm for finding shortest paths in a directed weighted graph 
with positive or negative edge weights (but with no negative cycles).
- A single execution of the algorithm will find the lengths (summed weights) 
of shortest paths between all pairs of vertices.
```
<hr>

### Problem (Find middle)

Given the `head` of a singly linked list, return the _middle node_ of the linked list.

If there are two middle nodes, return **the second middle** node.

#### - Solution
```
Use 2 pointers: slow and fast, both initially point at head.
    - Let’s fast pointer move twice as fast.
    - When fast reaches end of the linked list, slow is at the middle.
```

#### - Setup
```c++
ListNode* middleNode(ListNode* head) {
    ListNode* slow = head;
    ListNode* fast = head;

    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
    }
    
    return slow;
}
```
<hr>

### Problem (Detect circle)

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that** `pos` **is not passed as a parameter**.

Return `true` if there is a cycle in the linked list. Otherwise, return `false`.

#### - Solution

```
Use Floyd-algorithm: 2 pointers slow and fast
    If at any point: fast == slow => there is a cycle
    Otherwise: => there is no cycle
    
Explaint:
    If there is no cycle: 
        fast will reach end of linked list => O(n)
    If there is a cycle:
        - At some point of time, both fast and slow will be in the cycle
        - After that, the distance between them will decrease by 1 at a time 
            (because fast move 2 step at a time, slow move 1 step at time)
        - So, let’s say the cycle has len K, 
            after K seconds, fast and slow will be at the same node.
```

#### - Setup

```c++
bool hasCycle(ListNode *head) {
    if (!head || !head->next)
        return false;
    
    ListNode* first = head;
    ListNode* second = head;
    
    while(second && second->next) {
        first = first->next;
        second = second->next->next;
        
        if (first == second) 
            return true;
    }
    
    return false;
}
```


