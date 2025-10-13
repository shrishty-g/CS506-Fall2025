# Singular Value Decomposition

We can examine matrices to decompose it into a simpler matrix for easier handling.

Firstly, rank of a matrix is the number of linearly independent vectors in a matrix. It is obtained via the Gram Schmidt process.

For an mxn matrix, if the rank=min(m,n) the matrix is full rank.

For low rank matrices, there are redundancies/dependancies present.

For a matrix with rank k, A=UV, where U is nxk, V is kxm. This reduces storage from m.n to k(m+n) values.

Though most datasets are full rank, we can approximate a dataset A with a similar $A^k$, such that $d(A,A^k)$ is small and k is sufficiently small compared to m and n to justify the approximation.

When k<rank(A), rank k approximation of A:

$A^k=argmin_{B|rank(B)=k} d_f(A,B)$

Where $d_f$ is the Frobenius distance, $\sqrt{\Sigma_{i,j}(a_{ij}-b_{ij})^2}$

Now, we can improve matrix factorisation:

$A=U \Sigma V^T$

Where U is nxr, V is mxr. Both are Orthogonal and unit length, so $U^TU = V^TV = I$

$\Sigma$ is a diagonal matrix, with the diagonal values $\sigma_1, sigma_2,... \sigma_r$ in descending order being the singular values, or square root of the eigenvalues of $A^TA$

The $i^{th}$ singular vector is the direction of most variance, signified by $\sigma_i$.



The best k rank approximation of A would be:

$A^k=U_k \Sigma_k V^T_k$

Also, $d_f(A,A^k)=\Sigma_{i=k+1}^r \sigma_i^2$ gives the approximation error. This is known as the Eckart-Young theorem.

For appropriate decomposition, k can be found using the elbow plot of singular values, and also the residual errors of other values of k.



Principal Component Analysis can also be done with the largest directions of variance providing the best directions to take. So, the top singular vectors are taken to reduce dimensionality.

The largest rows of $A-A^k$ can also be seen as anomalies to detect.