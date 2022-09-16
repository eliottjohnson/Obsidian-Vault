# OpenCV

#### Opening an image
``` python
import cv2
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

img = cv2.imread("../DATA/dog_backpack.jpg")
plt.imshow(img)

```
#### Changing RGB order
```python
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### Flipping horizontally or vertically
```python
img_flip = np.flip(img_rgb, axis=0)
img_flip = cv2.flip(new_img, 0)
```
