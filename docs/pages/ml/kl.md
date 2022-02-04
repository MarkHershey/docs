# KL Divergence vs Cross Entropy


## Kullback–Leibler Divergence

KL Divergence is a statistical distance: a measure of how one probability distribution $Q$ is different from a second, reference probability distribution $P$.

For discrete distributions, the KL divergence is defined as:

$$
\begin{equation}
\begin{split}
D_{KL}(P || Q) 
& = - \sum_{i=1}^{N} P(x_i) \log \frac{Q(x_i)}{P(x_i)} \\
& = \sum_{i=1}^{N} P(x_i) \log \frac{P(x_i)}{Q(x_i)} \\
\end{split}
\end{equation}
$$

For continuous distributions, the KL divergence is defined as:

$$
\begin{equation}
\begin{split}
D_{KL}(P || Q)
& = \int_{-\infty}^{\infty} P(x) \log \frac{P(x)}{Q(x)} dx \\
& = \int_{-\infty}^{\infty} P(x) \log \frac{P(x)}{Q(x)} dx \\
\end{split}
\end{equation}
$$

- $D_{KL}(P || Q)$ is also called the __relative entropy__ of $P$ with respect to $Q$.
- __Relative entropy__ is always non-negative, $D_{KL}(P || Q) \geq 0$.
- $D_{KL}(P || Q)$ is a statistical distance. It is not a metric, but it is a divergence. Metrics are symmetric, and divergences are asymmetric. $D_{KL}(P || Q) \neq D_{KL}(Q || P)$.
- The logarithms in these formulae are taken to base $2$ if information is measured in units of [bits](https://en.wikipedia.org/wiki/Bit), or to base $e$ if information is measured in [nats](https://en.wikipedia.org/wiki/Nat_(unit)).

## Cross Entropy

The cross entropy is the average number of bits needed to encode data coming from a source with distribution p when we use model q.

The cross-entropy of the distribution $Q$ relative to a distribution $P$ over a given set is defined as follows:

$$
H(P, Q) = - \sum_{i=1}^{N} P(x_i) \log Q(x_i)
$$

For continuous distributions, the cross entropy is defined as:

$$
H(P, Q) = - \int_{-\infty}^{\infty} P(x) \log Q(x) dx
$$

## KL Divergence and Cross Entropy

$$
D_{KL}(P || Q) + H(P) = H(P, Q)
$$

$$
D_{KL}(P || Q) = H(P, Q) -  H(P)
$$

## References

- [Wikipedia - Mutual Information](https://en.wikipedia.org/wiki/Mutual_information)
- [Wikipedia - Kullback–Leibler divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)
- [Wikipedia - Cross entropy](https://en.wikipedia.org/wiki/Cross_entropy)