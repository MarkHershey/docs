# The Basics of Deep Learning

## Activation Functions

| Name                       | Formula                                           | Graph | Range                           |
| -------------------------- | ------------------------------------------------- | ----- | ------------------------------- |
| Gaussian Error Linear Unit | $f(x) = \frac{x_1 + x_2}{1 + x_1 x_2}$            |       | $-\infty \leq f(x) \leq \infty$ |
| ReLU                       | $f(x) = \max(0,x)$                                |       | $f(x) \geq 0$                   |
| Leaky ReLU                 | $f(x) = \max(0,x) \quad \text{if} \quad x \geq 0$ |       | $f(x) \geq 0$                   |
| Sigmoid                    | $f(x) = \frac{1}{1+e^{-x}}$                       |       | $0 \leq f(x) \leq 1$            |
| Tanh                       | $f(x) = \tanh(x)$                                 |       | $-1 \leq f(x) \leq 1$           |
| GLU                        | $f(x) = \frac{x_1 + x_2}{1 + x_1 x_2}$            |       | $-\infty \leq f(x) \leq \infty$ |

## Loss Functions

| Name | Formula | Description |
| ---- | ------- | ----------- |

## Optimization Functions
