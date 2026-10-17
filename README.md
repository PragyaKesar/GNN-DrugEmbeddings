GNN-DrugEmbeddings

Unsupervised graph neural network embeddings of drug molecules from SMILES.

View the notebook: pragyakesar.github.io/GNN-DrugEmbeddings

Overview

This project converts 11,914 drug SMILES strings into molecular graphs with RDKit. Atoms are nodes and bonds are edges. Three graph autoencoders (GCN, GAT and GIN) learn a fixed length embedding for each drug. A graph contrastive learning variant is also tested. RDKit physicochemical descriptors are computed as a complementary feature set.

Methods
Node features: atomic number, aromaticity, formal charge, degree
Models: GCN, GAT and GIN autoencoders trained on node feature reconstruction (MSE loss)
Graph embedding: mean pooling of node embeddings
Evaluation: reconstruction error, KMeans silhouette scores, PCA and t-SNE visualization
Results
Embedding	Dimension	Reconstruction MSE	Silhouette (k = 5)
GCN	88	1.078	0.405
GAT	180	0.199	0.470
GIN	200	0.618	0.615
GCN + GAT + GIN	468	not applicable	0.434
Requirements

Python 3, RDKit, PyTorch, PyTorch Geometric, NetworkX, scikit-learn, pandas, NumPy, Matplotlib

References
Kipf TN, Welling M. Semi-supervised classification with graph convolutional networks. ICLR 2017.
Veličković P, et al. Graph attention networks. ICLR 2018.
Xu K, et al. How powerful are graph neural networks? ICLR 2019.
Fey M, Lenssen JE. Fast graph representation learning with PyTorch Geometric. ICLR Workshop 2019.
Author

Pragya Kesarwani
