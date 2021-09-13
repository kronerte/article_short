https://distill.pub/2021/gnn-intro/

# Caracteristics of a graph
Nodes
Edges
Global

# What are data than can be represented as a graph ?
All data that expess as relationship between elements:
- Images
- Text
- Molecule
- Social
- Dataflow
- ...

# What are problem in Graph Learning ?
## Graph Level
Predict some global property on the graph.
Example: Bind prediction, ...
Analogous to image classification
## Node Level
Predict some local property on one node.
Examples: social group prediction, ...
Analogous to Image Segmentation
## Edge Level
Predict some property or the presence of one edge

# What are the challenges ?
Difficult to represent a graph as tensor, usable by deep learning algorithm.
It is possible to do for nodes, edge or graph embedding, but more difficult for connecivity.
This could be done with adjency matrice but:
- Very sparse and not efficient
- There are multiple adjency matrices (because of permutation): do not produce the same results
More efficient to use the list of connections.

# Graph Neural NEtworks
A GNN is a Neural NEtwork that preserve the symetries of the graph.
The embedding of the edges, nodes and graph are modified, but the connectivity is preserved.
## Simplest GNN
We apply on MLP over each Nodes; one MLP over each edges, one MLP over the Graph
## Pooling
To ensure that the information can circulating from node to egde, edge to node or node to global,
we may have to use pooling to average the embeddings of the neibourhood.

Rq: 
- All nodes/edges/global can be computed by stack
- The connecivity is only used at the pooling stage
## Message passing
The message passing consist of the following steps:
- For each aggregragate all embeging nodes from the neibourhood and sum
- Apply some transformation function
After some layers the message can pass trought all the graph
Can also be applied to the edge.
It is also called Graph Convolution

## Learning edge representations
We do not always have all the informations on a graph.
For example we may have only Edge information but want to predict nodes informations.
We can not directly use Message Passing.
First we use edge to node message message passing then node to edge (can be on the other order).
Rq: Because the two embedding space are not always the same size we may have to use linear transformation.
## Global information
To take in account the global informations, we may have to pass messages from edge or nodes to the global embedding.

# Other types of graphs
## Multigraphs
Each pair of nodes can have multiple edges.
For example to express different types of relations (falilly, friendship...).
A GNN can be adapted by having different message passing for each type of relation.
## Hypernode, nested graphs
Each node can be a graph
We can imagine having 2 model and altenating between the training.

# Batch and Sampling
Because of the variablitity of each graph size batch training is complicated.
Subsampling of graph is used, but it is a difficult problem.



# Attention GNN
Attention can be used to pass information thow the nodes.
The attention model the importance of each connection to process the information

# Graph Generation
Difficult to model topology generation.
Existing approaches:
- Adjancy matrice
- sequential construction using RNN





