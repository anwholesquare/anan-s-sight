---
title: "Popular algorithm and passings for single source shortest path"
datePublished: Fri Sep 01 2023 23:04:02 GMT+0000 (Coordinated Universal Time)
cuid: clm17c1lw000708mk0swr9r8y
slug: single-source-shortest-path
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693609373392/22d2ba1d-0db4-4d05-80b1-6966b238fc6c.png
tags: cpp, algorithms, dijkstra, shortestpath, single-source-shortest-path

---

Three commonly used methods for determining the shortest path from a single starting node require a fundamental understanding of graphs. These algorithms are as follows:

1. Shortest path in a Directed Acyclic Graph (DAG) using topological sorting
    
2. The Dijkstra algorithm
    
3. The Bellman-Ford algorithm
    

### **Relax Function (Edge Relaxation): (IMPORTANT)**

In graph algorithms, particularly shortest path algorithms like Dijkstra's and the Bellman-Ford algorithm, the "Relaxation" process, also known as "Node Relaxation," is a crucial step that helps in finding the shortest paths efficiently.

Relaxation involves optimizing the current known distance to a node by potentially replacing it with a shorter distance. The process compares the distance of a potential path through a neighboring node to the currently known shortest path to the destination node. If the potential path is indeed shorter, the distance of the destination node is updated, and this action is referred to as "relaxing" the edge or the node.

Consider a graph where you are trying to find the shortest distance from a source node to other nodes. During relaxation, if you find a path that is shorter than the currently known path, you update the distance of the destination node with this shorter distance. This process iterates through all the nodes in the graph, ensuring that the distances are accurately updated based on the shortest paths discovered so far.  
Algorithm:

```cpp
relax(i,j,distance[], weight[][]):
if distance[i] + weight[i][j] < distance[j]:
   distance [j] = distance[i] + weight[i][j]
   predecessor [j] = i
end if
```

1. ### Shortest path in a DAG using topological sorting
    

When dealing with a Directed Acyclic Graph (DAG), a graph without any cycles, we can find the shortest path from a single source node to all other nodes using a combination of topological sorting and edge relaxation. The key insight is that we process nodes in topological order, calculating the shortest distance to each node based on the distances to its incoming neighbors.

```cpp
0. single_source_shortest_path_dag (source, topolist, weight, adj):
1. for each vertex i in topolist:
2.     distance [i] = INFINITY
3.     predecessor [i] = NULL
4. end for
5. distance[source] = 0
6. for each vertex i in topolist:
7.     for each adjacent vertex j in adj[i]:
8.         relax(i,j,distance,weight)
9.     end for
10. end for
// Now using the distance and predecessor 
// we can measure distance from the single source 
// and track the path from source to destination
```

To make a graph topologically sorted, we have used below algorithm:

```cpp
0. toposort(u):
1. visited[u] = true
2. for all the adjacency vertex i of adj[u]:
3.     if visited [i] is not true
4.         toposort(i)
5.     end if
6. end for
5. insert u in a linkedlist 'topolist' from front
```

Example:  
The source node is ***r*** and explores all shortest paths from the source node. Show the tabular passing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693433816600/99c170a3-20ab-441a-86ad-740e9e3312a3.png align="center")

Answer: Tabular passing is given below in the chart,  
where distance/pi = cost to reach the node from source node/predecessor's node

| nodes | r | s | t | x | y | z |
| --- | --- | --- | --- | --- | --- | --- |
| initial | 0/r | INF/NIL | INF/NIL | INF/NIL | INF/NIL | INF/NIL |
| r | 0/r | 5/r | 3/r | INF/NIL | INF/NIL | INF/NIL |
| s | 0/r | 5/r | 3/r | 11/s | INF/NIL | INF/NIL |
| t | 0/r | 5/r | 3/r | 10/t | 7/t | 5/t |
| x | 0/r | 5/r | 3/r | 10/t | 7/t | 5/t |
| y | 0/r | 5/r | 3/r | 10/t | 7/t | 5/t |
| z | 0/r | 5/r | 3/r | 10/t | 7/t | 5/t |

