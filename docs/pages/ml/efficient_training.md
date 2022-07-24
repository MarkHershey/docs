# Tips on Efficient Deep Learning Model Training

## References

- [Faster Deep Learning Training with PyTorch – a 2021 Guide](https://efficientdl.com/faster-deep-learning-in-pytorch-a-guide/#1-consider-using-another-learning-rate-schedule)
- [[D] Here are 17 ways of making PyTorch training faster – what did I miss?](https://www.reddit.com/r/MachineLearning/comments/kvs1ex/d_here_are_17_ways_of_making_pytorch_training/)
- [Efficient PyTorch — Eliminating Bottlenecks](https://towardsdatascience.com/efficient-pytorch-part-1-fe40ed5db76c)
- [模型训练太慢？显存不够？这个方法让你的GPU联手CPU](https://zhuanlan.zhihu.com/p/257895005)
- [Lyken17's tips: Efficient-PyTorch](https://github.com/Lyken17/Efficient-PyTorch)


## Data Persistence Storage

- [NumPy uncompressed .npz](https://numpy.org/doc/stable/reference/generated/numpy.savez.html)
- [NumPy compressed .npz](https://numpy.org/doc/stable/reference/generated/numpy.savez_compressed.html)
- [Python pickle](https://docs.python.org/3/library/pickle.html)
- [Python pickle w/ compression](https://docs.python.org/3/library/archiving.html)
- [Joblib](https://joblib.readthedocs.io/en/latest/persistence.html)
- [Compressed Joblib](https://joblib.readthedocs.io/en/latest/persistence.html#compressed-joblib-pickles)
- [HDF5](https://docs.h5py.org/en/latest/index.html)
- [HDF5 w/ compression](https://docs.h5py.org/en/latest/high/dataset.html?highlight=compress#filter-pipeline)
- [Lightning Memory-Mapped Database Manager (LMDB)](https://github.com/jnwatson/py-lmdb)


## DP & DDP

TODO


## Find the Bottleneck

- [TORCH.PROFILER API](https://pytorch.org/docs/stable/profiler.html)
- [PYTORCH PROFILER Tutorial](https://pytorch.org/tutorials/recipes/recipes/profiler_recipe.html)