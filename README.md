# Graph Convolution Neural Network

Traditional neural network focuses on mapping some functions of the input feature vector to the labels. However, not all kinds of information can be represented by a feature vector. Most notably, information in network that describes the relationships between nodes cannot be easily captured in common feature vectors used in deep learning. In fact, they are much better represented as networks and graphs. 

## Networks
Networks are everywhere. Some common examples include social media network, transportation system and the food chain. There is significant information in the connection and relationships (i.e. who is connected with whom). To fully leverage this information, we use graph convolution neural network (GCN).

## GCNs
The key concepts in GCN can be described as label propagation. To fully capture a node in a graph, we have to not only include information (features) about the node itself, but also that of its neighbours. This means the feature vector of a node will have to be some function of its and its neighbours' features. This is where the name *convolution* comes from, as we aggregate information from neighbours, just like in CNNs. While CNNs use filters and convolutions, GCNs does this with the help of adjacency matrix.

![](https://github.com/RussH-code/Graph-Convolutional-Neural-Network-GCN/blob/main/gcn1.PNG)

Source: <a href="https://arxiv.org/pdf/1901.00596.pdf">A Comprehensive Survey on Graph Neural Networks</a>

### Adjacency Matrix

![adj matrix](https://github.com/RussH-code/Graph-Convolutional-Neural-Network-GCN/blob/main/adjacency.gif)

Source: <a href="https://mathworld.wolfram.com/AdjacencyMatrix.html">Adjacency Matrix - Wolfram Alpha</a>

Adjacency matrix is a square matrix to describe the relationship of nodes in a graph. It denotes whether two nodes are connected/adjacent (1) or not (0). The core functionality of a GCN is implemented by the following equation:

<img src="http://www.sciweavers.org/tex2img.php?eq=%24%7BH%7D%5E%7Bl%2B1%7D%20%3D%20%5Csigma%28%7BW%7D%5Chat%7BA%7D%7BH%7D%5E%7Bl%7D%29%24&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0" align="center" border="0" alt="${H}^{l+1} = \sigma({W}\hat{A}{H}^{l})$" width="132" height="22" />

**H** is the input at the **l** hidden layer. For every layer, the input is multiplied with the adjacency matrix **A**, as well as the weights **W** that are learnt by the neural net. Sigma denotes the activation function. 

Nodes | A | B | C | D
 _ | _ | _ | _ | _
A | 0 | 0 | 1 | 1
B | 0 | 0 | 1 | 1
C | 1 | 1 | 0 | 0
D | 1 | 1 | 0 | 0
