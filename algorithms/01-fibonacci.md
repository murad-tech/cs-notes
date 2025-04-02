# Fibonacci sequence

A series of numbers in which each number is the sum of the two preceding numbers, where the first two numbers are 0 and 1.

`0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...`

## Brute force Algorithm

### Recursive Algorithm

`F(n) = F(n-1) + F(n-2)`

```py
def fib(n):
  if n == 0 and n == 1: return n
  return fib(n-1) + fib(n-2)

# Time: O(2^n)  // exponential
# Space: O(1)   // not including recursive stack
```

![Fibonacci Recursion](../assets/fibonacci.drawio.png 'Fibonacci Recursion')

We can visualize this recursion as a tree, where each node has two children. The leaf nodes are the base cases.  
It won't form perfect triangle because the number of nodes in left side will be from `n` to `1` each node will be decreasing by `1`, and the number of nodes in right side will be from `n` to `0` each node will be increasing by `2`.  
Following worst case we can say that the height of the tree will be `n`.  
Each level will have `2^i` nodes, where `i` is the level number.  
The total number of nodes will be `2^(n+1) - 1` which is `O(2^n)`.

### Iterative Algorithm

```py
def fib(n):
  res = [0, 1]
  for i in range(2, n+1):
    res.append(res[i-1] + res[i-2])
  return res[n]

# Time: O(n)
# Space: O(n)
```

### Optimized Algorithm

```py
def fib(n):
  a, b = 0, 1
  for _ in range(n):
    a, b = b, a + b
  return a

# Time: O(n)
# Space: O(1)
```

> Top-down memoization or Bottom-up tabulation can also be used to solve this problem.
