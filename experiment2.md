CODE:
import cv2
import numpy as np
import matplotlib.pyplot as plt
from operator import add
from functools import reduce
img = cv2.imread("dhoniii.avif")
if img is None:
    raise FileNotFoundError("Image not found. Check the file path.")
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
def split4(image):
    half_split = np.array_split(image, 2, axis=0)
    res = map(lambda x: np.array_split(x, 2, axis=1), half_split)
    return reduce(add, res)
split_img = split4(img)
print(split_img[0].shape, split_img[1].shape)
fig, axs = plt.subplots(2, 2)
axs[0, 0].imshow(split_img[0])
axs[0, 1].imshow(split_img[1])
axs[1, 0].imshow(split_img[2])
axs[1, 1].imshow(split_img[3])
for ax in axs.flat:
    ax.axis("off")
def concatenate4(north_west, north_east, south_west, south_east):
    top = np.concatenate((north_west, north_east), axis=1)
    bottom = np.concatenate((south_west, south_east), axis=1)
    return np.concatenate((top, bottom), axis=0)
full_img = concatenate4(
    split_img[0],
    split_img[1],
    split_img[2],
    split_img[3]
)
plt.figure()
plt.imshow(full_img)
plt.axis("off")
plt.show()
OUTPUT:
<img width="441" height="438" alt="Screenshot 2026-02-18 101913" src="https://github.com/user-attachments/assets/3f787535-6c61-4680-acfd-dd21b52e4c5f" />
