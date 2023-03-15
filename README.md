# Multiple Comparisons Tutorial

`condensed_version/MultComp.py` contains almost everything you need.

## How to use it
Here is a sample fingerprint, containing five fingerprints and six feature on each. 
**1** is on-bit, meaning having a feature.
**0** is off-bit, meaning not having a feature.

$$ F_1 = \begin{bmatrix} 0 & 1 & 0 & 0 & 1 & 0 \end{bmatrix}$$

$$ F_2 = \begin{bmatrix} 1 & 0 & 1 & 1 & 0 & 1 \end{bmatrix}$$

$$ F_3 = \begin{bmatrix} 1 & 0 & 0 & 0 & 1 & 1 \end{bmatrix}$$

$$ F_4 = \begin{bmatrix} 1 & 1 & 0 & 1 & 1 & 1 \end{bmatrix}$$

$$ F_5 = \begin{bmatrix} 0 & 1 & 1 & 0 & 1 & 1 \end{bmatrix}$$

The basis of extended similarity relies on the values of column-wise sums. 
```
from MultComp import *
import numpy as np

data = np.array([[0, 1, 0, 0, 1, 0], [1, 0, 1, 1, 0, 1], [1, 0, 0, 0, 1, 1], \
                [1, 1, 0, 1, 1, 1], [0, 1, 1, 0, 1, 1]])
column_sum = np.sum(data, axis=0)
n_fingerprints = len(column_sum)
data_sets = np.array([np.append(column_sum, n_fingerprints)])
dict = calculate_counters(data_sets, c_threshold=None, w_factor="fraction")
print(dict)
```
