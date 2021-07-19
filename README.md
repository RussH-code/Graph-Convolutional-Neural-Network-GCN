# Graph Convolution Neural Network

Traditional neural network focuses on mapping some functions of the input feature vector to the labels. However, not all kinds of information can be represented by a feature vector. Most notably, information in network that describes the relationships between nodes cannot be easily captured in common feature vectors used in deep learning. In fact, they are much better represented as networks and graphs. 

## Networks
Networks are everywhere. Some common examples include social media network, transportation system and the food chain. There is significant information in the connection and relationships (i.e. who is connected with whom). To fully leverage this information, we use graph convolution neural network (GCN).

## GCNs
The key concepts in GCN can be described as label propagation. To fully capture a node in a graph, we have to not only include information (features) about the node itself, but also that of its neighbours. This means the feature vector of a node will have to be some function of its and its neighbours' features. This is where the name *convolution* comes from, as we aggregate information from neighbours, just like in CNNs. While CNNs use filters and convolutions, GCNs does this with the help of adjacency matrix.

![](https://github.com/RussH-code/Graph-Convolutional-Neural-Network-GCN/blob/main/gcn1.PNG)

Photo: <a href="https://arxiv.org/pdf/1901.00596.pdf">A Comprehensive Survey on Graph Neural Networks</a>

### Adjacency Matrix

![adj matrix](https://github.com/RussH-code/Graph-Convolutional-Neural-Network-GCN/blob/main/adjacency.gif)

Photo: <a href="https://mathworld.wolfram.com/AdjacencyMatrix.html">Adjacency Matrix - Wolfram Alpha</a>

Adjacency matrix is a square matrix to describe the relationship of nodes in a graph. It denotes whether two nodes are connected/adjacent (1) or not (0). The core functionality of a GCN is implemented by the following equation:

<img src="https://render.githubusercontent.com/render/math?math={H}^{l+1} = \sigma({W}\hat{A}{H}^{l})">

**H** is the input at the **l** hidden layer. For every layer, the input is multiplied with the adjacency matrix **A**, as well as the weights **W** that are learnt by the neural net. Sigma denotes the activation function. 

### Example: 
Given Adjacency matrix 

Nodes | A | B | C | D
---- | ---- | ---- | ---- | ----
A | 0 | 0 | 1 | 1
B | 0 | 0 | 1 | 1
C | 1 | 1 | 0 | 0
D | 1 | 1 | 0 | 0

and features

Nodes | Values
----- | ------
A | 1
B | 2
C | 3
D | 4

If we perform matrix multiplication, we will get 

Nodes | Values
----- | ------
A | 7
B | 7
C | 3
D | 3

The values of features changed depending on their relationships with neighbours. The node information is said to have propagated to its neighbours. The actual implementation is more complicated, the original graph neural network recommended using normalized adjacency matrix, we will discuss and implement that in the jupyter notebook.

This is the key idea in GCNs, the rest is similar to a normal neural network.

----
# Jupyter notebook
## 1. Graph neural network from scratch
In this notebook we go through the concepts of graph neural network by implementing a graph neural network from scratch to show the inner workings.

## 2. Stellargraph library
We also demonstrate using pre-built convolutional network implemented in `Stellarpgraph` library. This library is built on the `Keras` library, so should be easy to pick up for `tensorflow` users.

--- 
## References
1. <a href="https://youtu.be/8owQBFAHw7E">Intro to graph neural networks (ML Tech Talks)</a>
2. <a href="https://stellargraph.readthedocs.io/en/stable/demos/node-classification/gcn-node-classification.html">Node classification with Graph Convolutional Network</a>
3. <a href="https://towardsdatascience.com/how-to-do-deep-learning-on-graphs-with-graph-convolutional-networks-7d2250723780">A High-Level Introduction to Graph Convolutional Networks
</a>
