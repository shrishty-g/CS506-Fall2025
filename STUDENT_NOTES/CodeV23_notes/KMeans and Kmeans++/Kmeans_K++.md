# Kmeans Clustering

A method of unsupervised learning is clustering, which groups data into meaningful clusters to provide information on data structure.

The types of clustering include partitional, hierarchial, density based and soft clustering.

Kmeans is a type of partitional clustering, where k random centers $ \mu_1, \mu_2....\mu_k  $ are initialized. Then, via Lloyd's algorithm, the centers are recomputed until convergence, with the end goal to minimize the cost function, also called the within-cluster sum of squares (WCSS): 

$ \sum_{k=1}^{K} \sum_{x_i \in C_k} d(x_i, \mu_k) $ 

= $\sum_{k=1}^{K} \sum_{x_i \in C_k} \|x_i - \mu_k\|^2$

Lloyd's algorithm is as follows:
1. Randomly pick k centers $\mu_1, … , \mu_k$
2. Assign each point in the dataset to its closest center
3. Compute the new centers as the means of each cluster
4. Repeat 2 & 3 until convergence

Note that this algorithm will always converge in a finite amount of steps, as the cost always either decreases or remains the same, thus the cost will always arrive at a minimum. The assignment also cannot cycle between one cluster and another, since if the cost decreases upon one assignment, the point will not increase the cost by reassigning itself to the old cluster.


However, although the cost will always converge at a minimum, the minimum may not be the global optimal minimum.

If the centers are too close, bad partitions and local minima are possible.

So, we can utilize farthest first traversal, where the first center is randomly chosen and every other center is always taken as the farthest possible point from any other center.

This also has some caveats though, where if several outliers are present, they will be chosen as cluster centers, ignoring cluster centers.

---

# Kmeans++

So, we initialize with a combination of the two methods:
1. Start with a random center
2. Let $D(x)$ be the distance between x and the closest of the centers picked
so far. Choose the next center with probability proportional to $D(x)^2$

---

# How do we find k?

The number of clusters k can be found through a variety of ways.

- Sometimes, we can gauge an appropriate value through simply observing the dataset.

- Plotting the Cost (WCSS) vs the values of k, there is a certain point known as the elbow of the curve where further increase of k provides diminishing returns. This is often a good starting value for k.

- Other values include comparing our clustering to a random distribution of the same number of points.

---
# Evaluation of clusters

Silhouette scores are generally used to evaluate clusters.

$ s_i=\frac{(b_i-a_i)}{max(a_i,b_i)} $

Where $a_i$ is the mean distance from point i to every other point in its cluster, and $b_i$ is the smallest mean distance from point i
to every point in another cluster.

Silhouette scores can range from -1 to 1, with a value of 1 signifying perfect classification, a value of 0 signifying the point as a bouncdary point, and values less than 0 signifying misclassification.

---
# Other kinds of Kmeans

- K-medians (uses the L1norm / manhattan distance)
- K-medoids (any distance function + the centers must be in the dataset)
- Weighted K-means (each point has a different weight signifying varying importance when computing the
mean)
