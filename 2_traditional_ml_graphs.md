
* Review of ML on graphs
  * Node, Edge and Graph level prediction
  * Need to design and obtain features for nodes, edges, graph
  * Train and then apply model

* Node level features
  * node degree - number of edges incident with the node
  * centrality - problem with degree is it doesn't consider the important of neighbouring nodes. Centrality takes this into account.
    * eigenvector - define importance of node based on importance of neighbouring nodes. Definition is recursive. The definition of eigenvector importance can be written using linear algebra, with the vector of eigenvector centrality values as an eigenvector of a matrix A where $a_{ij}$ is 1 if node i is incident with node j, and 0 otherwise 