Now, we need to find paths from the source node to other nodes:

***r to s:*** 5 (r -&gt; s)  
***r to t:*** 3 (r -&gt; t)  
***r to x:*** 10 (r -&gt; t -&gt; x)  
***r to y:*** 7 (r -&gt; t -&gt; y)  
***r to z:*** 5 (r -&gt; t -&gt; z)

1. ### Dijkstra Algorithm
    

Dijkstra is useful for cyclic non-negative edge graphs where we must find all the shortest paths from a single source node. The algorithm maintains a set of explored nodes and continually updates the shortest distance from the source node to each node in the graph.

Here's the step-by-step description of Dijkstra's algorithm:

**Input:**

* `graph`: The graph is represented as an adjacency list or matrix.
    
* `source`: The starting node from which to find the shortest paths.
    

**Output:**

* An array `distances` where `distances[i]` represents the shortest distance from the source node to the node `i`.
    
* An array `prev` where `prev[i]` represents the previous node on the shortest path from the source node to the node `i`.
    
* Note: To reconstruct the shortest paths themselves, you can use the `prev` array.
    

**Algorithm:**

1. Initialize an array `distances` with the shortest distance from the source node to each node. Set `distances[source]` to 0 and all other distances to infinity.
    
2. Initialize a priority queue or a min-heap `pq` to store nodes and their tentative distances. Add the source node with a distance of 0 to `pq`.
    
3. Initialize an array `prev` to store the previous node on the shortest path for each node.
    
4. While `pq` is not empty: a. Extract the node `u` with the smallest distance from `pq`. b. For each neighbor `v` of `u`:
    
    * Calculate a tentative distance `new_distance` from the source to `v` through `u`. It is the sum of the distance from the source to `u` and the weight of the edge from `u` to `v`.
        
    * If `new_distance` is less than the current distance stored in `distances[v]`, update `distances[v]` with `new_distance` and set `prev[v]` to `u`.
        
    * Add node `v` to `pq` with its updated distance.
        
5. Once the algorithm finishes, the `distances` array will contain the shortest distances from the source node to all other nodes and the `prev` array will allow you to reconstruct the shortest paths.
    

```cpp
dijkstra(source, adj):
    distances.assign(N, INF)
    prev.assign(N, -1)
    distances[source] = 0
    prev[source] = source
    pq.push({distances[source], source})
    while pq is not empty:
        u = pq.top().first
        u.pop()
        for all neighbour node v of adj[u]:
            if (distances[u] + weight[u][v] < distances[v]):
                distances[v] = distances[u] + weight[u][v]
                prev[v] = u
                pq.push({distances[v], v})
            end if
        end for
    end while
```

Example:  
The source node is ***s*** and explores all shortest paths from the source node. Show the tabular passing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693605651502/5b03d96c-62bb-4996-8b6e-9765f7474a6d.png align="center")

Answer: Tabular passing is given below in the chart,  
where distance/pi = cost to reach the node from source node/predecessor's node

| Nodes | s | a | b | c | d |
| --- | --- | --- | --- | --- | --- |
| initial | 0/s | INF/NIL | INF/NIL | INF/NIL | INF/NIL |
| s | 0/s | 10/s | INF/NIL | 5/s | INF/NIL |
| c | 0/s | 8/c | 14/c | 5/s | 7/c |
| d | 0/s | 8/c | 13/d | 5/s | 7/c |
| a | 0/s | 8/c | 9/a | 5/s | 7/c |
| b | 0/s | 8/c | 9/a | 5/s | 7/c |

Now, we need to find paths from the source node to other nodes:

***s to a:*** 8 (s -&gt; c -&gt; a)  
***s to b:*** 9 (s -&gt; c -&gt; a -&gt; b)  
***s to c:*** 5 ( s-&gt; c)  
***s to d:*** 7 (s -&gt; c -&gt; d)

1. ### **Bellman-Ford Algorithm**
    

To be continued..