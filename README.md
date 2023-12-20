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

And now, filter our image with  Kx  and  Ky  seperately. We'll call our filtered images  Gx  and  Gy.

```
Gx = filter_2d(gray, Kx)
Gy = filter_2d(gray, Ky)

Gx
```
Output: 
```
array([[-0.00784314,  0.        ,  0.00392157, ...,  0.01960784,
         0.        , -0.01176471],
       [-0.00392157,  0.00392157,  0.01176471, ...,  0.01960784,
         0.        , -0.00784314],
       [ 0.        ,  0.00784314,  0.01176471, ...,  0.01176471,
         0.00392157,  0.00784314],
       ...,
       [ 0.00784314, -0.00784314, -0.01176471, ...,  0.        ,
         0.        , -0.01176471],
       [ 0.00784314, -0.00784314, -0.00392157, ...,  0.        ,
         0.        , -0.01176471],
       [ 0.00392157, -0.00392157,  0.        , ...,  0.        ,
         0.        , -0.00392157]])
```
Show image after applying these filters: 
```
fig = figure(0, (16, 8))
fig.add_subplot(1,2,1)
imshow(Gx)
title('$G_x$');

fig.add_subplot(1,2,2)
imshow(Gy)
title('$G_y$');
```

![image](https://github.com/lnilson0/Image-Processing/assets/128263527/2c5e9f3c-93fc-472b-b516-b1bb9f6ea82a)


This is an estimate of the gradient of our images in the x and y direction.
For the next step we estimate the overall gradient for each pixel in our images.
The overall gradient combines x and y direction, and gives positive whenever there is a edge.
We do this by taking the gradient magnitude:

$$
\mathbf{G} = \sqrt{ {\mathbf{G}_x}^2 + {\mathbf{G}_y}^2 }
$$


Compute Gradient Magnitude:
```
G = np.sqrt(Gx**2+Gy**2)
```

