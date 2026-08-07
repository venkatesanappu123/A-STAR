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
