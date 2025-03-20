# Binary Tree Notes

## Tree Terminology

**Binary Tree** is a hierarchical data structure in which each node has at most two children.

```py
# visual representation
    (A)
    / \
  (B) (C)
  / \
(D) (E)

# array representation
[A, B, C, D, E]

For node at index i:
- its left child is at index 2i+1
- its right child is at index 2i+2
- its parent is at index (i-1)/2
```

**Balanced Binary Tree** is a binary tree in which the difference between the heights of the left and right subtrees is not more than one.

```py
# balanced (height difference <= 1)
     (1)
    /   \
  (2)   (3)
  / \
(4)(5)

# unbalanced (height difference > 1)
         (1)
        /   \
      (2)   (3)
      / \
    (4)(5)
    /
  (6)
```

**Complete Binary Tree** is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible.

```py
     (1)
    /   \
  (2)   (3)
  / \   / \
(4)(5) (6)(7)
```

**Binary Search Tree** is a binary tree where the value of each node is greater than the values in the left subtree and less than the values in the right subtree.

```py
      (5)
    /     \
  (3)     (7)   # 5 > 3 and 5 < 7
  / \     / \
(1) (4) (6) (8) # 3 > 1 and 3 < 4 and 7 > 6 and 7 < 8
```

## Height of a Binary Tree

The height of a binary tree is the number of edges from the root node to the farthest leaf node.
Complete Binary Tree has height = log2(n)

```py
# Asymptotic Analysis:
        (1)            # level 0 | nodes = 1 = 2^0
      /     \
    (2)     (3)        # level 1 | nodes = 2 = 2^1
   /   \   /   \
  (4) (5) (6) (7)      # level 2 | nodes = 4 = 2^2
  ...............      # level i | nodes = 2^i
() () () () () () ()   # level h | nodes = 2^h

# number of nodes equal to sum of all nodes at all levels
n = 2^0 + 2^1 + 2^2 + ... + 2^h-1 + 2^h         # common-ratio = 2

# multiply both sides by common-ratio
2n = 2^1 + 2^2 + 2^3 + ... + 2^h + 2^(h+1)

# subtract second equation from first, cancelled out common elements (2^1, 2^2, 2^3, ..., 2^h-1, 2^h)
2n - n = 2^(h+1) - 1        # 2n-n = n
n = 2^(h+1) - 1

2^(h+1) = n + 1             # add 1 to both sides
h+1 = log2(n+1)             # take log base 2 of both sides, log2(2^(h+1)) = h+1
h = log2(n+1) - 1 = log2(n)
```
