# Graph Convolution Neural Network

Traditional neural network focuses on mapping some functions of the input feature vector to the labels. However, not all kinds of information can be represented by a feature vector. Most notably, information in network that describes the relationships between nodes cannot be easily captured in common feature vectors used in deep learning. In fact, they are much better represented as networks and graphs. 

## Networks
Networks are everywhere. Some common examples include social media network, transportation system and the food chain. There is significant information in the connection and relationships (i.e. who is connected with whom). To fully leverage this information, we use graph convolution neural network (GCN).

## GCNs
The key concepts in GCN can be described as label propagation. To fully capture a node in a graph, we have to not only include information (features) about the node itself, but also that of its neighbours. This means the feature vector of a node will have to be some function of its and its neighbours' features. This is where the name *convolution* comes from, as we aggregate information from neighbours, just like in CNNs. While CNNs use filters and convolutions, GCNs does this with the help of adjacency matrix.

![]()

### Adjacency Matrix

![]()

Adjacency matrix is a square matrix to describe the relationship of nodes in a graph. It denotes whether two nodes are connected/adjacent (1) or not (0). The core functionality of a GCN is implemented by the following equation:

