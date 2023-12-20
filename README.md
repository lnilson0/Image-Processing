# Image-Processing
Utilizes Python with OpenCV to process images using Sobel-Feldman operator, identifying outlines, making the images more easily identifiable for object recognition.

```
%pylab inline
import os, sys

from util.filters import filter_2d
from util.image import convert_to_grayscale
```

```
Kx = np.array([[1, 0, -1],
               [2, 0, -2],
               [1, 0, -1]])

Ky = np.array([[1, 2, 1],
               [0, 0, 0],
               [-1, -2, -1]])
```
