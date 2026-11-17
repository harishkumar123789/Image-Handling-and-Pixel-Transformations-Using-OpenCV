
# Experiment 1: Basic Image Processing Using OpenCV
### Name : HARISH KUMAR S
### Reg no: 212224230091

## AIM

To perform basic image-processing operations on an input image using
Python and OpenCV, including drawing shapes and text, color-space
conversion, pixel modification, resizing, cropping, flipping, and saving
the processed image.

## Input Image

<img width="1086" height="1448" alt="hari" src="https://github.com/user-attachments/assets/bb68172c-5dae-4c12-8c43-2a296bf95d5a" />





## PROCEDURE

1.  Import the required libraries: OpenCV (`cv2`) and Matplotlib
    (`matplotlib.pyplot`).
2.  Read the input image `Qno. 1.jpg` from the local directory using
    `cv2.imread()`.
3.  Convert the image from BGR to RGB format and display the original
    image.
4.  Draw a line from the top-left to the bottom-right of the image.
5.  Draw a circle at the center of the image, draw a rectangle around
    the image, and add the text **OpenCV Drawing**.
6.  Convert the RGB image into HSV, grayscale, and YCrCb color spaces
    and display each result.
7.  Convert the HSV image back into RGB format and display it.
8.  Access the pixel at coordinate `(100, 100)` and print its value.
    Modify the required pixel or region to white.
9.  Resize the original image to half its width and height.
10. Crop a region of interest (ROI) from the image and display it.
11. Flip the original image horizontally and vertically and display both
    results.
12. Save the final processed image using `cv2.imwrite()`.



## PROGRAM

### 1. Import Libraries and Display Original Image

```python
import cv2
import matplotlib.pyplot as plt

# Read the image
img = cv2.imread('hari.jpeg', cv2.IMREAD_COLOR)

# Convert BGR to RGB
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display original image
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()
```

### 2. Drawing a Line

```python
image = cv2.imread('hari.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

line_img = cv2.line(img_rgb, (0, 0), (900, 1200), (255, 0, 0), 10)

plt.imshow(line_img)
plt.title("Image with Line")
plt.axis('off')
plt.show()
```

### 3. Drawing a Circle

```python
image = cv2.imread('hari.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

circle_img = cv2.circle(img_rgb, (450, 400), 250, (255, 0, 0), 10)

plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis('off')
plt.show()
```

### 4. Drawing a Rectangle

```python
image = cv2.imread('hari.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

rectangle_img = cv2.rectangle(img_rgb, (100, 50), (750, 600), (0, 0, 255), 10)

plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()
```

### 5. Adding Text to Image

```python
image = cv2.imread('hari.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

text_img = cv2.putText(
    img_rgb,
    "OpenCV Drawing",
    (10, 30),
    cv2.FONT_HERSHEY_SIMPLEX,
    1,
    (0, 0, 0),
    10
)

plt.imshow(text_img)
plt.title("Image with Text")
plt.axis('off')
plt.show()
```

### 6. Color Space Conversion

```python
image = cv2.imread('hari.jpeg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
plt.show()

# RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
plt.show()

# RGB to Grayscale
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

# RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
plt.show()

# HSV to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
plt.show()
```

### 7. Pixel Transformation

```python
image = cv2.imread('hari.jpeg')

# Modify pixel region to white
image[200:600, 200:800] = [255, 255, 255]

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Modified Image")
plt.axis("off")
plt.show()
```

### 8. Resizing Image

```python
image = cv2.imread('hari.jpeg')

print(image.shape)

# Resize image to half size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))

resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

print(resized_image_rgb.shape)

plt.imshow(resized_image_rgb)
plt.title("Resized Image")
plt.axis("off")
plt.show()
```

### 9. Cropping Image (ROI)

```python
image = cv2.imread('hari.jpeg')

print(image.shape)

# Crop a region of interest
roi = image[50:350, 50:350]

roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest")
plt.axis("off")
plt.show()
```

### 10. Horizontal Flip

```python
image = cv2.imread('hari.jpeg')

flipped_horizontally = cv2.flip(image, 1)

flipped_horizontally_rgb = cv2.cvtColor(
    flipped_horizontally, cv2.COLOR_BGR2RGB
)

plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()
```

