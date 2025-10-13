# Dissimilarity

To gauge data structure, a dissimilarity function can be usedto return a value based on how close the data points are

A special kind of dissimilarity is a distance function, which has the requirements:
- distance is zero only if the data points are coincident, ie, d(i,j)=0 iff i=j.
- the function is commutative, ie, d(i,j)=d(j,i)
- the triangle inequality is held, ie, d(i,j)<=d(i,k)+d(k,j)

---

# Minkowski Distance

In a d dimensional space, and parameter $p \ge 1$:

$ L_p(x,y)= (\Sigma_i^d |x_i-y_i|^p)^{1/p} $

The parameter p defines the type of distance used.

---
# Manhattan distance

Also known as the taxicab distance, at p=1 the distance metric follows along the axes.

$ D(x, y) = \sum_{i=1}^{n} |x_i - y_i| $

---
# Euclidean distance

The classic straight line distance, at p=2 is just the shortest distance between the two points.

$ D(x, y) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2} $

---

As the value p rises, the exponent of p in the Minkowski distance formula causes the largest coefficients to dominate. Thus, as p approaches infinity (Chebyshev distance), the formula is just reduced to difference between the maximum coefficients.

on the other hand, a value of $0 \lt p \lt 1$, the triangle inequality does not hold, and thus the distance metric is no longer valid.

---

# Jaccard Similarity

For binary/set data, Manhattan distance can be used, but since it only returns the numerical difference between the two sets, it doesn't quite help with different sets with the same numerical difference.

Jaccard similarity utilizes intersections and unions instead:

$ J(A, B) = \frac{|A \cap B|}{|A \cup B|} $

And thus, Jaccard distance is 1-J(A,B)

---

# Cosine similarity

A similarity function that is useful when the direction of the data point vectors matters more than the magnitude is the cosine similarity

$ s(x,y)=cos(\theta) $

The corresponding dissimilarity function would be $ \frac{1}{s(x,y)} $ or 1-s(x,y)