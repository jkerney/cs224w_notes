
* Review of ML on graphs
  * Node, Edge and Graph level prediction
  * Need to design and obtain features for nodes, edges, graph
  * Train and then apply model

### Lecture 2.1 - Node features

* Node level features
  * node degree - number of edges incident with the node
  * centrality - problem with degree is it doesn't consider the importance of neighbouring nodes. Centrality takes this into account.
    * eigenvector - define importance of node based on importance of neighbouring nodes. Definition is recursive. The definition of eigenvector importance can be written using linear algebra, with the vector of eigenvector centrality values as an eigenvector of a matrix A where $a_{ij}$ is 1 if node i is incident with node j, and 0 otherwise
    * betweeness - how many shortest paths the node lies on
    * closeness - based on shortest path distance to all other nodes
    * clustering coefficient - how connected the neighbours of a node are. Take how many neighbour pairs are connected divided by total number of neighbour pairs.
    * graphlets - graphlet degree vector. measures node's local network topology. Create a vector representing the rooted, induced, non-isomorphic subgraphs that can be found rooted at a node. There are 73 possible graphlets up to size 5.

* importance vs structure features
  * importance features - good for predicting influential nodes e.g. celebrity users
  * structure features - predict role of node in a graph e.g. functionality of a protein?
