# GMMs and Expectation Maximization

Upto now, each clustering algorithm is a hard clustering algorithm. It assigns each point a fixed cluster. Soft clustering on the other hand assigns clusters to points only in probabilities (ie, "soft" clustering).

For soft clustering, we treat the dataset as a mix of Gaussians, with specified weights/coefficients($\pi_k$), means($\mu_k$), and covariances($\Sigma_k$).


To find which cluster a point would belong to, we find the likelihood $P(C_k|X_i)$

using Naive Bayes,

$ P(C_k|X_i) = \frac{P(X_i|C_k)P(C_k)}{P(X_i)} $

The probability of a point under the GMM model is:

$ P(x_i)=\Sigma_{k=1}^K \pi_k N(x_i|\mu_k, \Sigma_k) $

The likelihood is also called the responsibility $\gamma_{ik}$ of cluster k for point $x_i$.

$\gamma_{ik}= \frac{\pi_k N(x_i|\mu_k, \Sigma_k)}{\Sigma_{j=1}^K \pi_j N(x_i|\mu_j, \Sigma_j)} $

---

# EM algorithm

To fit the GMM model, we use the expectation maximization algorithm:

With a random initialisation for mean, covariance and weight, 

1. **E-step:** We find what the responsibility $\gamma_{ik}$, or explanation of each cluster for the point $x_i$ using the formula above.

2. **M-step:** Next we update mean, covariance and weight based on the responsibility evaluated above.

$\mu_k=\frac{\Sigma_{i=1}^N \gamma_{ik}x_i}{\Sigma_{i=1}^N \gamma_{ik}}$

$\Sigma_k=\frac{\Sigma_{i=1}^N \gamma_{ik}(x_i-\mu_k)(x_i-\mu_k)^T}{\Sigma_{i=1}^N \gamma_{ik}}$

$\pi_k=\frac{\Sigma_{i=1}^N \gamma_{ik}}{N}$

The E and M steps are alternated until convergence, or until log likelihood stabilizes.

