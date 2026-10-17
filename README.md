<div align="center">

<h1>🧬 GNN-DrugEmbeddings</h1>

<b>Unsupervised graph neural network embeddings of drug molecules from SMILES</b>

<br><br>

<a href="https://pragyakesar.github.io/GNN-DrugEmbeddings/"><img src="https://img.shields.io/badge/View-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="View Notebook"></a>

<br>

<a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white" alt="Python"></a>
<a href="https://pytorch.org/"><img src="https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white" alt="PyTorch"></a>
<a href="https://pytorch-geometric.readthedocs.io/"><img src="https://img.shields.io/badge/PyTorch%20Geometric-3C2179" alt="PyTorch Geometric"></a>
<a href="https://www.rdkit.org/"><img src="https://img.shields.io/badge/RDKit-cheminformatics-2E8B57" alt="RDKit"></a>

</div>

<hr>

## 📖 **Overview**

This project converts **11,914 drug SMILES strings** into molecular graphs with [RDKit](https://www.rdkit.org/). Atoms are nodes and bonds are edges.

Three graph autoencoders learn a fixed length embedding for each drug:

* **GCN** (Graph Convolutional Network)
* **GAT** (Graph Attention Network)
* **GIN** (Graph Isomorphism Network)

A **graph contrastive learning** variant is also tested. RDKit **physicochemical descriptors** are computed as a complementary feature set.

👉 **[Open the full rendered notebook](https://pragyakesar.github.io/GNN-DrugEmbeddings/)**

<hr>

## ⚙️ **Methods**

<table>
  <thead>
    <tr>
      <th align="left"><b>Step</b></th>
      <th align="left"><b>Details</b></th>
    </tr>
  </thead>
  <tbody>
    <tr><td><b>Input</b></td><td>DrugBank IDs and SMILES strings</td></tr>
    <tr><td><b>Graph construction</b></td><td>RDKit molecule → NetworkX graph → PyTorch Geometric <code>Data</code> object</td></tr>
    <tr><td><b>Node features</b></td><td>Atomic number, aromaticity, formal charge, degree</td></tr>
    <tr><td><b>Edge features</b></td><td>Bond type, aromaticity</td></tr>
    <tr><td><b>Models</b></td><td>GCN, GAT and GIN autoencoders</td></tr>
    <tr><td><b>Training loss</b></td><td>Mean squared error of node feature reconstruction</td></tr>
    <tr><td><b>Graph embedding</b></td><td>Mean pooling of node embeddings</td></tr>
    <tr><td><b>Evaluation</b></td><td>Reconstruction error, KMeans silhouette scores, PCA and t-SNE plots</td></tr>
  </tbody>
</table>

<hr>

## 📊 **Results**

<table>
  <thead>
    <tr>
      <th align="left"><b>Embedding</b></th>
      <th align="center"><b>Dimension</b></th>
      <th align="center"><b>Reconstruction MSE ↓</b></th>
      <th align="center"><b>Silhouette (k = 5) ↑</b></th>
    </tr>
  </thead>
  <tbody>
    <tr><td>GCN autoencoder</td><td align="center">88</td><td align="center">1.078</td><td align="center">0.405</td></tr>
    <tr><td>GAT autoencoder</td><td align="center">180</td><td align="center"><b>0.199</b></td><td align="center">0.470</td></tr>
    <tr><td>GIN autoencoder</td><td align="center">200</td><td align="center">0.618</td><td align="center"><b>0.615</b></td></tr>
    <tr><td>GCN + GAT + GIN (concatenated)</td><td align="center">468</td><td align="center">n/a</td><td align="center">0.434</td></tr>
  </tbody>
</table>

**Key findings**

* The **GAT** autoencoder achieved the lowest reconstruction error.
* The **GIN** autoencoder produced the best separated clusters at k = 5.

<hr>

## 🛠️ **Requirements**

<table>
  <thead>
    <tr>
      <th align="left"><b>Package</b></th>
      <th align="left"><b>Purpose</b></th>
    </tr>
  </thead>
  <tbody>
    <tr><td><a href="https://www.rdkit.org/">RDKit</a></td><td>SMILES parsing and molecular descriptors</td></tr>
    <tr><td><a href="https://pytorch.org/">PyTorch</a></td><td>Model training</td></tr>
    <tr><td><a href="https://pytorch-geometric.readthedocs.io/">PyTorch Geometric</a></td><td>Graph neural network layers</td></tr>
    <tr><td><a href="https://networkx.org/">NetworkX</a></td><td>Graph construction and visualization</td></tr>
    <tr><td><a href="https://scikit-learn.org/">scikit-learn</a></td><td>Clustering, PCA and t-SNE</td></tr>
    <tr><td>pandas, NumPy, Matplotlib</td><td>Data handling and plotting</td></tr>
  </tbody>
</table>

<hr>

## 🚀 **Usage**

```bash
git clone https://github.com/pragyakesar/GNN-DrugEmbeddings.git
cd GNN-DrugEmbeddings
```

1. Install the packages listed above.
2. Place the input CSV (`drugbank_id`, `SMILES`) in the repository folder.
3. Update the file path in the data loading cell.
4. Run the notebook from top to bottom.

<hr>

## 📚 **References**

1. Kipf TN, Welling M. [Semi-supervised classification with graph convolutional networks](https://arxiv.org/abs/1609.02907). *ICLR* 2017.
2. Veličković P, et al. [Graph attention networks](https://arxiv.org/abs/1710.10903). *ICLR* 2018.
3. Xu K, et al. [How powerful are graph neural networks?](https://arxiv.org/abs/1810.00826) *ICLR* 2019.
4. Fey M, Lenssen JE. [Fast graph representation learning with PyTorch Geometric](https://arxiv.org/abs/1903.02428). *ICLR Workshop* 2019.

<hr>

## 👩‍🔬 **Author**

**Pragya Kesarwani**
