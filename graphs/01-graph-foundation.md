# Graph theory foundation

A graph is a collection of nodes and edges.

**Real world example**: Map of states as Nodes/Vertices and Roads as Edges

![State Map Graph](../assets/state_map_graph.drawio.png 'State Map Graph')

```py
# visual representation
       (A)
      /   \              # edges
   (B)    (C)--(E)       # nodes/vertices
      \   /     |
       (D)-----(F)

# non-cyclic graph
       (A)
      /   \
   (B)    (C)
      \
       (D)

# cyclic graph
      (A)
     /   \
   (B)---(C)

# unconnected graph
      (A)
     /   \
   (B)   (C)     (D)-(E)
```

## Eulerian Cycle and Path

```py
# Eulerian Path - a path that passes through every edge exactly once
start-> (A)-(D)
         | \ |
        (B)-(C) <-end
# *tip: if graph has only 2 odd degree vertices => Eulerian Path

# Eulerian Cycle - a cycle that passes through every edge exactly once and returns to the starting node
    (A)-(D)
     |   |
    (B)-(C)
# *tip: if all vertex degree is even => Eulerian Cycle
```
