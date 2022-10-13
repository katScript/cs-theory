# Bit Manipulation

### Definition
```
Bitwise Operators:
    Is operates on a bit string, a bit array or a binary numeral (considered as a bit string) 
        at the level of its individual bits.
    It is a fast and simple action, basic to the higher-level arithmetic operations 
        and directly supported by the processor.
       
    |=============|==========|
    | AND         |     &    |
    | OR          |     |    |
    | XOR         |     ^    |
    | NOT         |     ~    |
    | Left shift  |    <<    |
    | Right shift |    >>    |
    |=============|==========|
```
<hr>

### Operators

#### 1. AND : &

```
Only true if both input bits are true:

    0 & 0 = 0
    1 & 0 = 0
    0 & 1 = 0
    1 & 1 = 1
```

#### 2. OR : | 

```
True if any input bit is true:

    0 | 0 = 0
    1 | 0 = 1
    0 | 1 = 1
    1 | 1 = 1
```
#### 3. XOR : ^
```
True if one and only one input bit is true:
    
    0 ^ 0 = 0
    1 ^ 0 = 1
    0 ^ 1 = 1
    1 ^ 1 = 0
```
#### 4. NOT : ~
```
Flip the input bit:
    
    ~1 = 0
    ~0 = 1
```

#### 5. Left shift : <<
```
Shift left the binary digits by n, pad 0’s on the right:
    
    00010110 << 3 = 10110000
    
Shift left 1 = multiply by 2:
    
    7 << 1 = 14 or 111 (7) << 1 = 1110 (14)
```

#### 6. Right shift : >>
```
Shift right the binary digits by n, pad 0’s on the left:
    
    00010110 >> 3 = 00000010
```

<hr>

### Problem 

#### 1. GetBit

```c++
/** 
 * get_bit(x, position) = (x >> position) & 1
 * position is counted from right to left, start from 0.
 */
int get_bit(int x, int position) {
    return (x >> position) & 1;
}

/**
 * Example:
 * get_bit(102, 6) = (01100110 >> 6) & 1 = (00000001) & (00000001) = 1
 */
```

#### 2. SetBit

```c++
int set_bit(int x, int position) {
    return x | (1 << position)
}

/**
 * Example:
 * set_bit(22, 5) = 00010110 | (1 << 00000101) = (00010110) | (0010000) = 00110110 = 54
 */
```

#### 3. FlipBit
```c++
int flip_bit(int x, int position) {
    return x ^ (1 << position)
}
```

#### 4. Turn off the right-most bit
```c++
int turnOffRightMostBit(int x) {
    return x & (x - 1);
}
```

#### 5. Check if power of 2
```c++
// any number is power of 2 has only 1 digit 1 in binary form
bool checkIfPowerOf2(int x) {
    return x & (x-1) == 0;
}
```

#### 6. Subset
Given an integer array `nums` of **unique** elements, return _all possible subsets (the power set)_.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.





