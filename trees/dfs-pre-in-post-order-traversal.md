# Depth First Search (Preorder, Inorder, Postorder Traversal)

DFS - is a traversal algorithm that starts from the root node and explores all the nodes at the current depth level before moving to the nodes at the next depth level.

```py
def dfsPreorder(root):
  if root is null: return
  print(root)
  dfsPreorder(root.left)
  dfsPreorder(root.right)

def dfsInorder(root):
  if root is null: return
  dfsInorder(root.left)
  print(root)
  dfsInorder(root.right)

def dfsPostorder(root):
  if root is null: return
  dfsPostorder(root.left)
  dfsPostorder(root.right)
  print(root)
```
