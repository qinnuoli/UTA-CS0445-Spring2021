# Week 11 Lecture 1

## Lab 7: Writing the Graph Class

### Data Structure

The Graph class you will write uses uses a 2D array of int as the backing data structure.

### Concepts

A graph may be thought of as a set of nodes (or vertices) and edges.

In a **weighted, directed** graph, the nodes and the edges may carry a label or some information. Often the nodes will carry a label and the edges will carry a value (***weight*** or cost).

In a directed graph an edge has ***direction***. It goes **from** one node **to** another node.

### The Mini World

![weightedgraph1.jpg](Week%2011%20Le%20f9e6b/weightedgraph1.jpg)

### Adjacency Matrix

The **adjacency Matrix** for the above example would thus be:

```
City #         0   1   2   3   4   5   6   7
--------------------------------------------
0 Pendeleton   0   oo  oo  4   oo  oo  oo  8
1 Pensicola    oo  0   oo  5   oo  oo  oo  oo
2 Peoria       oo  oo  0   oo  oo  5   oo  3
3 Phoenix      oo  oo  4   0   oo  10  oo  3
4 Pierre       2   oo  oo  oo  0   oo  oo  oo
5 Pittsburgh   oo  4   oo  oo  oo  0   oo  oo
6 Princeton    oo  oo  oo  oo  oo  2   0   oo
7 Pueblo       oo  oo  oo  oo  3   oo  oo  0

// notice that the weights on the main diagonal line is 0 because the distance from one city to itself is 0
// if infinity means there's no edge existed between two cities
// source is the row, destination is the column

```

### Adjacency List

The adjacency matrix input file (written as adjacency list) for our lab looks like this:

```
8       // number of nodes in the graph
0 1 10  // there is an edge from node 0 to node 1 and the weight of the edge is 10
0 6 2   // (source, dest, weight)
1 2 31
2 1 22
3 5 11
4 0 9
4 1 56
4 3 13
5 2 25
5 6 15
6 1 6
6 7 22
7 0 12
7 5 1
```

From this input file, we will dimension a 8 x 8 matrix and for every triplet (source, dest, weight ) we read in, we will store

```java
G[source][dest] = weight  // where G is some 2D array indexed with [][] braces
```

### **Properties of directed graphs**

For each node in a directed graph, its edges have **direction.** Thus, for a directed graph, we can define the following terms:

- **out-degree** - the number of edges *leaving* the vertex
- **in-degree** - the number of edges *entering* the vertex
- **degree** - the number of edges *entering and leaving* the vertex

In-Degree for Node 4:

Go to the 4th column and look for values greater than 0 (0 represents itself, -1 represents infinity)

Out-Degree for Node 4:

Go to the 4th row and look for values greater than 0

Degree:  in-degree + out-degree

MaxInDegree:

call in-degree on every node

remember the largest degree you saw

return that degree

AND we expect that number could not be largest n-1