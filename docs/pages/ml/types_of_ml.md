# Types of Machine Learning 

## Supervised Learning

- Classification 
    - classify discrete values, predict discrete categories
- Regression
    - predict continuous values

## Unsupervised Learning

- Clustering
- Dimensionality Reduction
    - [PCA](https://en.wikipedia.org/wiki/Principal_component_analysis) (Principal Component Analysis)
        - Find projection that maximizes the variance.
    - [Kernal PCA](https://en.wikipedia.org/wiki/Kernel_principal_component_analysis)
        - PCA using the [Kernel Trick](https://en.wikipedia.org/wiki/Kernel_method).
    - [MDS](https://en.wikipedia.org/wiki/Multidimensional_scaling) (Multidimensional Scaling)
        - Find projection that best preserves inter-point distances.
    - [LDA](https://en.wikipedia.org/wiki/Linear_discriminant_analysis) (Linear Discriminant Analysis)
        - Maximizing the component axes for class-separation.
    - [t-SNE](https://en.wikipedia.org/wiki/T-distributed_stochastic_neighbor_embedding) (t-distributed Stochastic Neighbor Embedding)
        - Non-linear dimensionality reduction technique mainly used for visualization of high-dimensional dataset/features.
        - Introduced by Van der Maaten, Laurens, and Geoffrey Hinton in "[Visualizing data using t-SNE](https://www.jmlr.org/papers/volume9/vandermaaten08a/vandermaaten08a.pdf)" Journal of machine learning research 9, no. 11 (2008).
    - [Autodencoder](https://en.wikipedia.org/wiki/Autoencoder)
        - Introduced by Hinton, Geoffrey E., and Ruslan R. Salakhutdinov. in "[Reducing the dimensionality of data with neural networks](https://www.science.org/doi/full/10.1126/science.1127647)" science 313, no. 5786 (2006): 504-507.

## Semi-supervised Learning

Use a small subset of labelled data with a large amount of unlabelled data for learning.

## Reinforcement Learning

- Q-learning
- SARSA