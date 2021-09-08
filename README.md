# Srinadh Ponugoti
### Northwest missouri state university

Northwest missouri state university is a **beautiful** campus and having a good **weather**
 
---
Directions from Los Angeles  to  maryville
1. Go to the parking in your homr at los angeles 
2. Start your drive to maryville 
     1. Choose kansas-missouri express highway
     2. Make sure that you have next free left to missouri
     3. After free left you have sign boards of maryville
3. At maryville you will get the northwest missouri.
* Go to the store
* buy a laptop
   * Headset
   * Pendrive
   * Bag
* come to northwest university 

**[To Know about me](AboutMe.md)**

***
### Recomanding to my friend to try some items
 my friend ask me about the local food items and i recomanded some of my favorite to experience him and he has done and feel good of those items and enjoyed the food 

|Items|Location|Cost|
|:---|:---|:---|  
|Cheese rolls|Downtown maryville|23$|
|Bread|St.Jhones|4.34$|
|Chicken nuggets|Kansas|12$|
|Diet coke|Walmart|3.12$|

***
>Life is what happens when you're busy making other plans — *John Lennon*
>
> You only live once, but if you do it right, once is enough — *Mae West*

***
## Depth First Search
>Depth-first search (DFS) is an algorithm for traversing or searching tree or graph data structures. The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking.
>
>A version of depth-first search was investigated in the 19th century by French mathematician Charles Pierre Trémaux as a strategy for solving mazes.
>
>**Properties:**
>
>The time and space analysis of DFS differs according to its application area. In theoretical computer science, DFS is typically used to traverse an entire graph, and takes time {\displaystyle O(|V|+|E|)}O(|V| + |E|), where |V| is the number of vertices and |E| the number of edges. This is linear in the size of the graph. In these applications it also uses space {\displaystyle O(|V|)}O(|V|) in the worst case to store the stack of vertices on the current search path as well as the set of already-visited vertices. Thus, in this setting, the time and space bounds are the same as for breadth-first search and the choice of which of these two algorithms to use depends less on their complexity and more on the different properties of the vertex orderings the two algorithms produce.
>
>For applications of DFS in relation to specific domains, such as searching for solutions in artificial intelligence or web-crawling, the graph to be traversed is often either too large to visit in its entirety or infinite (DFS may suffer from non-termination). In such cases, search is only performed to a limited depth; due to limited resources, such as memory or disk space, one typically does not use data structures to keep track of the set of all previously visited vertices. When search is performed to a limited depth, the time is still linear in terms of the number of expanded vertices and edges (although this number is not the same as the size of the entire graph because some vertices may be searched more than once and others not at all) but the space complexity of this variant of DFS is only proportional to the depth limit, and as a result, is much smaller than the space needed for searching to the same depth using breadth-first search. For such applications, DFS also lends itself much better to heuristic methods for choosing a likely-looking branch. When an appropriate depth limit is not known a priori, iterative deepening depth-first search applies DFS repeatedly with a sequence of increasing limits. In the artificial intelligence mode of analysis, with a branching factor greater than one, iterative deepening increases the running time by only a constant factor over the case in which the correct depth limit is known due to the geometric growth of the number of nodes per level.
>
>DFS may also be used to collect a sample of graph nodes. However, incomplete DFS, similarly to incomplete BFS, is biased towards nodes of high degree.
>
>**Output of a depth-first search:**
>
>A convenient description of a depth-first search of a graph is in terms of a spanning tree of the vertices reached during the search. Based on this spanning tree, the edges of the original graph can be divided into three classes: forward edges, which point from a node of the tree to one of its descendants, back edges, which point from a node to one of its ancestors, and cross edges, which do neither. Sometimes tree edges, edges which belong to the spanning tree itself, are classified separately from forward edges. If the original graph is undirected then all of its edges are tree edges or back edges.

For more Information <https://en.wikipedia.org/wiki/Depth-first_search>

**Classification of edges of a graph**

We can classify the edges using the entry and exit time of the end nodes u and v of the edges (u,v). These classifications are often used for problems like finding bridges and finding articulation points.

We perform a DFS and classify the encountered edges using the following rules:

If v is not visited:

* Tree Edge - If v is visited after u then edge (u,v) is called a tree edge. In other words, if v is visited for the first time and u is currently being visited then (u,v) is called tree edge. These edges form a DFS tree and hence the name tree edges.
If v is visited before u:
* Back edges - If v is an ancestor of u, then the edge (u,v) is a back edge. v is an ancestor exactly if we already entered v, but not exited it yet. Back edges complete a cycle as there is a path from ancestor v to descendant u (in the recursion of DFS) and an edge from descendant u to ancestor v (back edge), thus a cycle is formed. Cycles can be detected using back edges.
* Forward Edges - If v is a descendant of u, then edge (u,v) is a forward edge. In other words, if we already visited and exited v and entry[u]<entry[v] then the edge (u,v) forms a forward edge.
* Cross Edges: if v is neither an ancestor or descendant of u, then edge (u,v) is a cross edge. In other words, if we already visited and exited v and entry[u]>entry[v] then (u,v) is a cross edge.

Note: Forward edges and cross edges only exist in directed graphs.

**Implementation**

```
vector<vector<int>> adj; // graph represented as an adjacency list
int n; // number of vertices

vector<bool> visited;

void dfs(int v) {
    visited[v] = true;
    for (int u : adj[v]) {
        if (!visited[u])
            dfs(u);
    }
}
```
This is the most simple implementation of Depth First Search. As described in the applications it might be useful to also compute the entry and exit times and vertex color. We will color all vertices with the color 0, if we haven't visited them, with the color 1 if we visited them, and with the color 2, if we already exited the vertex.

Here is a generic implementation that additionally computes those:
```
vector<vector<int>> adj; // graph represented as an adjacency list
int n; // number of vertices

vector<int> color;

vector<int> time_in, time_out;
int dfs_timer = 0;

void dfs(int v) {
    time_in[v] = dfs_timer++;
    color[v] = 1;
    for (int u : adj[v])
        if (color[u] == 0)
            dfs(u);
    color[v] = 2;
    time_out[v] = dfs_timer++;
}
```




