# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** ASHWIN BAALAJI V K
- **Register No:** 212225230026 

---
## PROGRAM
###  Sobel Edge Detector
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel = cv2.convertScaleAbs(cv2.magnitude(sobel_x, sobel_y))

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(sobel, cmap="gray")
plt.title("Sobel Edge Detector")
plt.axis("off")
plt.show()
```
###  Prewitt Edge Detector
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

kernel_x = np.array([[-1, 0, 1],
                     [-1, 0, 1],
                     [-1, 0, 1]], dtype=np.float64)
kernel_y = np.array([[ 1,  1,  1],
                     [ 0,  0,  0],
                     [-1, -1, -1]], dtype=np.float64)

prewitt_x = cv2.filter2D(gray, cv2.CV_64F, kernel_x)
prewitt_y = cv2.filter2D(gray, cv2.CV_64F, kernel_y)
prewitt = cv2.convertScaleAbs(cv2.magnitude(prewitt_x, prewitt_y))

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(prewitt, cmap="gray")
plt.title("Prewitt Edge Detector")
plt.axis("off")
plt.show()
```
###  Roberts Edge Detector
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

kernel_x = np.array([[1,  0],
                     [0, -1]], dtype=np.float64)
kernel_y = np.array([[ 0, 1],
                     [-1, 0]], dtype=np.float64)

roberts_x = cv2.filter2D(gray, cv2.CV_64F, kernel_x)
roberts_y = cv2.filter2D(gray, cv2.CV_64F, kernel_y)
roberts = cv2.convertScaleAbs(cv2.magnitude(roberts_x, roberts_y))

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(roberts, cmap="gray")
plt.title("Roberts Edge Detector")
plt.axis("off")
plt.show()
```
###  Laplacian Edge Detector
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

laplacian = cv2.convertScaleAbs(cv2.Laplacian(gray, cv2.CV_64F, ksize=3))

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(laplacian, cmap="gray")
plt.title("Laplacian Edge Detector")
plt.axis("off")
plt.show()
```
###  Canny Edge Detector
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("Downloads/WALT.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

canny = cv2.Canny(gray, 100, 200)

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(canny, cmap="gray")
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
```
## Output

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map
<img width="1047" height="497" alt="Screenshot 2026-11-17 084908" src="https://github.com/user-attachments/assets/ae624d41-ac42-4f42-997e-8ad0db1d564b" />


###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges
<img width="1090" height="493" alt="Screenshot 2026-11-17 084917" src="https://github.com/user-attachments/assets/86c4b31c-36d9-4094-b351-534ed88b1e48" />


###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise
<img width="1028" height="492" alt="Screenshot 2026-11-17 084923" src="https://github.com/user-attachments/assets/92b1ec3c-b194-4615-a162-07be80fe4330" />


###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes
<img width="1031" height="492" alt="Screenshot 2026-11-17 084928" src="https://github.com/user-attachments/assets/1a3ec02d-9ab9-4126-a91d-24839fa9859f" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges
<img width="1060" height="492" alt="Screenshot 2026-11-17 084936" src="https://github.com/user-attachments/assets/473fa783-48db-455e-86d0-c7652f0beef6" />


---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
