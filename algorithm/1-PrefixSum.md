# Prefix Sum

### Definition
```
Prefix sums are trivial to compute in sequential models of computation, 
by using the formula y[i] = y[i − 1] + x[i] to compute each output value in sequence order.
```

<hr>

### Problem (Array)

Given an array `A` and `q` queries.
Calculate `query(i,j) = A[i] + A[i+1] + ... + A[j]`.

#### - Solution
```
Prefix sum from index 0 to index i is sum of all element from index 0 to index i 
or equal to sum of prefix[i-1] and A[i]:
    prefix[i] = A[0] + A[1] + ... + A[i] = prefix[i-1] + A[i]

=> Prefix sum from index i to index j equal prefix[j] - prefix[i-1]
    query(i,j) = prefix[j] - prefix[i-1]

Edge case: i == 0 => query(i,j) = prefix[j]
```
#### - Setup
```c++
vector<int> buildPrefixSum(vector<int>& a) {
    int n = a.size();
    vector<int> prefixSum(n + 1, 0);

    for (int i = 0; i < n; i++)
        prefixSum[i + 1] = prefixSum[i] + a[i];

    return prefixSum;
}
```
<hr>

### Problem (Matrix)

Given a matrix `A` of size nxm.
Function: `int sumRegion(int row1, int col1, int row2, int col2)`.

Returns the sum of the elements of matrix inside the rectangle
defined by its upper left corner `(row1, col1)` and lower right corner `(row2, col2)`.

#### - Solution
```
Sum(i+1,j+1) = sum all number in rectangle (0,0,i,j)
Query(u,v,i,j) = Sum(i+1,j+1) - Sum(u,j+1) - Sum(u+1, j) + Sum(u,v)
Sum[i][j] = Sum[i-1][j] + Sum[i][j-1] - Sum[i-1][j-1] + A[i-1][j-1]
```
#### - Setup
```c++
vector<vector<int>> buildPrefixSum(vector<vector<int>> matrix) {
    int n = matrix.size(),
        m = matrix[0].size();
    
    vector<vector<int>> prefixMatrix (n+1, vector<int> (m+1, 0));
    
    for (int i = 0; i < n; ++i) 
        for (int j = 0; j < m; ++j) 
            prefixMatrix[i+1][j+1] = prefixMatrix[i][j+1] + prefixMatrix[i+1][j] + matrix[i][j];

    return prefixMatrix;
}
```
<hr>

### Problem (XOR)

Give an array `arr` of positive integers and array `queries` where `queries[i] = [left, right]`.

For each query `i` compute the **XOR** of elements from `left` to `right` (that is, `arr[left] XOR arr[left + 1] XOR ... XOR arr[right]`).

Return an array `answer` where `answer[i]` is the answer to the `ith` query.

**Notice:**
- `x^x = 0`
- `x^0 = x`

#### - Solution
```
Prefix XOR from index 0 to index i is XOR of all element from index 0 to index i 
or equal to XOR of prefix[i-1] and A[i]:
    prefix[i] = A[0] ^ A[1] ^ ... ^ A[i] = prefix[i-1] ^ A[i]

=> Prefix XOR from index i to index j equal is:
    query(left, right) = prefix[right] ^ prefix[left] ^ A[left] = prefix[right] ^ prefix[left-1]

Edge case: left == 0 => query(left,right) = prefix[right]
```

#### - Setup
```c++
vector<int> xorQueries(vector<int>& arr, vector<vector<int>>& queries) {
     vector<int> ans;
    
    for(int i = 1; i < arr.size(); i++) 
        arr[i] = arr[i] ^ arr[i-1];
    
    for(int i = 0; i < queries.size(); i++) {
        int left = queries[i][0];
        int right = queries[i][1];
        
        if (left == 0) 
            ans.push_back(arr[right]);
        else 
            ans.push_back(arr[right] ^ arr[start-1]);
    }
    
    return ans;
}
```