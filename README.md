<div align="center">
🧬 GNN-DrugEmbeddings

Unsupervised graph neural network embeddings of drug molecules from SMILES

View Notebook

Python PyTorch PyG RDKit

</div>
📖 Overview

This project converts 11,914 drug SMILES strings into molecular graphs with RDKit. Atoms are nodes and bonds are edges.

Three graph autoencoders learn a fixed length embedding for each drug:

GCN (Graph Convolutional Network)
GAT (Graph Attention Network)
GIN (Graph Isomorphism Network)

A graph contrastive learning variant is also tested. RDKit physicochemical descriptors are computed as a complementary feature set.

👉 Open the full rendered notebook

⚙️ Methods
Step	Details
Input	DrugBank IDs and SMILES strings
Graph construction	RDKit molecule → NetworkX graph → PyTorch Geometric Data object
Node features	Atomic number, aromaticity, formal charge, degree
Edge features	Bond type, aromaticity
Models	GCN, GAT and GIN autoencoders
Training loss	Mean squared error of node feature reconstruction
Graph embedding	Mean pooling of node embeddings
Evaluation	Reconstruction error, KMeans silhouette scores, PCA and t-SNE plots
📊 Results
Embedding	Dimension	Reconstruction MSE ↓	Silhouette (k = 5) ↑
GCN autoencoder	88	1.078	0.405
GAT autoencoder	180	0.199	0.470
GIN autoencoder	200	0.618	0.615
GCN + GAT + GIN (concatenated)	468	n/a	0.434

Key findings

The GAT autoencoder achieved the lowest reconstruction error.
The GIN autoencoder produced the best separated clusters at k = 5.
🛠️ Requirements
Package	Purpose
RDKit	SMILES parsing and molecular descriptors
PyTorch	Model training
PyTorch Geometric	Graph neural network layers
NetworkX	Graph construction and visualization
scikit-learn	Clustering, PCA and t-SNE
pandas, NumPy, Matplotlib	Data handling and plotting
🚀 Usage
bash
git clone https://github.com/pragyakesar/GNN-DrugEmbeddings.git
cd GNN-DrugEmbeddings
Install the packages listed above.
Place the input CSV (drugbank_id, SMILES) in the repository folder.
Update the file path in the data loading cell.
Run the notebook from top to bottom.
📚 References
Kipf TN, Welling M. Semi-supervised classification with graph convolutional networks. ICLR 2017.
Veličković P, et al. Graph attention networks. ICLR 2018.
Xu K, et al. How powerful are graph neural networks? ICLR 2019.
Fey M, Lenssen JE. Fast graph representation learning with PyTorch Geometric. ICLR Workshop 2019.
👩‍🔬 Author

Pragya Kesarwani
