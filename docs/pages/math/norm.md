# Norm

- Norm is a function that maps from real or complex vector space to the non-negative real number space.
- If we think about a vector as a transformation, norm measures the magnitude of the transformation. (not sure if we can say so)



## L1 Norm

AKA Manhattan Norm, Taxicab Norm, 1-norm.

$$
{\| \mathbf{x} \|}_{1} := \sum_{i=1}^{n} |x_i|
$$

## L2 Norm

AKA Euclidean norm, 2-norm, square norm.

$$
{\| \mathbf{x} \|}_{2} := \sqrt{\sum_{i=1}^n x_i^2} = \sqrt{ \mathbf{x} \cdot \mathbf{x}}
$$

-  $\mathbf{x} \cdot \mathbf{x}$ denotes the dot product of two vectors in $\mathbb{R}^n$.

## Lp Norm

$$
{\| \mathbf{x} \|}_{p} := (\sum_{i=1}^{n} {|x_i|}^{p})^{\frac{1}{p}}
$$

## Maximum Norm

Special case of uniform norm, supermum norm, Chebyshev norm, or infinity norm.

$$
{\| \mathbf{x} \|}_{\infty} := \max(|x_1|, |x_2|, ..., |x_n|)
$$

## References

- [Wikipedia - Norm](https://en.wikipedia.org/wiki/Norm_(mathematics))
- [Wikipedia - Uniform norm](https://en.wikipedia.org/wiki/Uniform_norm)
- [Wikipedia - Euclidean space](https://en.wikipedia.org/wiki/Euclidean_space)
- [Wikipedia - Inner product space](https://en.wikipedia.org/wiki/Inner_product_space)
- [Wikipedia - L^p space](https://en.wikipedia.org/wiki/Lp_space)