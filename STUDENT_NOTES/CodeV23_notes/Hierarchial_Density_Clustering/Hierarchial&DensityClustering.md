# Hierarchial Clustering

Hierarchial clustering can be of two types:

1. *Agglomerative Clustering*: Points begin in their separate clusters, and the closest clusters (based on chosen type of linkage) are merged. This is repeated until every point is in the same cluster.

2. *Divisive Clustering* : Points begin in one cluster, and partitions are made to split this cluster into smaller clusters until every point is in its own cluster.

The distance functions used are called linkages. The types of linkages are:

1. Single Linkage: The minimum of pairwise distances of intra cluster points, or the shortest distance from a point in one cluster to a point in another. Though it can handle different sizes of clusters, it is sensitive to noise points and tends to create elongated clusters.

$ D_SL(C_1,C_2) = min(d(p_1,p_2))|p_1 \epsilon C1, p_2 \epsilon C2 $

2. Complete Linkage: The maximum of pairwise distances of intra cluster points, or the longest distance from a point in one cluster to a point in another. It is less susceptible to noise but tends to split up larger clusters to focus on equal diameter clusters.

$ D_CL(C_1,C_2) = max(d(p_1,p_2))|p_1 \epsilon C1, p_2 \epsilon C2 $

3. Average Linkage: The average of all pairwise distances of intra cluster points. It handles noise better but prefers globular clusters.

$ D_AL(C_1,C_2) = \frac{1}{C_1.C_2} \Sigma_{p_1 \epsilon C_1, p_2 \epsilon C_2} d(p_1,p_2) $

4. Centroid Linkage: Distance between cluster centroids

$ D_C=d(\mu_1,\mu_2) $

5. Ward's Distance: The difference between the variance or spread of points in the merged and the unmerged clusters.

$ D_WD = \Sigma_{p \epsilon C_{12}} d(p, \mu_{12}) - \Sigma_{p_1 \epsilon C_1} d(p_1, \mu_1) -\Sigma_{p_2 \epsilon C_2} d(p_2, \mu_2) $

A dendrogram can be created for the merging process of agglomerative clustering, and we can make a "cut" at our required threshold to obtain our required clusters.

A distance matrix can also be created for the clustering process. Note that this matrix must follow the rules:

- Diagonals ($AA, BB, CC$, so on) must be 0.
- Symmetry ($AB=BA$).
- Triangle inequlity ($AB+AC\ge AC$)

---
# Density Based Clustering

Simply put, an area is considered dense if it has at least min_pts number of data points within a fixed radius $\epsilon$.

The DBSCAN algorithm clusters based on this method.

Given $\epsilon$ and min_pts, the neighborhood of each point defines its status as core, border, or noise:

- If a point satisfies min_pts neighboring points within the radius of $\epsilon$, it is classified as a core point.

- If the point is within the radius of a core point, but does not possess the min_pts neighbors to be classified as a core point itself, it is a border point.

- All the points unable to be classified as core or border points are noise points.

The algorithm uses these definitions to create clusters around the core points and assign border points to nearby clusters. 

DBSCAN tends to focus on making equal density clusters, and thus can struggle with datasets with varying densities and higher dimensions.