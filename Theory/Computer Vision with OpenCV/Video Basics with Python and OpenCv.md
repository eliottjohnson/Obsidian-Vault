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