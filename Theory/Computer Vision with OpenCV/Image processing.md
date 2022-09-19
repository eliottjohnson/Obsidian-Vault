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

## Blending and Pasting Images

$pixel_{new}=\alpha\cdot pixel_{1} + \beta pixel_{2} + \gamma$

``` python
img1 = cv2.resize(img1,(1200,1200))
img2 = cv2.resize(img2,(1200,1200))

blended = cv2.addWeighted(src1=img1,alpha=0.8,src2=img2,beta=0.1, gamma=0.0) # Needs to be same size
```

## Overlay small image on top of larger image

``` python
x_offset = 0
y_offset = 0

x_end = x_offset + small_img.shape[1]
y_end = y_offset + small_img.shape[0]

large_img[y_offset:y_end, x_offset:x_end] = small_img
```

## Blend images of different sizes with mask

``` python
x_offset = img1.shape[1] - 600
y_offset = img1.shape[0] - 600

rows, cols, channels = img2.shape
roi = img1[y_offset:1401,x_offset:943]
plt.imshow(roi)

img2gray = cv2.cvtColor(img2, cv2.COLOR_RGB2GRAY) # Convert to grayscale
mask_inv = cv2.bitwise_not(img2gray) # Inverse the grayscale image

white_background = np.full(img2.shape,255,dtype=np.uint8)

bk = cv2.bitwise_or(white_background,white_background, mask=mask_inv) # Create mask for 3 color channel
fg = cv2.bitwise_or(img2,img2,mask=mask_inv) # Shines original image through the mask

final_roi = cv2.bitwise_or(roi,fg)

```

### Image Thresholding

Segmenting an image into different parts. Binary threshold

Read an image as grayscale:
```python
img = cv2.imread("../DATA/rainbow.jpg", 0) # The 0 variable loads the image as a grayscale
plt.imshow(img, cmap="gray")
```

Threshold an image:
```python
ret, thresh1 = cv2.threshold(img, 127, 255, cv2.THRESH_BINARY)
plt.imshow(thresh1, cmap="gray")
```

Other options of threshold:
* THRESH_BINARY_INV
* THRESH_TRUNC
* THRESH_TOZERO
* THRESH_TOZERO_INV

Function to show images with increased size:
``` python
def show_pic(img):
    fig = plt.figure(figsize=(15,15))
    ax = fig.add_subplot(111)
    ax.imshow(img, cmap="gray")
```