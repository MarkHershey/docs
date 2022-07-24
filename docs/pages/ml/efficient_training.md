# Tips on Efficient Deep Learning Model Training

## References

- [Faster Deep Learning Training with PyTorch – a 2021 Guide](https://efficientdl.com/faster-deep-learning-in-pytorch-a-guide/#1-consider-using-another-learning-rate-schedule)
- [[D] Here are 17 ways of making PyTorch training faster – what did I miss?](https://www.reddit.com/r/MachineLearning/comments/kvs1ex/d_here_are_17_ways_of_making_pytorch_training/)
- [Efficient PyTorch — Eliminating Bottlenecks](https://towardsdatascience.com/efficient-pytorch-part-1-fe40ed5db76c)
- [模型训练太慢？显存不够？这个方法让你的GPU联手CPU](https://zhuanlan.zhihu.com/p/257895005)
- [Efficient-PyTorch](https://github.com/Lyken17/Efficient-PyTorch)


## Data Formats

- [npz](https://numpy.org/doc/stable/reference/generated/numpy.savez.html)
- pickle
- joblib
- hdf5
- npz_compress
- pickle_compress
- joblib_compress
- hdf5_compress
- [Lightning Memory-Mapped Database Manager (LMDB)](http://www.lmdb.tech/doc/)

## Find the Bottleneck

- [TORCH.PROFILER](https://pytorch.org/docs/stable/profiler.html)
- [PYTORCH PROFILER](https://pytorch.org/tutorials/recipes/recipes/profiler_recipe.html)