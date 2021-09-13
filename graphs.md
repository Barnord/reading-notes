# Graphs

A graph is a collection of nodes, connected by edges. The nodes in a graph are called vertices.

Common terminolody:
1. Vertex - where the data is
2. Edge - where a connected vertex is
3. Neighbor - where the edges go
4. Degree - how many edges a vertex has

## Directed vs Undirected

### Undirected

Edges contain a reference for both vertices.

### Directed

Edges only go one direction, so a vertex contains an edge, and the edge points to a different vertex that doesn't have any information about this edge.

## Complete vs Connected vs Disconnected

### Complete Graphs

In a complete graph, each vertex has an edge to every other node, without any exceptions.

### Connected Graphs

In a connected graph, each vertex has at least one edge. They don't necessarily have to be connected to each other, for example, you can have two subgraphs that don't connect.

### Disconnected

In a disconnected graph, some vertices may not have edges.

## Acyclic vs Cyclic

### Acyclic

In a cyclical graph, you can iterate through from the first node, all the way back to the first node, hitting every node in the graph, without using the same edge twice.

### Cyclic

A graph of a positive length that starts and ends at the same vertex.

## Graph Representation

### Adjacency Matrix

An adjacency matrix is basically the graph looking form of a graph. It compares every vertex against every vertex with a bool representing if there's an edge to that node or not.

### Adjacency List

A more common way to represent a graph, it's some form of list, containing an entry for each vertex. The entry contains the edges a vertex has.

## Weighted Graphs

When edges have a numerical value associated with them, it becomes a weighted graph.

A weight matrix would be like an adjacency matrix, except the weight of each edge would be listed instead of a bool, with 0 meaning no edge.

In an adjacency list of a weighted table, you include the weight of the edge after the vertex it connects to.

## Traversals

### Breadth First

Same as a tree, except you're going to want a collection to keep track of vertices you've visited before, so you don't get stuck in a cyclical graph.

### Depth First

Steps are as follows:
1. Push root vertex into stack
2. Start loop that iterates while the stack isn't empty
3. Peek the top vertex
4. If the top vertex has unvisited children, mark the top as visited, and push the unvisited children into the stack.
5. Pop nodes without unvisited children.
6. Rinse & repeat.

## Applications of Graphs

1. GPS and Mapping
2. Driving Directions
3. Social Networks
4. Airline Traffic
5. Netflix suggestions

[<==Back](README.md)