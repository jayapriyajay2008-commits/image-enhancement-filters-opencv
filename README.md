# Image Smoothing and Sharpening Using OpenCV

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

##  Developed By

- **Name:** Jayapriya P 
- **Register No:** 212225040144
## program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1 & 2: Read the input image
image = cv2.imread('632130435-8c11f193-adfd-42d8-8791-c7ae123456.jpg')

# Check if image is loaded
if image is None:
    print("Error: Image not found. Check the image name.")
else:

    # Step 3: Convert BGR to RGB for display
    rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

    # Step 4: Averaging Filter
    averaging = cv2.blur(image, (5, 5))

    # Step 5: Weighted Averaging Filter
    kernel = np.array([
        [1, 2, 1],
        [2, 4, 2],
        [1, 2, 1]
    ], dtype=np.float32) / 16

    weighted = cv2.filter2D(image, -1, kernel)

    # Step 6: Gaussian Filter
    gaussian = cv2.GaussianBlur(image, (5, 5), 0)

    # Step 7: Median Filter
    median = cv2.medianBlur(image, 5)

    # Step 8: Laplacian Sharpening using Kernel
    laplacian_kernel = np.array([
        [0, -1, 0],
        [-1, 5, -1],
        [0, -1, 0]
    ])

    sharpened = cv2.filter2D(image, -1, laplacian_kernel)

    # Step 9: Convert to grayscale and apply Laplacian
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    laplacian = cv2.Laplacian(gray, cv2.CV_64F)
    laplacian = np.uint8(np.absolute(laplacian))

    # Step 10: Display all images
    plt.figure(figsize=(12, 8))

    plt.subplot(2, 4, 1)
    plt.imshow(rgb)
    plt.title('Original Image')
    plt.axis('off')

    plt.subplot(2, 4, 2)
    plt.imshow(cv2.cvtColor(averaging, cv2.COLOR_BGR2RGB))
    plt.title('Averaging Filter')
    plt.axis('off')

    plt.subplot(2, 4, 3)
    plt.imshow(cv2.cvtColor(weighted, cv2.COLOR_BGR2RGB))
    plt.title('Weighted Averaging')
    plt.axis('off')

    plt.subplot(2, 4, 4)
    plt.imshow(cv2.cvtColor(gaussian, cv2.COLOR_BGR2RGB))
    plt.title('Gaussian Filter')
    plt.axis('off')

    plt.subplot(2, 4, 5)
    plt.imshow(cv2.cvtColor(median, cv2.COLOR_BGR2RGB))
    plt.title('Median Filter')
    plt.axis('off')

    plt.subplot(2, 4, 6)
    plt.imshow(cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB))
    plt.title('Laplacian Sharpening')
    plt.axis('off')

    plt.subplot(2, 4, 7)
    plt.imshow(laplacian, cmap='gray')
    plt.title('Laplacian Operator')
    plt.axis('off')

    plt.tight_layout()
    plt.show()
```
---

##  Output
### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively
  i)Using Averaging Filter
  ```
  import cv2
import matplotlib.pyplot as plt
import numpy as np
image1=cv2.imread("spider.png")
image2=cv2.cvtColor(image1,cv2.COLOR_BGR2RGB)
kernel=np.ones((11,11),np.float32)/169
image3=cv2.filter2D(image2,-1,kernel)
plt.figure(figsize=(9,9))
plt.subplot(1,2,1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(image3)
plt.title("Average Filter Image")
plt.axis("off")
plt.show()
```
<img width="1093" height="357" alt="image" src="https://github.com/user-attachments/assets/5bfb543c-e04c-4f7d-a6ca-0b3b98053c68" />

ii)Using Weighted Averaging Filter
```
kernel1=np.array([[1,2,1],[2,4,2],[1,2,1]])/16
image3=cv2.filter2D(image2,-1,kernel1)
plt.imshow(image3)
plt.title("Weighted Average Filter Image")
plt.axis("off")
plt.show()
```
<img width="784" height="472" alt="image" src="https://github.com/user-attachments/assets/057c5717-b18d-4c2b-ae3c-2fb5513cf3b6" />
iii)Using Gaussian Filter
```
gaussian_blur=cv2.GaussianBlur(image2,(33,33),0,0)
plt.imshow(gaussian_blur)
plt.title("Gaussian Blur")
plt.axis("off")
plt.show()
```
<img width="771" height="479" alt="image" src="https://github.com/user-attachments/assets/5c3dbd12-1346-4752-969d-f1277dffad72" />
iv)Using Median Filter
```
median=cv2.medianBlur(image2,13)
plt.title("Median Blur")
plt.axis("off")
plt.show()
```
<img width="719" height="411" alt="image" src="https://github.com/user-attachments/assets/574d6d7c-1432-41be-8429-2e94c0da661d" />

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  
```
kernel2=np.array([[-1,-1,-1],[2,-2,1],[2,1,-1]])
image3=cv2.filter2D(image2,-1,kernel2)
plt.imshow(image3)
plt.title("Laplacian Kernel")
plt.axis("off")
plt.show()
```
<img width="769" height="467" alt="image" src="https://github.com/user-attachments/assets/f9441839-7869-4991-a5f8-f6486e971ed3" />
ii) Using Laplacian Operator
```
laplacian=cv2.Laplacian(image2,cv2.CV_64F)
plt.imshow(laplacian)
plt.title("Laplacian Operator")
plt.axis("off")
plt.show()
```
<img width="1058" height="329" alt="image" src="https://github.com/user-attachments/assets/033115d6-edb3-49f2-99fd-58f642694929" />
---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
