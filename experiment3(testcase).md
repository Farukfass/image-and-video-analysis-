code:

!pip install opencv-python-headless

import cv2
from google.colab.patches import cv2_imshow
from google.colab import files

uploaded = files.upload()

image = cv2.imread("msd.webp") # Changed filename from sunset.jpg to msd.webp
if image is None:
    raise Exception("Image not loaded. Please upload a valid image file.") 
print("Original Image")
cv2_imshow(image)

zoom_in = cv2.resize(image, None, fx=1.5, fy=1.5)
print("Zoom In Image")
cv2_imshow(zoom_in)

zoom_out = cv2.resize(image, None, fx=0.5, fy=0.5)
print("Zoom Out Image")
cv2_imshow(zoom_out)
OUTPUT:
<img width="755" height="542" alt="image" src="https://github.com/user-attachments/assets/b5376b86-857f-4d6b-866c-0179553b0a32" />
