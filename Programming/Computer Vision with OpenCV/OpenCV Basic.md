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

## Draw circles on image by dragging mouse
Only works as a script
```python
import cv2
import numpy as np

# VARIABLES

# True while mouse button down, False while mouse button up
drawing = False
ix,iy = -1,-1

# FUNCTION
def draw_rectangle(event, x,y, flags, param):

  global ix,iy,drawing
  
  if event == cv2.EVENT_LBUTTONDOWN:
    drawing = True
    ix,iy = x,y
    
  elif event == cv2.EVENT_MOUSEMOVE:
    if drawing == True:
      cv2.circle(img, (ix,iy), int(np.sqrt(abs(x-ix)**2+abs(y-iy)**2)), (0,0,255), -1)
  
  elif event == cv2.EVENT_LBUTTONUP:
    drawing = False

cv2.namedWindow(winname="my_drawing")
cv2.setMouseCallback("my_drawing", draw_rectangle)

# SHOWING IMAGE WITH OPENCV
img = cv2.imread("../DATA/dog_backpack.png")
#img = np.zeros((512,1024,3))
while True:
  cv2.imshow("my_drawing",img)  
  if cv2.waitKey(1) & 0xFF == 27:
    break

cv2.destroyAllWindows()
```