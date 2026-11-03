# EXP.4-RECORD-IMAGE-TRANSFORMATIONS

## AIM

To write a Python program using OpenCV to perform various image transformations such as translation, scaling, shearing, reflection, rotation, and cropping.

The program performs the following operations:

- Read and display the original image.
- Perform image translation by shifting the image horizontally and vertically.
- Apply image scaling to resize the image.
- Perform image shearing in both horizontal and vertical directions.
- Apply image reflection using flipping.
- Rotate the image by 45 degrees.
- Crop a specific portion of the image.

## SOFTWARE REQUIRED

Anaconda – Python 3.7  
Jupyter Notebook / VS Code  
OpenCV (cv2)  
NumPy  
Matplotlib

## ALGORITHM

**Step 1:**

Import the required libraries: OpenCV, NumPy, and Matplotlib.

**Step 2:**

Read the input image `Image.png` using OpenCV.

**Step 3:**

Display the original image using Matplotlib after converting the BGR image into RGB format.

**Step 4:**

Perform image translation by creating a translation matrix with horizontal shift of 100 pixels and vertical shift of 50 pixels.

**Step 5:**

Apply image scaling using `cv2.resize()` with scaling factors of 5.0 and 2.0.

**Step 6:**

Perform image shearing by creating a shearing matrix with a factor of 0.5 in both horizontal and vertical directions.

**Step 7:**

Perform image reflection using `cv2.flip()`.

**Step 8:**

Perform image rotation by 45 degrees using `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`.

**Step 9:**

Perform image cropping by selecting a specific region from the original image using array slicing.

**Step 10:**

Display all the transformed images using Matplotlib.

## PROGRAM

**Developed By**

## Name: Rubasri R
## Register No: 212224240139

### 1. Import the Required Libraries and Read the Image

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('Image.png')

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')
```

**OUTPUT:**

<img width="348" height="413" alt="Screenshot 2026-10-30 160311" src="https://github.com/user-attachments/assets/dfe3b512-fe3e-45c9-8377-708adf0479c7" />


### 2. Perform Image Translation

```python
tx, ty = 100, 50

M_translation = np.float32([[1, 0, tx], [0, 1, ty]])

translated_image = cv2.warpAffine(
    image, M_translation,
    (image.shape[1], image.shape[0])
)

plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))
plt.title("Translated Image")
plt.axis('off')
```

**OUTPUT:**

<img width="368" height="413" alt="image" src="https://github.com/user-attachments/assets/e7e65e20-cf3c-4133-af19-644eebfa7455" />


### 3. Perform Image Scaling

```python
fx, fy = 5.0, 2.0

scaled_image = cv2.resize(
    image, None, fx=fx, fy=fy,
    interpolation=cv2.INTER_LINEAR
)

plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))
plt.title("Scaled Image")
plt.axis('off')
```

**OUTPUT:**

<img width="560" height="304" alt="image" src="https://github.com/user-attachments/assets/bfd06f0b-f839-4977-9815-6175ce322b67" />

### 4. Perform Image Shearing

```python
shear_matrix = np.float32([
    [1, 0.5, 0],
    [0.5, 1, 0]
])

sheared_image = cv2.warpAffine(
    image, shear_matrix,
    (image.shape[1], image.shape[0])
)

plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))
plt.title("Sheared Image")
plt.axis('off')
```

**OUTPUT:**

<img width="365" height="423" alt="image" src="https://github.com/user-attachments/assets/eb43c5ff-2062-447b-bd4e-192f234443d0" />


### 5. Perform Image Reflection

```python
reflected_image = cv2.flip(image, 2)

plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))
plt.title("Reflected Image")
plt.axis('off')
```

**OUTPUT:**

<img width="346" height="411" alt="image" src="https://github.com/user-attachments/assets/d93ee96b-d677-4c8e-90d5-805d388bb595" />


### 6. Perform Image Rotation

```python
(height, width) = image.shape[:2]

angle = 45

center = (width // 2, height // 2)

M_rotation = cv2.getRotationMatrix2D(center, angle, 1)

rotated_image = cv2.warpAffine(
    image, M_rotation, (width, height)
)

plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))
plt.title("Rotated Image")
plt.axis('off')
```

**OUTPUT:**

<img width="394" height="407" alt="image" src="https://github.com/user-attachments/assets/7ac65e24-1490-41eb-abf1-6f1d589a6d6d" />


### 7. Perform Image Cropping

```python
x, y, w, h = 200, 200, 250, 200

cropped_image = image[y:y+h, x:x+w]

plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))
plt.title("Cropped Image")
plt.axis('off')
```

**OUTPUT:**

<img width="540" height="421" alt="image" src="https://github.com/user-attachments/assets/c6aa4fa3-50b9-47dc-8c31-42a8b45947cb" />


## RESULT

Thus, various image transformations such as translation, scaling, shearing, reflection, rotation, and cropping are successfully performed using OpenCV. The transformations demonstrate how images can be modified and manipulated for different image processing applications.
