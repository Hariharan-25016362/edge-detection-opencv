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

- **Name:** Ajayprabu.A
- **Register No:** 212225220005

---

## Output
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread("C:\\Users\\manas\\OneDrive\\Desktop\\Manasa\\image.jpg") 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
<img width="836" height="448" alt="image" src="https://github.com/user-attachments/assets/326cfb3b-98a2-44ff-a838-e7534bfbb90c" />

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```
<img width="797" height="427" alt="image" src="https://github.com/user-attachments/assets/cb018585-f39d-4607-a68d-981e3118a6ca" />

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges
```
image = cv2.imread("C:\\Users\\manas\\OneDrive\\Desktop\\Manasa\\image.jpg") 

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

plt.imshow(canny_edges, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
```
<img width="757" height="420" alt="image" src="https://github.com/user-attachments/assets/3b4a3607-d6f9-45a8-881a-2ac64f6c93c2" />


###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  
```
import cv2
import matplotlib.pyplot as plt
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
laplacian_8bit = cv2.convertScaleAbs(laplacian)
plt.imshow(laplacian_8bit, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```
<img width="712" height="397" alt="image" src="https://github.com/user-attachments/assets/38b90a50-cba2-4c62-b8a9-5312dc106599" />

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes
```
import cv2
import matplotlib.pyplot as plt
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
laplacian_8bit = cv2.convertScaleAbs(laplacian)
plt.imshow(laplacian_8bit, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```
<img width="712" height="397" alt="image" src="https://github.com/user-attachments/assets/38b90a50-cba2-4c62-b8a9-5312dc106599" />

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  
```
import cv2
import matplotlib.pyplot as plt
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```
<img width="673" height="403" alt="image" src="https://github.com/user-attachments/assets/a3107607-e385-475a-829e-dba100ad97c8" />

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
