# Dutch flag partition

### Definition

```
This problem can also be viewed in terms of rearranging elements of an array. 
Suppose each of the possible elements could be classified into exactly one of three categories 
- bottom.
- middle.
- top.
```

<hr>

### Problem
Given an array `A` and an index `i`.

Rearranges the elements of A 
such that all elements _less than_ `A[i]` appear first, 
followed by elements _equal to_ `A[i]`, 
followed by elements _greater than_ `A[i]`.

#### - Solution

```
Move all smaller element to the beginning
    - set pivot = A[i]
    - maintain a variable boundary such that A[0], A[1], ..., A[boundary-1] < pivot
    - loop through array A and extend the boundary

Similarly, move all larger elements to the end.
```

#### - Setup
```c++
/** 
 * Space: O(1) extra
 * Time: O(n)
 * */
void dutchFlagPartition(vector<int>& A) Ơ{
    int pivot = A[i];
    int boundary = 0;
    
    for(int i = 0; i < n; i++) 
        if (A[i] < pivot) {
            swap(A[i], A[boundary])
            boundary++;
        }
}
```
