# Matrix Operations: PyTorch vs NumPy

```python
import numpy as np
import torch.nn.functional as F
```


| Operations | NumPy | PyTorch |
| :--- | :--- | :--- |
| padding | [np.pad](https://numpy.org/doc/stable/reference/generated/numpy.pad.html) | [F.pad](https://pytorch.org/docs/stable/generated/torch.nn.functional.pad.html) |
| squeeze | [np.squeeze](https://numpy.org/doc/stable/reference/generated/numpy.squeeze.html) | [torch.squeeze](https://pytorch.org/docs/stable/generated/torch.squeeze.html) |
| transpose | [np.transpose](https://numpy.org/doc/stable/reference/generated/numpy.transpose.html) | [torch.transpose](https://pytorch.org/docs/stable/generated/torch.transpose.html) |
| in-place transpose | [x.T](https://numpy.org/doc/stable/reference/generated/numpy.ndarray.T.html) | [x.t](https://pytorch.org/docs/stable/generated/torch.Tensor.t.html) |
| permute | None | [torch.permute](https://pytorch.org/docs/stable/generated/torch.permute.html) |