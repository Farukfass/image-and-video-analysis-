CODE:
import cv2
import numpy as np
import matplotlib.pyplot as plt
h, w = 400, 400
img = np.zeros((h, w, 3), dtype=np.uint8)
# Homogeneous colors (RGB)
img[0:200, 0:200]   = [255, 0, 0]     # Top-left (Red)
img[0:200, 200:400] = [0, 255, 0]     # Top-right (Green)
img[200:400, 0:200] = [0, 0, 255]     # Bottom-left (Blue)
img[200:400, 200:400] = [255, 255, 0] # Bottom-right (Yellow)
def split4(image):
    h, w = image.shape[:2]
    return (
        image[0:h//2, 0:w//2],     # NW
        image[0:h//2, w//2:w],     # NE
        image[h//2:h, 0:w//2],     # SW
        image[h//2:h, w//2:w]      # SE
    )
q1, q2, q3, q4 = split4(img)
fig, axs = plt.subplots(2, 2)
axs[0, 0].imshow(q1)
axs[0, 1].imshow(q2)
axs[1, 0].imshow(q3)
axs[1, 1].imshow(q4)
for ax in axs.flat:
    ax.axis("off")
plt.show()
def concatenate4(nw, ne, sw, se):
    top = np.concatenate((nw, ne), axis=1)
    bottom = np.concatenate((sw, se), axis=1)
    return np.concatenate((top, bottom), axis=0)
full_img = concatenate4(q1, q2, q3, q4)
plt.imshow(full_img)
plt.axis("off")
plt.show()

OUTPUT:
<img width="620" height="544" alt="Screenshot 2026-02-18 101904" src="https://github.com/user-attachments/assets/6559cf91-4d95-4c9f-8050-fa3ffa074e3c" />
