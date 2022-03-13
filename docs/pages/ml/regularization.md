# Regularization


## Definition

Regularization is "any modification we make to a learning algorithm that is intended to reduce its generalization error but not its training error". In another words, regularization is a way to "penalize" the model for overfitting, thereby improving its performance on test set.

We can define a regularized objective function $\tilde{J}$ as follows:

$$
\tilde{J}(\theta; \mathbf{X}, \mathbf{y}) = J(\theta; \mathbf{X}, \mathbf{y}) + \alpha \Omega(\theta)
$$

- $\theta$ denotes the model parameters.
- $\mathbf{X}$ denotes the training input.
- $\mathbf{y}$ denotes the training label.
- $J$ denotes the original objective function.
- $\tilde{J}$ denotes the regularized objective function.
- $\Omega(\theta)$ is the regularization term (usually a norm penalty).
- $\alpha$ is a scalar hyperparameter and $\alpha \in [0, \infty)$.

## Choice of the Norm Penalty

### L2 Regularization

L2 regularization, also known as weight decay, ridge regression, or Tikhonov regularization.

$$
\Omega(\theta) = \frac{1}{2} {\| \mathbf{w} \|}_2^2
$$

- $\mathbf{w}$ denotes the model parameters thats needs regularization.
- $\theta$ denotes all the model parameters.
- ${\| \mathbf{w} \|}_2$ denotes the $L^2$ norm, a.k.a. Euclidean norm.



### L1 Regularization

$$
\Omega(\theta) = {\| \mathbf{w} \|}_1
$$

- $\mathbf{w}$ denotes the model parameters thats needs regularization.
- $\theta$ denotes all the model parameters.
- ${\| \mathbf{w} \|}_1$ denotes the $L^1$ norm, a.k.a. Manhattan norm.


## References

```bibtex
@book{Goodfellow-et-al-2016,
    title={Deep Learning},
    author={Ian Goodfellow and Yoshua Bengio and Aaron Courville},
    publisher={MIT Press},
    note={\url{http://www.deeplearningbook.org}},
    year={2016}
}
```