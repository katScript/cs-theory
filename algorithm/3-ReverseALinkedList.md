# Reverse a Linked List

### Problem

Given the `head` of a singly linked list, reverse the list, and return the _reversed list_.
```
Input : head = [1,2,3,4,5]
Output:        [5,4,3,2,1]
```

#### - Solution
```
While traversing the list, change current node’s next to previous node
Use a variable to store the previous node
```

#### - Setup

```c++
ListNode* reverseList(ListNode* head) {
    ListNode* prev = NULL;
    ListNode* cur = head;
    
    while (cur) {
        ListNode* next = cur->next;
        cur->next = prev;
        prev = cur;
        cur = next;
    }
    
    return prev;
}
```