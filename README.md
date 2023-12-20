# Image-Processing
Utilizes Python with OpenCV to process images using Sobel-Feldman operator, identifying outlines, making the images more easily identifiable for object recognition.

```
%pylab inline
import os, sys

from util.filters import filter_2d
from util.image import convert_to_grayscale
```
Sobel kernels as numpy arrays:
```
Kx = np.array([[1, 0, -1],
               [2, 0, -2],
               [1, 0, -1]])

Ky = np.array([[1, 2, 1],
               [0, 0, 0],
               [-1, -2, -1]])
```
Import an image to work on:
```
im = imread(data_dir + 'data/easy/brick/brick_2.jpg')
gray = convert_to_grayscale(im/255.)
```
```
fig = figure(0, (8, 8))
imshow(gray, cmap = 'gray');
```
This is our starting image:
![image](https://github.com/lnilson0/Image-Processing/assets/128263527/0d94aec3-1fbb-4105-bc49-eaf81bacd5b6)
