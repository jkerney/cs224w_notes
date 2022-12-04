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
