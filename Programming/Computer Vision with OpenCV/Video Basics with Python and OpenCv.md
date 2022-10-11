# Video Basics with Python and OpenCV

## Using video file

```python
import cv2
import time

cap = cv2.VideoCapture("../DATA/finger_move.mp4")

if cap.isOpened() == False:
  print("ERROR FILE NOT FOUND OR WRONG CODEC USED !")

while cap.isOpened():
  ret, frame = cap.read()
    
  if ret == True:
    
    time.sleep(1/60)
    cv2.imshow("frame", frame)
     
    if cv2.waitKey(10) & 0xFF == 27:
      break
  else:
    break

cap.realease()
cv2.destroyAllWindows()
```

# Drawing on Live Camera

This draws a fixed rectangle on the video.
```python
import cv2
import time

cap = cv2.VideoCapture("../DATA/finger_move.mp4")

width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))

# TOP LEFT CORNER
x = width // 2
y = height // 2

# width and height of RECTANGLE
w = width // 4
h = height // 4

# BOTTOM RIGHT x + w, y + h

while True:

  ret, frame = cap.read()
  
  cv2.rectangle(frame, (x,y),(x+w, y+h), color=(0,0,255), thickness=4)
  cv2.imshow("frame",frame)
      
  if cv2.waitKey(10) & 0xFF == 27:
    break

cap.realease()
cv2.destroyAllWindows()
```

### Interactively draw on video

Draw a rectangle while the video is playing by clicking with the mouse.
```python
import cv2
import time

## CALLBACK FUNCTION RECTANGLE

def draw_rectangle(event, x,y, flags, param):

  global pt1, pt2, topLeft_clicked, botRight_clicked
  
  if event == cv2.EVENT_LBUTTONDOWN:
  
    # Reset the rectangle (it checks if the rect is there)
    if topLeft_clicked and botRight_clicked:
      pt1 = (0,0)
      pt2 = (0,0)
      topLeft_clicked = False
      botRight_clicked = False
    if topLeft_clicked == False:
      pt1 = (x,y)
      topLeft_clicked = True
    elif botRight_clicked == False:
      pt2 = (x,y)
      botRight_clicked = True
  
## GLOBAL VARIABLES

pt1 = (0,0)
pt2 = (0,0)
topLeft_clicked = False
botRight_clicked = False

## CONNECT TO CALLBACK
cap = cv2.VideoCapture("../DATA/finger_move.mp4")

cv2.namedWindow("Test")
cv2.setMouseCallback("Test", draw_rectangle)

while True:

  ret, frame = cap.read()

  # Drawing on the FRAME based on global variables
  if topLeft_clicked:
    cv2.circle(frame, center=pt1, radius=5, color=(0,0,255), thickness=-1)
  if topLeft_clicked and botRight_clicked:
    cv2.rectangle(frame, pt1, pt2, (0,0,255), 3)
    
  
  cv2.imshow("Test",frame)
      
  if cv2.waitKey(10) & 0xFF == 27:
    break

cap.realease()
cv2.destroyAllWindows()
```