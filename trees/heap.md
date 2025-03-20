# Heap

A Tree based data structure.
It is a complete Binary Tree.
It can be only min heap or max heap.

**Min heap** - parent.value <= child.value
**Max heap** - parent.value >= child.value

```py
         (2)
        /   \
      (3)   (4)
      / \   / \
    (5) (8)(7)(9)

         (9)
        /   \
      (8)   (7)
     /  \   /  \
   (5) (2)(3)  (6)
```

## Operations

### Heapify

Process of moving a heap node to it's correct position.

```py
def heapify(arr, n, i):   # max heap example
  # initially root/i as a max node
  max = i

  # children
  l, r = 2 * i +1, 2 * i +2

  # compare parent to children
  if l < n and arr[max] < arr[l]:
    max = l

  if r < n and arr[max] < arr[r]:
    max = r

  # if max value changed then swap
  if max != i:
    arr[i], arr[max] = arr[max], arr[i]

    # Recursively heapify the affected subtree
    heapify(arr, n, max)
```

### Heap insert

```py
def insert(arr, newValue):
  # add to the end (left to right)
  arr.append(newValue)
  i = len(arr) - 1

  # find the parent of a new node
  p = (i - 1) // 2

  # swap while child node is grater than parent
  while arr[i] > arr[p] and p <= 0:
    arr[i], arr[p] = arr[p], arr[i]
    i = p
    p = (i - 1) // 2
```

### Heap deleteMax

```py
def delete_max(arr):
  # swap root with last element
  n = len(arr)
  arr[0], arr[n-1] = arr[n-1], arr[0]

  # delete last element
  arr.remove(n-1)

  # heapify tree
  heapify(arr, n, 0)
```
