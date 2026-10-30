# Record-Implementation-of-Filters-Image-Smoothing-and-Sharpening-Using-OpenCV-

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---
## Program
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read Image
img = cv2.imread("image.jpg")

if img is None:
    print("Image not found!")
    exit()

# Convert to RGB
rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Averaging Filter
average = cv2.blur(rgb, (5,5))

# Weighted Averaging Filter
kernel = np.array([[1,2,1],
                   [2,4,2],
                   [1,2,1]], dtype=np.float32)
kernel = kernel / kernel.sum()
weighted = cv2.filter2D(rgb, -1, kernel)

# Gaussian Filter
gaussian = cv2.GaussianBlur(rgb, (5,5), 0)

# Median Filter
median = cv2.medianBlur(rgb, 5)

# Laplacian Sharpening Kernel
sharp_kernel = np.array([[0,-1,0],
                         [-1,5,-1],
                         [0,-1,0]])
lap_kernel = cv2.filter2D(rgb, -1, sharp_kernel)

# Laplacian Operator
gray = cv2.cvtColor(rgb, cv2.COLOR_RGB2GRAY)
lap_operator = cv2.Laplacian(gray, cv2.CV_64F)
lap_operator = np.uint8(np.absolute(lap_operator))

# Display Images
plt.figure(figsize=(15,10))

plt.subplot(2,4,1)
plt.imshow(rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(2,4,2)
plt.imshow(average)
plt.title("Average Filter")
plt.axis("off")

plt.subplot(2,4,3)
plt.imshow(weighted)
plt.title("Weighted Average")
plt.axis("off")

plt.subplot(2,4,4)
plt.imshow(gaussian)
plt.title("Gaussian Filter")
plt.axis("off")

plt.subplot(2,4,5)
plt.imshow(median)
plt.title("Median Filter")
plt.axis("off")

plt.subplot(2,4,6)
plt.imshow(lap_kernel)
plt.title("Laplacian Kernel")
plt.axis("off")

plt.subplot(2,4,7)
plt.imshow(lap_operator, cmap="gray")
plt.title("Laplacian Operator")
plt.axis("off")

plt.tight_layout()
plt.show()
```

##  Developed By

- **Name: JINITH KUMAR V** 
- **Register No: 212225040157** 

---

##  Output
<img width="337" height="473" alt="image" src="https://github.com/user-attachments/assets/ebb48daa-93a7-4c98-84d1-4aae193beeca" />

### Smoothing Filters

- Averaging filter produces blurred image
<img width="341" height="470" alt="image" src="https://github.com/user-attachments/assets/b153a867-06cc-4d6a-8f27-e4b18ae3f470" />

- Weighted averaging provides smoother result with less distortion
<img width="342" height="467" alt="image" src="https://github.com/user-attachments/assets/2f6a2329-1b5a-45c8-97fd-9b84e0a99288" />

- Gaussian filter preserves edges better while reducing noise
<img width="343" height="471" alt="image" src="https://github.com/user-attachments/assets/21c1062f-bc8d-4964-a7e3-fa6fcf8467ad" />

- Median filter removes salt-and-pepper noise effectively
<img width="338" height="470" alt="image" src="https://github.com/user-attachments/assets/06ad101c-9055-4ab1-824d-70f452382bd0" />


###  Sharpening Filters

- Laplacian kernel enhances edges and fine details
<img width="337" height="467" alt="image" src="https://github.com/user-attachments/assets/16ec21b9-57a1-4103-89b3-9946e0d86cef" />

- Laplacian operator detects edges clearly in grayscale  
<img width="347" height="470" alt="image" src="https://github.com/user-attachments/assets/9dfdb82c-27c2-4cc3-be96-e6663849a363" />

---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
