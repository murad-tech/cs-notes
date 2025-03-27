# Graph representation in code

![State Map Graph](../assets/state_map_graph.drawio.png 'State Map Graph')

```py
# vertices representation as a list, access based on index
vertices = ['NY', 'PA', 'IL', 'TX', 'WA', 'CA']

# vertices representation as a map, access based on key
vertices = {
  "NY": 0,
  "PA": 1,
  "IL": 2,
  "TX": 3,
  "WA": 4,
  "CA": 5
}
```

## Edge List

```py
# edge list based on vertices index
edge_list = [
  (0, 1),
  (1, 0), (1, 2), (1, 3),
  (2, 1), (2, 3), (2, 4),
  (3, 1), (3, 2), (3, 5),
  (4, 2), (4, 5),
  (5, 3), (5, 4)
]
```

## Adjacency List

```py
# adjacency list based on vertices index
adj_list = [
  [1],          # edges of vertex 0
  [0, 2, 3],    # edges of vertex 1
  [1, 3, 4],    # edges of vertex 2
  [1, 2, 5],    # edges of vertex 3
  [2, 5],       # edges of vertex 4
  [3, 4]        # edges of vertex 5
]
```

**Visual example of adjacency list**
| | |
| --- | ---------- |
| NY | PA |
| PA | NY, IL, TX |
| IL | PA, TX, WA |
| TX | PA, IL, CA |
| WA | IL, TX |
| CA | TX, WA |

## Adjacency Matrix

```py
# adjacency matrix based on vertices index (n*n)
adj_matrix = [
  [0, 1, 0, 0, 0, 0],
  [1, 0, 1, 1, 0, 0],
  [0, 1, 0, 1, 1, 0],
  [0, 1, 1, 0, 0, 1],
  [0, 0, 1, 0, 0, 1],
  [0, 0, 0, 1, 1, 0]
]
```

**Visual Table representation of adjacency matrix**

|        | NY  | PA  | IL  | TX  | WA  | CA  |
| ------ | --- | --- | --- | --- | --- | --- |
| **NY** | 0   | 1   | 0   | 0   | 0   | 0   |
| **PA** | 1   | 0   | 1   | 1   | 0   | 0   |
| **IL** | 0   | 1   | 0   | 1   | 1   | 0   |
| **TX** | 0   | 1   | 1   | 0   | 0   | 1   |
| **WA** | 0   | 0   | 1   | 0   | 0   | 1   |
| **CA** | 0   | 0   | 0   | 1   | 1   | 0   |

## Adjacency Map

Best if we have weights (distance, time, etc.)

```py
# adjacency map based on vertices key and distance
adj_map = {
  "NY": {"PA": 310},
  "PA": {"NY": 310, "IL": 760, "TX": 1440},
  "IL": {"PA": 760, "TX": 920, "WA": 1740},
  "TX": {"PA": 1440, "IL": 920, "CA": 1610},
  "WA": {"IL": 1740, "CA": 680},
  "CA": {"TX": 1610, "WA": 680}
}
```
