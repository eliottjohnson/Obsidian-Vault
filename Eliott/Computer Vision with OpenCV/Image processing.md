# Image processing

See [[OpenCV Basic]] for basic image opening

## Color Mappings
HSL and HSV are human vision color space (different from RGB).

**RGB** is a combination of Red Green and Blue.
![[Pasted image 20220916133942.png]]
**HSL** Cylinder Model (Hue, Saturation, Lightness)
![[Pasted image 20220916133900.png]]

**HSV** (Hue, Saturation, Value)
![[Pasted image 20220916133917.png]]

### Change color space
``` python
import cv2
import matplotlib.pyplot as plt
% matplotlib inline

img = cv2.imread("DATA/00-puppy.jpg")

img = cv2.cvtColor(img,cv2.COLOR_BGR2RGB) # Convert to RGB
img = cv2.cvtColor(img,cv2.COLOR_BGR2HSV) # Convert to HSV
img = cv2.cvtColor(img,cv2.COLOR_BGR2HSL) # Convert to HSL

plt.imshow(img)
```
