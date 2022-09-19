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

### Adaptive threshold

```python
th2 = cv2.adaptiveThreshold(img, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, blockSize=11, C=8)
show_pic(th2)
```

## Blurring and smoothing

Blurring or smoothing is combined with edge detection algorithms.

Image kernel visualization: https://setosa.io/ev/image-kernels/
![[Pasted image 20220919111053.png]]

## Gamma correction - brightness

$\gamma<1$ will show brighter image

``` python

def load_img():
    img = cv2.imread("../DATA/bricks.jpg").astype(np.float32) / 255
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    return img
def display_img(img):
    fig = plt.figure(figsize=(12,10))
    ax = fig.add_subplot(111)
    ax.imshow(img)
    
img = load_img()
gamma = 1/4
result = np.power(img, gamma)
display_img(result)
```

## Low-pass filter with 2D convolution - Blurring -  Reducing noise

Write text on image:
``` python
font = cv2.FONT_HERSHEY_COMPLEX
cv2.putText(img, text="bricks",org=(10,600), fontFace=font, fontScale=10, color=(255,0,0), thickness=4)
```

You manually pass a kernel to an image

``` python
kernel = np.ones(shape=(5,5), dtype=np.float32)/25
dst = cv2.filter2D(img, -1, kernel) # Destination image
display_img(dst)

```

Built-in blur:
* Median blur is quite good for noise removal
``` python
blurred_img = cv2.blur(img,ksize=(10,10))
blurred_img = cv2.GaussianBlur(img, (5,5), 10)
blurred_img = cv2.medianBlur(img, 5) # Square kernel, takes 1D
blurred_img = cv2.bilateralFilter(img, 9, 75, 75)
```

## Morphological operators

Can also reduce noise. Reduce white points on black background or vice-verse.
Erosion or dilation effect.

Erosion, erodes boundaries of foreground objects.

``` python
kernel = np.ones((5,5),dtype=np.uint8)
result = cv2.erode(img, kernel, iterations=4)
```

### Opening (removes background noise)

Adding white noise
```python
white_noise = np.random.randint(low=0,high=2,size=(600,600))*255
noise_img = white_noise + img
```

![[Pasted image 20220919140229.png]]

Opening is erosion + dilation (useful for removing background noise)

```python
kernel = np.ones((5,5),dtype=np.uint8)
opening = cv2.morphologyEx(noise_img, cv2.MORPH_OPEN, kernel)
```

![[Pasted image 20220919140241.png]]
### Closing (removes foreground)

Black noise
```python
black_noise = np.random.randint(low=0, high=2, size=(600,600))*-255
noise_img = black_noise + img
noise_img[noise_img==-255]=0
```
![[Pasted image 20220919140927.png]]

Closing
```python
closing = cv2.morphologyEx(noise_img, cv2.MORPH_CLOSE, kernel)
```
![[Pasted image 20220919140920.png]]

# Gradient

Directional change in the intensity or color in an image.

Morphological gradient (takes the difference of the dilation and erosion of an image)
Crude form of edge detection.
![[Pasted image 20220919141305.png]]

### Sobel-Feldman Operators

Operator uses 2 - 3x3 kernels to approximate the derivates in H and V.

```python
sobelx = cv2.Sobel(img, cv2.CV_64F, 1,0, ksize=5) # Derivative in H, shows vertical lines
sobely = cv2.Sobel(img, cv2.CV_64F, 0,1, ksize=5) # Derivative in V, shows horizontal lines
laplacian = cv2.Laplacian(img, cv2.CV_64F) # Double derivative in both direction
```

# Color histogram

We can display the frequency of values for colors with three histograms.

We have to use BGR for histograms on OPENCV but RGB for displaying.
