# A-STAR-SEARCH

# ExpNo 4 : Implement A* Search Algorithm for a Graph

### Name: VENKATESAN R

### Register Number: 212224230299

## Aim

To implement A* Search Algorithm for a Graph using Python 3.
## Algorithm

```text
// A* Search Algorithm

1. Initialize the open list.

2. Initialize the closed list.
   Put the starting node on the open list
   (you can leave its f at zero).

3. While the open list is not empty:

   a) Find the node with the least f on
      the open list, call it "q".

   b) Pop q off the open list.

   c) Generate q's 8 successors and set their
      parents to q.

   d) For each successor:

      i) If successor is the goal, stop search.

      ii) Else, compute both g and h for successor.

          successor.g = q.g + distance between
                        successor and q

          successor.h = distance from goal to
                        successor

          (This can be done using many ways,
          such as Manhattan, Diagonal, and
          Euclidean heuristics.)

          successor.f = successor.g + successor.h

      iii) If a node with the same position as
           successor is in the OPEN list which
           has a lower f than successor,
           skip this successor.

      iv) If a node with the same position as
          successor is in the CLOSED list which
          has a lower f than successor,
          skip this successor.

          Otherwise, add the node to the
          OPEN list.

   e) Push q onto the CLOSED list.

4. Repeat until the goal is found or the
   OPEN list becomes empty.
```
---
## PROGRAM:
```python
import heapq

def a_star(graph, heuristic, start, goal):
    open_list = []
    heapq.heappush(open_list, (heuristic[start], 0, start, [start]))

    visited = {}

    while open_list:
        f, g, current, path = heapq.heappop(open_list)

        if current == goal:
            return path

        if current in visited and visited[current] <= g:
            continue

        visited[current] = g

        for neighbor, cost in graph[current]:
            new_g = g + cost
            new_f = new_g + heuristic[neighbor]
            heapq.heappush(open_list, (new_f, new_g, neighbor, path + [neighbor]))

    return None


# Input
n, e = map(int, input().split())

graph = {}

for _ in range(e):
    u, v, w = input().split()
    w = int(w)

    if u not in graph:
        graph[u] = []
    if v not in graph:
        graph[v] = []

    graph[u].append((v, w))
    graph[v].append((u, w))  # Undirected graph

heuristic = {}

for _ in range(n):
    node, h = input().split()
    heuristic[node] = int(h)

start = input("Enter Start Node: ").strip()
goal = input("Enter Goal Node: ").strip()

path = a_star(graph, heuristic, start, goal)

if path:
    print("Path found:", path)
else:
    print("No path found")

```
## Sample Graph I

![Sample Graph I](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/b1377c3f-011a-4c0f-a843-516842ae056a)

## Sample Input

<img width="692" height="667" alt="image" src="https://github.com/user-attachments/assets/0a9fc2ad-f4de-4c32-8c84-173c2470a17d" />



## OUTPUT:

<img width="621" height="90" alt="image" src="https://github.com/user-attachments/assets/92a828ea-218b-4acf-a17f-9a70fa111d76" />


## Sample Graph II

![Sample Graph II](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/acbb09cb-ed39-48e5-a59b-2f8d61b978a3)

## Sample Input

<img width="691" height="355" alt="image" src="https://github.com/user-attachments/assets/5cc58661-6c8a-4e44-b554-0531b76aef28" />


## Sample Output

<img width="637" height="87" alt="image" src="https://github.com/user-attachments/assets/f8c22726-9294-457a-b2b1-6661a65a26b5" />

# RESULT:
Thus, a python program to implement A* search algorithm for a graph has been written and executed successfully.



