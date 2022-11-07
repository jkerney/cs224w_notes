## Do:

These questions refer to the following graph:
![Example Graph](/img/Example_Graph.png "Example Graph")

### Define:
Provide definiations of the following:
* Degree - number of edges incident with the node
* Eigenvector Centrality - eigenvector centrality value is equal to the sum of eigenvector centrality of the node's neighbours. This turns out to be an eigenvector of the adjacency matrix.
* Betweenness Centrality - ratio of shortest paths in the graph that include the node over all shortest paths (but exclude shortest paths where the node is an endpoint)
* Closeness Centrality - how close the node is to other vertices in the graph. 1 over the sum of shortest paths to all other nodes
* Clustering Coefficient - ratio of (count of neighbour pairs that have an edge between them) / (count of neighbour pairs)

### Centrality
* The Degree of nodes A, B, and C
  * $d_A = 3, d_B = 1, d_C = 3$
* The Eigenvector Centrality of nodes A, B, C, D, and E. (Use wolphram alpha or numpy to solve the matrix equations)

$$\lambda c = A c$$

$$ \lambda c = {\left\lbrack \matrix{0 & 1 & 1 & 0 & 1 \cr 1 & 0 & 0 & 0 & 0 \cr 1 & 0 & 0 & 1 & 1 \cr 0 & 0 & 1 & 0 & 1 \cr 1 & 0 & 1 & 1 & 0} \right\rbrack} c$$

Use wolfram alpha to find the eigenvector of A with the largest eigenvalue:

```
eigenvectors {{1, 1, 1, 0 , 1}, {1,1,0,0,0},{1,0,0,1,1}, {0,0,1,1,1},{1,0,1,1,1}}
v_1≈(0.892316, 0.371337, 0.772881, 0.737784, 1)
λ_1≈3.40298
```

* The Betweenness Centrality of node E

$$c_E = {\text{number shortest paths (where endpoint is not E) that pass through vertex E} \over \text{number of shortest paths (where endpoint is not E )}}$$

Find all shortest paths between the pairs of vertices in {A, B, C , D} - (A,B), (A,C), (A,D), (B,C), (B,D), (C,D)

| Vertex pair | total shortest paths | shortest paths that include E |
| ---- | ----| ---- |
| AB| 1| 0|
| AC | 1| 0|
| AD| 2| 1|
| BC | 1| 0|
| BD| 2| 1|
| CD | 1 | 0|

$$c_E = { 2 \over 8} = {1 \over 4}$$

* The Closeness Centrality of nodes B and C

$$ c_B = {1 \over (1 + 2 +3 + 2)} = {1 \over 8}$$

$$ c_C = {1 \over (1 + 2 + 1 + 1)} = {1 \over 5}$$

### Clustering
* The Clustering Coefficient of node E
* Graphlet Degree Vector of node C for Graphlets of Degree 2 or 3

Graphlets of Degree 3:

![Example Graph](/img/Graphlets_Deg_3.PNG "Example Graphlets")

## Code
[Colab 1](https://colab.research.google.com/drive/1p2s0on6nibUYhJnONBWEAwpBlue37Tcc?usp=sharing)

### Questions
* For closeness centrality - what do you do for nodes you can't reach?
