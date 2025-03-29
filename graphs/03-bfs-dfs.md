# Traverse a forest with BFS and DFS

```py
        (1) - (3)
         |     |
        (2)   (6)
        / \
      (4) (5)

adjacency_list = {
  1: [2, 3],
  2: [1, 4, 5],
  3: [1, 6],
  4: [2],
  5: [2],
  6: [3]
}
```

## BFS

```py
def bfs(root):
  queue = [root], visited = set()
  visited[root] = True

  while queue:
    node = queue.pop(0)

    for neighbor in adjacency_list[node]:
      if neighbor not in visited:
        queue.append(neighbor)
        visited[neighbor] = True
```

## DFS Stack Implementation

```py
def dfs(root):
  stack = [root], visited = set()
  visited[root] = True

  while stack:
    node = stack.pop()

    for neighbor in adjacency_list[node]:
      if neighbor not in visited:
        stack.append(neighbor)
        visited[neighbor] = True
```

## DFS Recursive Implementation

```py
def dfs(root):
  visited = set()
  visited[root] = True

  def _dfs(node):
    for neighbor in adjacency_list[node]:
      if neighbor not in visited:
        visited[neighbor] = True
        _dfs(neighbor)

  _dfs(root)
```
