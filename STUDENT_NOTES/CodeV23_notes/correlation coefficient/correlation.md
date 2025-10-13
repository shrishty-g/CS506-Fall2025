# Pearson's Correlation coefficient (r)

To find the correlation between two features, or how one feature changes with respect to another, we utilise the correlation coefficient.


$ r = \frac{\text{cov}(X, Y)}{\sigma_X \sigma_Y}$

Or: 

$
  r = \frac{\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}
           {\sqrt{\sum_{i=1}^{n}(x_i - \bar{x})^2} \sqrt{\sum_{i=1}^{n}(y_i - \bar{y})^2}}$

r ranges from -1 to 1, with a value of 1 signifying a perfect positive linear relationship (ex: y=x), a value of -1 signifying a perfect negative linear relationship (ex: y=-x), and a value of 0 signifying no linear correlation (ex: $ y= x^2 $).

Note that scaling the coefficients of the variables do not change r value. So, y=x has the same r coefficient=1 as y=9999x, since it is still linear in relation.

shifting the values also does nothing to change the value of r, so adding 100 to x will keep the value of r constant.
