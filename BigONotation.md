# Big O Notation

### Definition
```
- Big O notation describles the complexity of algorithm as a function of the size of an input
    + performance / runtime complexity
    + space complexity
=> How quickly algorithms will likely run based on the number of inputs passed into it 
```

<hr>

### Complexity growth

| Class       | N = 1 | N = 10 | N = 1000  | N = 1000000   |
|-------------|-------|--------|-----------|---------------|
| O(1)        | 1     | 1      | 1         | 1             |
| O(log(N))   | 1     | 3      | 10        | 20            |
| O(N)        | 1     | 10     | 1000      | 1000000       |
| O(N log(N)) | 1     | 30     | 10000     | 20000000      |
| O(N^2)      | 1     | 100    | 1000000   | 1000000000000 |
| O(2^N)      | 2     | 1024   | 1.07e+301 | ...           |

<hr>

### Compute complexity

#### 1. Instructions and Conditions: O(1)
```c++
void function() {
    cout << "Hello!";
    return 1 == 2;
}
```

#### 2. Loops: O(N)
```c++
/** function run with O(N) time complexity, with N is nums.size() */
void function(vector<int> nums) {
    for (auto n: nums) 
        cout << n;
}
```

#### 3. Nested Loop: O(N * M * ...)
```c++
/** function run with O(N * M) time complexity, with N is maps.size() and M is maps[i].size() */
void function(vector<vector<int>> maps) {
    for (int i = 0; i < maps.size(); ++i) 
        for (int j = 0; j < maps[i].size(); ++j) 
            cout << maps[i][j];
}
```

#### 4. Recursion: O(K * N)

```
Runtime of recursion algorithm = number of recursion time x runtime of each recursion
```

```c++
/** 
 *  function run with O(K) time complexity recursion
 *  each recursion is O(1) time complexity
 *  O(K * 1) = O(K)
 */
int function(int k) {
    if (k > 0) 
        return k + function(k-1);
    
    return k;
}
```

<hr>

### Complexity compute rule

#### Rule 1: Focus on dominant term

```
Drop constants and multiplicative factors
```
```
- O(n^2 + 2n + 2) = O(n^2)
- O(n^3 + 100000n + 9) = O(n^3)
- O(log(n) + n + 4) = O(n)
```

#### Rule 2: Law of Addition

```
- O(f(n)) + O(g(n)) = O(f(n) + g(n))
- Used with sequential statements
```

```c++
void function(int n) {
    // this one is O(n) runtime complexity
    for (int i = 0; i < n; ++i)
        cout << i;
    
    // this one is O(n^2) runtime complexity
    for (int i = 0; i < n*n; ++i)
        cout << i;
    
    // overall runtime complexity is O(n + n^2), using Rule 1 it became O(n^2)
}
```

#### Rule 3: Law of Multiplication

```
- O(f(n)) * O(g(n)) = O(f(n) * g(n))
- Used with nested statements/loops
```

```c++
void function(int n, int m) {
    /** 
     * outer loop is O(n)
     * nested loop is O(m)
     * runtime complexity O(n) * O(m) = O(n*m)
     */
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) 
            cout << i << j;
}
```