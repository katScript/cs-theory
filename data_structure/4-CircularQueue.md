# Circular Queue

### Definition

!["circular queue"](https://media.geeksforgeeks.org/wp-content/uploads/Circular-queue.png)
```
A Circular Queue is a special version of queue where the last element of the queue 
    is connected to the first element of the queue forming a circle.
    
    - FIFO
    - Last position is connected 
    - to the first position 
    - Benefit: reuse space in front of queue
```

#### Operation

```c++
// sample circular queue object
class MyCircularQueue {
public:
    // Initializes the object with the size of the queue to be k
    MyCircularQueue(int k);
    
    // Inserts an element into the circular queue. Return true if the operation is successful.
    bool enQueue(int value);
    
    // Deletes an element from the circular queue. Return true if the operation is successful.
    bool deQueue();
    
    // Gets the front item from the queue. If the queue is empty, return -1. 
    int Front();
    
    // Gets the last item from the queue. If the queue is empty, return -1.
    int Rear();
    
    // Queue empty or not
    bool isEmpty();
    
    // Queue is full or not
    bool isFull();
};
```

#### Setup

```c++
class MyCircularQueue {
private:
    struct ListNode {
        int val;
        ListNode *next;
        
        ListNode() : val(0), next(nullptr) {}
        ListNode(int x) : val(x), next(nullptr) {}
        ListNode(int x, ListNode *next) : val(x), next(next) {}
    };
    
    int queueLength = 0;
    int currentSize = 0;
    ListNode* queue;
    ListNode* back;
    
public:
    MyCircularQueue(int k) {
        queueLength = k;
    }

    bool enQueue(int value) {
        if(isFull())
            return false;
        
        if (isEmpty()) {
            queue = new ListNode(value);
            back = queue;
        } else {
            ListNode* node = new ListNode(value, nullptr);
            back->next = node;
            back = back->next;
        }

        currentSize++;
        return true;
    }

    bool deQueue() {
        if(isEmpty())
            return false;
        
        ListNode* term = queue;
        queue = queue->next;
        
        delete term;
        currentSize--;
        
        return true;
    }

    int Front() {
        if(isEmpty())
            return -1;
        
        return queue->val;
    }

    int Rear() {
        if(isEmpty())
            return -1;
        
        return back->val;
    }

    bool isEmpty() {
        return currentSize == 0;
    }

    bool isFull() {
        return currentSize == queueLength;
    }
};
```
