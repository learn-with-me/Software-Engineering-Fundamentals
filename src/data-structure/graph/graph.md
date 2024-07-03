### Understanding Graphs

A graph is a collection of nodes (also called vertices) and edges that connect pairs of nodes. Graphs can be:
- **Directed or Undirected:** In a directed graph, edges have a direction, while in an undirected graph, edges do not.
- **Weighted or Unweighted:** In a weighted graph, edges have weights or costs associated with them. In an unweighted graph, all edges are considered equal.
- **Sparse or Dense:** A sparse graph has relatively few edges compared to the number of nodes, while a dense graph has many edges.

Graphs are used to represent various real-world systems such as social networks, transportation networks, and communication networks.

### Java Implementation of a Graph

Here’s a simple implementation of a graph in Java using an adjacency list representation.

#### Graph Class

```java
import java.util.*;

class Graph {
    private int numVertices;
    private LinkedList<Integer>[] adjLists;

    // Constructor
    public Graph(int vertices) {
        numVertices = vertices;
        adjLists = new LinkedList[vertices];
        for (int i = 0; i < vertices; i++) {
            adjLists[i] = new LinkedList<>();
        }
    }

    // Add edge
    public void addEdge(int src, int dest) {
        adjLists[src].add(dest);
        adjLists[dest].add(src); // For undirected graph, add both connections
    }

    // Print the graph
    public void printGraph() {
        for (int i = 0; i < numVertices; i++) {
            System.out.print("Vertex " + i + ":");
            for (Integer node : adjLists[i]) {
                System.out.print(" -> " + node);
            }
            System.out.println();
        }
    }

    // Depth First Search (DFS) traversal
    public void DFS(int vertex) {
        boolean[] visited = new boolean[numVertices];
        DFSUtil(vertex, visited);
    }

    private void DFSUtil(int vertex, boolean[] visited) {
        visited[vertex] = true;
        System.out.print(vertex + " ");

        for (int adj : adjLists[vertex]) {
            if (!visited[adj]) {
                DFSUtil(adj, visited);
            }
        }
    }

    // Breadth First Search (BFS) traversal
    public void BFS(int startVertex) {
        boolean[] visited = new boolean[numVertices];
        LinkedList<Integer> queue = new LinkedList<>();

        visited[startVertex] = true;
        queue.add(startVertex);

        while (queue.size() != 0) {
            int vertex = queue.poll();
            System.out.print(vertex + " ");

            for (int adj : adjLists[vertex]) {
                if (!visited[adj]) {
                    visited[adj] = true;
                    queue.add(adj);
                }
            }
        }
    }

    public static void main(String[] args) {
        Graph graph = new Graph(5);

        graph.addEdge(0, 1);
        graph.addEdge(0, 4);
        graph.addEdge(1, 2);
        graph.addEdge(1, 3);
        graph.addEdge(1, 4);
        graph.addEdge(2, 3);
        graph.addEdge(3, 4);

        graph.printGraph();

        System.out.println("Depth First Search starting from vertex 0:");
        graph.DFS(0);

        System.out.println("\nBreadth First Search starting from vertex 0:");
        graph.BFS(0);
    }
}
```

### Explanation

**Graph Class:**

```java
class Graph {
    private int numVertices;
    private LinkedList<Integer>[] adjLists;

    // Constructor
    public Graph(int vertices) {
        numVertices = vertices;
        adjLists = new LinkedList[vertices];
        for (int i = 0; i < vertices; i++) {
            adjLists[i] = new LinkedList<>();
        }
    }
}
```

The `Graph` class represents a graph with a specified number of vertices. The adjacency list is used to store the graph, with each vertex having a linked list of its adjacent vertices.

**Add Edge Function:**

```java
public void addEdge(int src, int dest) {
    adjLists[src].add(dest);
    adjLists[dest].add(src); // For undirected graph, add both connections
}
```

This function adds an edge between two vertices in the graph. For an undirected graph, edges are added in both directions.

**Print Graph Function:**

```java
public void printGraph() {
    for (int i = 0; i < numVertices; i++) {
        System.out.print("Vertex " + i + ":");
        for (Integer node : adjLists[i]) {
            System.out.print(" -> " + node);
        }
        System.out.println();
    }
}
```

This function prints the graph's adjacency list representation.

**Depth First Search (DFS) Function:**

```java
public void DFS(int vertex) {
    boolean[] visited = new boolean[numVertices];
    DFSUtil(vertex, visited);
}

private void DFSUtil(int vertex, boolean[] visited) {
    visited[vertex] = true;
    System.out.print(vertex + " ");

    for (int adj : adjLists[vertex]) {
        if (!visited[adj]) {
            DFSUtil(adj, visited);
        }
    }
}
```

The DFS function recursively traverses the graph starting from a given vertex. It uses a boolean array to keep track of visited vertices.

**Breadth First Search (BFS) Function:**

```java
public void BFS(int startVertex) {
    boolean[] visited = new boolean[numVertices];
    LinkedList<Integer> queue = new LinkedList<>();

    visited[startVertex] = true;
    queue.add(startVertex);

    while (queue.size() != 0) {
        int vertex = queue.poll();
        System.out.print(vertex + " ");

        for (int adj : adjLists[vertex]) {
            if (!visited[adj]) {
                visited[adj] = true;
                queue.add(adj);
            }
        }
    }
}
```

The BFS function iteratively traverses the graph starting from a given vertex using a queue to manage the traversal.

**Main Method:**

```java
public static void main(String[] args) {
    Graph graph = new Graph(5);

    graph.addEdge(0, 1);
    graph.addEdge(0, 4);
    graph.addEdge(1, 2);
    graph.addEdge(1, 3);
    graph.addEdge(1, 4);
    graph.addEdge(2, 3);
    graph.addEdge(3, 4);

    graph.printGraph();

    System.out.println("Depth First Search starting from vertex 0:");
    graph.DFS(0);

    System.out.println("\nBreadth First Search starting from vertex 0:");
    graph.BFS(0);
}
```

### Conclusion

This example demonstrates how to implement a graph in Java using an adjacency list. The `Graph` class includes methods to add edges, print the graph, and perform both Depth First Search (DFS) and Breadth First Search (BFS) traversals. This basic implementation can be extended to handle more complex operations and types of graphs, such as weighted and directed graphs.
