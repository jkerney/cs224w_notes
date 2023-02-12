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

## Lecture 6.3 - Deep Learning for Graphs

- Naive approach to representing graph in a neural network
    - Adjacency matrix appended with node features
    - Problems:
        - $O(|V|)$ parameters. End up with more parameters than rows of training data. Leads to overfitting?
        - Sensitive to node ordering. Using a different order of node neighbours leads to different inputs to the parameters.
    - Instead use ideas from convolutional neural networks to scan over a subset of a grid and produce a summary pixel.
 
- GNN architecture
    - Each node has a computation graph
        - Propogate and transform information
        - Generate node embeddings based on local network neighbourhoods
        - Nodes aggregate information from neighbours using neural networks
        - Every node defines a computation graph based on its neighbourhood
    - Model of arbitrary depth
        - Nodes have embeddings at each layer
        - Layer 0 embedding is the input feature of the node
        - Layer k embedding gets information from nodes that are k hops away
        - Number of layers would depend on width of graph - what's the length of the longest shortest path?
    - Neighbourhood aggregation
        - Basic - average information from neighbours and apply a neural network (linear transformation followed by non-linearity)
    - Formula for node embeddings
        - at level 0, node embedding $h_{0}$ is just the node feature itself
        - at level i, node embedding $h_{i}$ is
            - linear transformation $W$ applied to the average of the node's neighbours node embeddings at the previous layer
            - linear transformation $B$ applied to the node's previous node embedding
            - Linear transformations summed, then a non-linear transformation applied

    - We can use adjacency matrix to write an equation that generates node embeddings for all nodes at once
        - $H^{(l)} = [h_{1} h_{2} ... h_{|v|}]$
        - Once we have this, we can write $H^{(l+1)} = D^{-1}AH^{(l)}W_{l}^{T} + H^{(l)}B_{l}^{T}$

    - Can then feed node embeddings into a loss function, apply SGD to train the weights of the transformations
    - Can use in both supervised and unsupervised context. In the unsupervised context, we choose a similarity measure e.g. node2vec, matrix factorisation. We then train the model to predict the similarity of the similarity measure.

    - Can apply model on graphs we haven't seen before. Can generalise to unseen nodes. Could train on a small graph and apply to a large graph.