### 11. Vertical Flip

```python
flipped_vertically = cv2.flip(image, 0)

flipped_vertically_rgb = cv2.cvtColor(
    flipped_vertically, cv2.COLOR_BGR2RGB
)

plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
plt.show()
```

### 12. Saving Processed Image

```python
cv2.imwrite("hari.jpeg", image)

print("Image saved successfully")
```


## OUTPUT

The following outputs are obtained after executing the program:

### 1.  Original input image displayed.

<img width="1086" height="1448" alt="hari" src="https://github.com/user-attachments/assets/e265e21b-8ab4-4190-97d0-bdb0101b9256" /><img width="299" height="393" alt="Screenshot 2026-11-17 224539" src="https://github.com/user-attachments/assets/f21ea45d-3133-4fb0-968d-88f52d01cfcd" />



### 2.  Image with a diagonal line drawn from top-left to bottom-right.

<img width="281" height="390" alt="Screenshot 2026-11-17 224544" src="https://github.com/user-attachments/assets/33eda77f-3186-4b3b-819e-f9e4761c679a" />



### 3.  Image with a circle at its center.

<img width="274" height="396" alt="Screenshot 2026-11-17 224548" src="https://github.com/user-attachments/assets/0ac6206f-511c-466f-94b0-ddb6bb19786b" />


### 4.  Image with a rectangular border.

<img width="298" height="395" alt="Screenshot 2026-11-17 224550" src="https://github.com/user-attachments/assets/6e742492-fc7f-4ee5-809f-095d01007267" />



### 5.  Image displaying the text **OpenCV Drawing**.

<img width="327" height="388" alt="Screenshot 2026-11-17 224553" src="https://github.com/user-attachments/assets/b9e93304-a803-4c4c-8bc8-1b2d923b0955" />


### 6.  HSV, grayscale, and YCrCb versions of the image.

<img width="396" height="403" alt="Screenshot 2026-11-17 224558" src="https://github.com/user-attachments/assets/8ac48d40-2418-4594-ac80-8b32fed57991" />


<img width="285" height="390" alt="Screenshot 2026-11-17 224600" src="https://github.com/user-attachments/assets/a93db81f-4035-4843-b4c1-8a9e390f0a7f" />



<img width="331" height="402" alt="Screenshot 2026-11-17 224604" src="https://github.com/user-attachments/assets/52c91cf5-42cd-4da6-b189-6fab257f97f8" />



### 7.  Image converted from HSV back to RGB.

<img width="312" height="397" alt="Screenshot 2026-11-17 224607" src="https://github.com/user-attachments/assets/1a506e2e-ae2c-4a97-af1e-b9b6f864a148" />


### 8.  Image with the selected pixel changed to white.

<img width="361" height="400" alt="Screenshot 2026-11-17 224610" src="https://github.com/user-attachments/assets/e13c4c79-b5e7-4659-841d-9b0825b06f25" />


### 9.  Resized image with half the original width and height.

<img width="545" height="396" alt="Screenshot 2026-11-17 224613" src="https://github.com/user-attachments/assets/1be00f85-a7a6-40fb-8ab7-8bd681a479c4" />


### 10. Cropped region of interest (ROI).

<img width="411" height="387" alt="Screenshot 2026-11-17 224616" src="https://github.com/user-attachments/assets/cb3213a4-589d-48de-861f-879947260625" />


### 11. Horizontally flipped image.

<img width="366" height="402" alt="Screenshot 2026-11-17 224620" src="https://github.com/user-attachments/assets/7fdfaec4-fcdf-45f3-83e3-8d0da87cb5e5" />


### 12. Vertically flipped image.

<img width="402" height="405" alt="Screenshot 2026-11-17 224623" src="https://github.com/user-attachments/assets/6132c112-779d-49db-977e-af4444c0514a" />




## RESULT

Thus, basic image-processing operations such as image loading,
displaying, drawing, color-space conversion, pixel modification,
resizing, cropping, flipping, and saving were performed successfully
using Python and OpenCV.
