# Clustering Aggregation

To obtain more robust information on a dataset, we can combine results from multiple clusterings via clustering aggregation.

For 2 clusterings P and C, aggregation of clusterings can be done via disagreement distance:

$D(P,C)=\Sigma_{x,y} I_{P,C}(x,y)$ 

$I_{P,C}(x,y) =$ 1 if P and C disagree, 0 otherwise.

So, our goal is to find an optimal clustering from a set of m clusterings, that minimizes $\Sigma_{i=1}^m D(C*,C_i)$. However, since this is NP-hard, we often use approximations and heuristics to solve it.

Quick example for problems:

Index:  1 2 3 4 5

P:_____ 1 2 1 1 2

C:_____ 1 1 2 2 1

We make a Disagreement table for each pair:

| Pair  | P(i) | P(j) | Same in P? | C(i) | C(j) | Same in C? | Disagree? |
| ----- | ---- | ---- | ---------: | ---- | ---- | ---------: | --------: |
| (1,2) | 1    | 2    |          0 | 1    | 1    |          1 |         1 |
| (1,3) | 1    | 1    |          1 | 1    | 2    |          0 |         1 |
| (1,4) | 1    | 1    |          1 | 1    | 2    |          0 |         1 |
| (1,5) | 1    | 2    |          0 | 1    | 1    |          1 |         1 |
| (2,3) | 2    | 1    |          0 | 1    | 2    |          0 |         0 |
| (2,4) | 2    | 1    |          0 | 1    | 2    |          0 |         0 |
| (2,5) | 2    | 2    |          1 | 1    | 1    |          1 |         0 |
| (3,4) | 1    | 1    |          1 | 2    | 2    |          1 |         0 |
| (3,5) | 1    | 2    |          0 | 2    | 1    |          0 |         0 |
| (4,5) | 1    | 2    |          0 | 2    | 1    |          0 |         0 |


Total number of pairs=$(^5_2)=5*4/2=10$

So, disagreement distance= $\frac{1+1+1+1+0+0+0+0+0+0}{10} = 0.4$