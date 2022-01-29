# speciescomposition_communities


# Learning Objectives {.unnumbered}

In this lab, we worked with **unsupervised classification** techniques while working with **ecological community** datasets.

- Comparing species counts between sites using **distance** metrics:

  - **Euclidean** calculates the distance between a virtualized space using Pythagorean theorem.
  
  - **Manhattan** calculates integer "around the block" difference.
  
  - **Bray-Curtis** dissimilarity is based on the sum of lowest counts of shared species between sites over the sum of all species. A dissimilarity value of 1 is completely dissimilar, i.e. no species shared. A value of 0 is completely identical.

- **Clustering**

  - **_K_-Means clustering** with function `kmeans()` given a pre-assigned number of clusters assigns membership centroid based on reducing within cluster variation.
  
    - **Voronoi diagrams** visualizes regions to nearest points, useful here to show membership of nodes to nearest centroid.
  
  - **Hierarchical clustering** allows for a non-specific number of clusters. 
  
    - **Agglomerative hierarchical clustering**, such as with `diana()`, agglomerates as it builds the tree. It is good at identifying small clusters.

    - **Divisive hierarchical clustering**, such as with `agnes()`, divides as it builds the tree. It is good at identifying large clusters.
    
    - **Dendrograms** visualize the branching tree.

- **Ordination** (coming Monday)

# Clustering

**Clustering** associates similar data points with each other, adding a grouping label. It is a form of **unsupervised learning** since we don't fit the model based on feeding it a labeled response (i.e. $y$). 

## _K_-Means Clustering

Source: [K Means Clustering in R | DataScience+](https://datascienceplus.com/k-means-clustering-in-r/)

In _k_-means clustering, the number of clusters needs to be specified. The algorithm randomly assigns each observation to a cluster, and finds the centroid of each cluster. Then, the algorithm iterates through two steps:

1. Reassign data points to the cluster whose centroid is closest.
1. Calculate new centroid of each cluster.

These two steps are repeated until the within cluster variation cannot be reduced any further. The within cluster variation is calculated as the sum of the euclidean distance between the data points and their respective cluster centroids.

- **Ordination** orders sites near each other based on similarity. It is a multivariate analysis technique used to effectively collapse dependent axes into fewer dimensions, i.e. dimensionality reduction.

  - **Principal Components Analyses (PCA)** is the most common and oldest technique that assumes linear relationships between axes. You will follow a non-ecological example from [Chapter 17 Principal Components Analysis | Hands-On Machine Learning with R](https://bradleyboehmke.github.io/HOML/pca.html) to learn about this commonly used technique.
  
  - **Non-metric MultiDimensional Scaling (NMDS)** allows for non-linear relationships. This ordination technique is implemented in the R package [`vegan`](https://cran.r-project.org/web/packages/vegan/index.html). You'll use an ecological dataset, species and environment from lichen pastures that reindeer forage upon, with excerpts from the [vegantutor vignette](https://github.com/bbest/eds232-ml/raw/main/files/vegantutor.pdf) ([source](https://github.com/jarioksa/vegandocs)) to apply these techniques:
    - **Unconstrained ordination** on species using NMDS;
    - Overlay with environmental gradients; and
    - **Constrained ordination** on species and environmnent using another ordination technique, **canonical correspondence analysis (CCA)**.
