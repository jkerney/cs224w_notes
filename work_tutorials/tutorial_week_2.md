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
* The Eigenvector Centrality of nodes A, B, C, D, and E. (Use wolphram alpha or numpy to solve the matrix equations)
* The Betweenness Centrality of node E
* The Closeness Centrality of nodes B and C

### Clustering
* The Clustering Coefficient of node E
* Graphlet Degree Vector of node C for Graphlets of Degree 2 or 3

Graphlets of Degree 3:

![Example Graph](/img/Graphlets_Deg_3.PNG "Example Graphlets")

## Code
[Colab 1](https://colab.research.google.com/drive/1p2s0on6nibUYhJnONBWEAwpBlue37Tcc?usp=sharing)

### Questions
* For closeness centrality - what do you do for nodes you can't reach?
