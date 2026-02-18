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
<img width="1359" height="506" alt="Screenshot 2026-02-18 101612" src="https://github.com/user-attachments/assets/b5a4a3e2-8b8f-49c0-88e7-59a2e7e411f6" />
<img width="1027" height="534" alt="Screenshot 2026-02-18 101602" src="https://github.com/user-attachments/assets/c81fe494-d794-4c46-ba7d-0a90d52c16b3" />
<img width="1329" height="493" alt="Screenshot 2026-02-18 101549" src="https://github.com/user-attachments/assets/a25474ed-01bd-4994-b6f3-0e2a6e914726" />

