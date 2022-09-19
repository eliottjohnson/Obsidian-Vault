# OpenCV Basic

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

#### Draw an empty red rectangle on an image
```python
cv2.rectangle(img_rgb,pt1=(200,380),pt2=(600,700),color=(255,0,0),thickness=10)
```

#### Draw a polyline
```python
vertices = np.array([[250,700],[425,400],[600,700]])
pts = vertices.reshape((-1,1,2))
cv2.polylines(img_rgb,[pts], isClosed=True, color=(0,0,255), thickness=20)
```

#### Fill a polygon
```python
vertices = np.array([[250,700],[425,400],[600,700]])
pts = vertices.reshape((-1,1,2))
cv2.fillPoly(img_rgb,[pts], color=(0,0,255))
```
