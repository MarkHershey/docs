# KL Divergence vs Cross Entropy

the cross entropy is the average number of bits needed to encode data coming from a source with distribution p when we use model q.

$$
D_{KL}(p||q) = \sum_{i=1}^{N} p(x_i) \log \frac{p(x_i)}{q(x_i)}
$$