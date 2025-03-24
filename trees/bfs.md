# Breadth First Search (BFS)

Breadth First Search (BFS) is a graph traversal algorithm that starts from the root node
and explores all the nodes at the current depth level before moving to the nodes at the next depth level.

```py
def bfs(root):
  queue = [root]
  while queue is not empty:
    node = queue.pop(0)
    print(node)
    if node.left is not null:
      queue.append(node.left)
    if node.right is not null:
      queue.append(node.right)
```
