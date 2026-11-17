# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** G.Ramanujam 
- **Register Number:** 212224240129

  ### Ex. No. 01
  ### Image Handling and Pixel Transformations Using OpenCV
  **Name:** G.Ramanujam    **Reg.No:** 212224240129
#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
img=cv2.imread("Eagle_in_Flight.jpg",0)
```

#### 2. Print the image width, height & Channel.
```python
img.shape
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img)
plt.title('BGR Image')
plt.axis('on')
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite('Eagle.png',img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img = cv2.imread('Eagle_in_Flight.jpg')  
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img_rgb)
plt.show()
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
crop = img_rgb[0:450,200:550] 
plt.imshow(crop[:,:,::1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```

#### 8. Resize the image up by a factor of 2x.
```python
res=cv2.resize(crop,None,fx=50,fy=50,interpolation=cv2.INTER_LINEAR)
```

#### 9. Flip the cropped/resized image horizontally.
```python
flipped_img=cv2.flip(crop,1)
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img=cv2.imread('Apollo-11-launch.jpg',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text=cv2.putText(img_rgb,"Apollo 11 Saturn V Launch",(300, 700),cv2.FONT_HERSHEY_SIMPLEX,1,(255,255,255),2)
plt.imshow(text)
plt.title('New Image')
plt.show()
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)
```

#### 13. Display the final annotated image.
```python
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```python
img =cv2.imread('boy.jpg',cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 
```

#### 15. Adjust the brightness of the image.
```python
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)  
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```

## Output:
- **i)** Read and Display an Image.  
- **ii)** Adjust Image Brightness.  
- **iii)** Modify Image Contrast.  
- **iv)** Generate Third Image Using Bitwise Operations.


<img width="299" height="393" alt="Screenshot 2026-11-17 224539" src="https://github.com/user-attachments/assets/f361e1a5-5367-432f-8e50-59d30da272bf" />

<img width="281" height="390" alt="Screenshot 2026-11-17 224544" src="https://github.com/user-attachments/assets/95413588-4b41-4172-ad08-3c3002176291" />

<img width="274" height="396" alt="Screenshot 2026-11-17 224548" src="https://github.com/user-attachments/assets/3893733e-87ed-47d7-bb53-3409174f8a22" />

<img width="298" height="395" alt="Screenshot 2026-11-17 224550" src="https://github.com/user-attachments/assets/09e7428c-0603-4389-addd-6824e4184118" />

<img width="327" height="388" alt="Screenshot 2026-11-17 224553" src="https://github.com/user-attachments/assets/c4d7b621-ac76-4c9e-b933-bdc4774dd9e8" />

<img width="316" height="395" alt="Screenshot 2026-11-17 224555" src="https://github.com/user-attachments/assets/948d6a71-0a41-4263-88aa-687614e6eb27" />

<img width="396" height="403" alt="Screenshot 2026-11-17 224558" src="https://github.com/user-attachments/assets/18607458-3d5b-4317-a8f6-faef0c2858d8" />

<img width="285" height="390" alt="Screenshot 2026-11-17 224600" src="https://github.com/user-attachments/assets/751e855b-6520-4a49-b81d-05c8376673ac" />

<img width="331" height="402" alt="Screenshot 2026-11-17 224604" src="https://github.com/user-attachments/assets/afb6f500-a4d0-4976-94ac-38cb9671b922" />

<img width="312" height="397" alt="Screenshot 2026-11-17 224607" src="https://github.com/user-attachments/assets/e51b67f4-3d2b-4c2d-890d-922fa0032d9e" />

<img width="361" height="400" alt="Screenshot 2026-11-17 224610" src="https://github.com/user-attachments/assets/ae3fe12e-470a-48a1-a28b-cbb8797e6b3f" />

<img width="545" height="396" alt="Screenshot 2026-11-17 224613" src="https://github.com/user-attachments/assets/95a3e2ea-f737-4a7c-96d0-037623c0fc9b" />

<img width="411" height="387" alt="Screenshot 2026-11-17 224616" src="https://github.com/user-attachments/assets/f0a66f9e-dbab-464a-9a1d-9db25b025b5b" />

<img width="366" height="402" alt="Screenshot 2026-11-17 224620" src="https://github.com/user-attachments/assets/46419f7e-4d6c-4285-bc9e-e6dbeda377e6" />

<img width="402" height="405" alt="Screenshot 2026-11-17 224623" src="https://github.com/user-attachments/assets/d1c74435-7c2a-449e-a603-138f6b1289e7" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

