# Binary Search Tree Build, Search, Insert, Delete

BST Abstract Data Type (Pseudo-code):

```py
class Node:
  attribute value
  attribute left
  attribute right

interface BST:
  method buildBST(arr)
  method insertNode(value)
  method searchNode(value)
  method deleteNode(value)
```

## Binary Search Tree Build

Build BST from array (unbalanced BST)

```py
method buildBST(arr):
  if len(arr) == 0: return null
  root = Node(arr[0])
  for value in arr[1:]:
    insertNode(root, value)
  return root
```

## Binary Search Tree Insert

```py
method insertNode(root, value):
  newNode = Node(value)
  curr = root, prev = null

  while curr is not null:               # find correct insertion point
    if newNode.value == curr.value:     # value already exists
      return curr
    if newNode.value < curr.value:      # move left
      prev = curr
      curr = curr.left
    else:                               # move right
      prev = curr
      curr = curr.right

  newNode.value < prev.value ? prev.left = newNode : prev.right = newNode
```

## Binary Search Tree Search

```py
method searchNode(root, value):
  current = root

  while current is not null:
    if value == current.value:
      return current
    if value < current.value:
      current = current.left
    else:
      current = current.right

  return null
```

## Binary Search Tree Delete

Before implementing delete node function, we need to understand couple of edge cases:

- a node can have 0, 1, or 2 children
- case1: if node has 0 children, make node null
- case2: if node has 1 child, replace node with child
- case3: if node has 2 children:
  - find minimum node in right subtree (successor)
  - replace node with minimum node
  - delete minimum node

### BST Minimum and Maximum

Below BST conditions can be used to find minimum and maximum nodes:

- minimum node is leftmost node
- maximum node is rightmost node

```py
method findMin(root):
  current = root

  while current.left is not null:
    current = current.left

  return current

method findMax(root):
  current = root

  while current.right is not null:
    current = current.right

  return current
```

### BST successor and predecessor

Successor of a node is the next _largest_ node in the BST.

- if node has right subtree, find minimum node in right subtree
- if node does not have right subtree, find first parent where target node is in a left subtree

```py
# target node has right subtree
              (5)  <- target node
              / \
            (2) (8)
                / \
successor ->  (6) (9)

# target node is direct child of ancestor
                    (5)
                    / \
  successor ->    (2) (8)
                  /
target node ->  (1)

# target node is not direct child of ancestor but is in a left subtree
     (9)   <- successor
    /
  (4)
    \
     (5)
       \
        (8) <- target node
```

Successor pseudo-code:

```py
method findSuccessor(root, node):
  # if node has right subtree, find minimum node in right subtree
  if node.right is not null:
    return findMin(node.right)

  # if node does not have right subtree, find first parent where node is in a left subtree
  ancestor = null
  curr = root
  while curr.value is not node.value:
    if node.value < curr.value:
      ancestor = curr
      curr = curr.left
    else:
      curr = curr.right
  return ancestor
```

Predecessor of a node is the next _smallest_ node in the BST.

- if node has left subtree, find maximum node in left subtree
- if node does not have left subtree, find first ancestor of node that is a right child

```py
# target node has left subtree
                    (5)
                    / \
  predecessor ->  (4) (8)
                  /
target node ->  (2)

# target node does not have left subtree, but is a direct right child of ancestor
  (4)
  / \
(2)  (5)    <- predecessor
       \
        (8) <- target node

# target node does not have left subtree, but is not a direct right child of ancestor
  (5)   <- predecessor
     \
      (8)
     /
   (7)
  /
(6) <- target node
```

Predecessor pseudo-code:

```py
method findPredecessor(root, node):
  # if node has left subtree, find maximum node in left subtree
  if node.left is not null:
    return findMax(node.left)

  # if node does not have left subtree, find first ancestor of node that is a right child
  ancestor = null
  curr = root
  while curr.value is not node.value:
    if node.value < curr.value:
      curr = curr.left
    else:
      ancestor = curr
      curr = curr.right
  return ancestor
```

### Delete Node

```py
method deleteNode(root, value):
  if root is null: return null
  curr = root, prev = null
  # find node and its parent
  while curr.value is not value and curr is not null:
    prev = curr
    if value < curr.value:
      curr = curr.left
    else:
      curr = curr.right

  if curr is null:
    return root        # node not found

  # case1: if node has 0 children, make node null
  if curr.left is null and curr.right is null:
    if curr is prev.left:
      prev.left = null
    else:
      prev.right = null

  # case2: if node has 1 child, replace node with child
  else if curr.left is not null:
    if curr is prev.left:
      prev.left = curr.left
    else:
      prev.right = curr.left
  else:
    if curr is prev.left:
      prev.left = curr.right
    else:
      prev.right = curr.right

  # case3: if node has 2 children:
  else if curr.left is not null and curr.right is not null:
    successor = findMin(curr.right)
    curr.value = successor.value
    deleteNode(curr.right, successor.value)
  return root
```
