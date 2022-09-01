### Lecture 1
* Networks (Natural Graphs) - Examples
  * Social networks
  * Communication and transactions
  * Biomedicine
  * Brain connections
* Graph Examples
  * Knowledge
  * Software
  * Similarity
  * Relational structures

* How do we use graphs to improve predictive performance?
* Graphs are hard
  * Arbitrary size
  * No reference point
  * Dynamic
* With representation learning, we avoid feature engineering
  * Map nodes to embeddings so that similar nodes are embedded close together

### Lecture 2

* Examples of Graph ML tasks
  * node classification
  * link prediction
    * recommender systems - recommend items users might like to buy
    * traffic prediction via GNN
  * graph classification
  * clustering
  * graph generation/evolution

### Lecture 3

 * How network is defined will affect usefulness
 * Bipartite graph - two disjoint sets of nodes. Links only between sets, not within sets. Sets are independent.
   * Folded network
   * Projection network
     * Project network onto a U and V set
 * Adjacency matrix
   * Most networks are sparse
 * Edge list
   * Not great for manipulation, e.g. hard to compute degree of a node
 * Adjacency list
 * More types - weighted edges, self edges, multigraph (multiple edges between a pair of nodes)
 * Connectivity
   * Connected components - can write adjacency matrix in block diagonal form
   * Strongly and weakly connected - weak if we ignore edge direction
