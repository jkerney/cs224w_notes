# Week 6 - Graph Neural Networks

## Lecture 6.1 - Introduction to Graph Neural Networks

### Recap

- Node Embeddings
    - Technique that maps nodes to a d-dimensional space so that similar nodes are close together
    - Requires an encoder and a similarity function

- Shallow Encoders
    - node2vec is an example
    - Downsides
        - Require $O(|V|)$ parameters. Large graphs require large number of parameters.
        - Every node has a unique embedding
        - Transductive - can't generate embeddings for nodes not seen during training
        - Don't incorporate node features

- Deep Graph Encoders
    - Approach that uses multiple layers of non-linear transformations
    - Combined with similarity measures
    - Can apply this approach to node classification, link prediction, community detection, network (subgraph) similarity
 
 - Modern deep learning toolbox is designed for sequences and grids e.g. audio and images
     - Require a different approach for networks
     - No spatial locality, unlike grids which have up, down, left, right
     - No reference point
     - Dynamic
     - Multimodal features (is this referring to networks having nodes of different types?)

## Lecture 6.2 - Basics of Deep Learning

- Machine learning as optimisation
    - Given input x, predict y
    - Formulate task as optimisation
    - $min_\theta L(y,f(x))$ where $\theta$ is parameters of the model
    - Loss function
        - L2
        - Cross entropy
    - How do we optimise the objective function
        - Gradient vector
        - Repeatedly update weights iteratively
        - Learning rate  - control size of gradient step
        - Gradient descent requires full dataset, so use Stochastic Gradient Descent. Use a minibatch.
            - Epoch - one full pass over dataset
            - SGD is unbiased estimator of full gradient
          
- Neural Network function
    - forward propogation - compute L given x
    - back propogation - compute gradient of L with respect to model parameters
    - introduce non-linearity - relu, sigmoid
    - Multi-layer Perceptron - each layer has bias and non-linearity

## Lecture 6.2 - Deep Learning for Graphs

- Graph G with following
    - $V$ vertex set
    - $A$ adjacency matrix
    - $X \in \mathbb{R}^{m \times |V|}$
    - $v$ node in $V$
    - $n(v)$ neighbours of node $v$

- Naive approach to representing graph
    - matrix of adjacency matrix appended with node features
    - Problems:
        - $O(|V|)$ parameters
        - sensitive to node ordering
    - Use ideas from convolutional neural networks
    - Node's neighbourhood defines a computation graph
        - Determine node computation graph
        - Propogate and transform information
        - Generate node embeddings based on local network neighbourhoods
        - Nodes aggregate information from neighbours using neural networks
        - Every node defines a computation graph based on its neighbourhood
        - Every node comes with its own neural network architecture?
        - Model of arbitrary depth
            - Nodes have embeddings at each layer
            - Layer 0 embedding is the input feature of the node
            - layer k embedding gets information from nodes that are k hops away
        - Neighbourhood aggregation
            - Basic - average information from neighbours and apply a neural network (linear transformation followed by non-linearity)
        - Matrix formulation
            - note all nodes use the same $W$ and $b$
    - Can apply model on graphs we haven't seen before. Can generalise to unseen nodes. Could train on a small graph and apply to a large graph.
    - 

