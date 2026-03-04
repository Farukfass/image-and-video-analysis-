CODE:
import cv2
import numpy as np
import matplotlib.pyplot as plt
from google.colab import files
uploaded = files.upload()
image_path = list(uploaded.keys())[0]
print(image_path)
img = cv2.imread(image_path)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
plt.figure(figsize=(12,5))
plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.subplot(1,2,2)
plt.imshow(edges, cmap='gray')
plt.title("Edge Detection Result")
plt.axis('off')
plt.show()

OUTPUT:
<img width="919" height="465" alt="Screenshot 2026-03-04 095244" src="https://github.com/user-attachments/assets/af71b546-efa6-4f5d-89c9-43b3e9aeb0bf" />
