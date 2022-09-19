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

