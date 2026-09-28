Computer Vision Lab 4 – Bit Plane Slicing
Overview

This project demonstrates Bit Plane Slicing, a fundamental image-processing technique used to analyze the individual binary bit levels of a grayscale image.

A grayscale image uses 8 bits per pixel, meaning each pixel can have a value between 0 and 255. Each pixel can therefore be represented using 8 binary bits, from Bit Plane 0 (LSB) to Bit Plane 7 (MSB).

In this lab, all eight bit planes of a grayscale image are extracted and displayed separately.

Technologies Used

Python

OpenCV (cv2)

NumPy

Matplotlib

Google Colab

Input Image

The program reads the following grayscale image:

/content/Nature view.jpg


The image is loaded using OpenCV:

img = cv2.imread("/content/Nature view.jpg", 0)


The 0 parameter loads the image in grayscale mode.

What is Bit Plane Slicing?

Bit Plane Slicing separates a grayscale image into its individual binary bit planes.

For an 8-bit grayscale pixel, the binary representation is:

Bit 7  Bit 6  Bit 5  Bit 4  Bit 3  Bit 2  Bit 1  Bit 0
 MSB                                             LSB


Each bit plane contains either 0 or 1 for every pixel.

For visualization, the binary values are converted to:

0 → 0   (Black)
1 → 255 (White)


This produces a visible black-and-white image for each bit plane.

Method 1: Using Bitwise Operations

The first implementation extracts each bit plane using bit shifting and a bitwise AND operation:

bit_plane = (img >> i) & 1


The extracted binary plane is then converted for visualization:

vis_plane = bit_plane * 255


The process is repeated for all eight bit planes:

for i in range(8):

Method 2: Manual Bit Plane Extraction

The second implementation extracts the bit planes manually without using bitwise shifting.

For each pixel, the kth bit is calculated using:

bit = (pixel // (2 ** k)) % 2


If the extracted bit is 1, the corresponding output pixel is set to 255; otherwise, it remains 0.

if bit == 1:
    bit_plane[i, j] = 255
else:
    bit_plane[i, j] = 0


This demonstrates the underlying mathematical process of bit-plane extraction.

Bit Planes

The program extracts eight bit planes:

Bit Plane	Description
Bit Plane 0	Least Significant Bit (LSB)
Bit Plane 1	Second least significant bit
Bit Plane 2	Third bit
Bit Plane 3	Fourth bit
Bit Plane 4	Fifth bit
Bit Plane 5	Sixth bit
Bit Plane 6	Seventh bit
Bit Plane 7	Most Significant Bit (MSB)

Generally, the higher-order bit planes contain more of the major visual structure of the image, while the lower-order planes tend to contain finer intensity variations and details.

Output

The program displays a 3×3 grid containing:

Original grayscale image

Bit Plane 0

Bit Plane 1

Bit Plane 2

Bit Plane 3

Bit Plane 4

Bit Plane 5

Bit Plane 6

Bit Plane 7

Each bit plane is displayed as a black-and-white image.

How to Run
Using Google Colab

Open the notebook in Google Colab.

Upload Nature view.jpg to the /content/ directory.

Run the cells sequentially.

The original image and its eight bit planes will be displayed.

Required Libraries

Install the required libraries if necessary:

pip install opencv-python numpy matplotlib

Applications

Bit Plane Slicing can be useful in:

Image analysis

Image compression

Image enhancement

Image segmentation

Pattern recognition

Image representation

Studying the contribution of individual bits to image information

Conclusion

This experiment demonstrates how an 8-bit grayscale image can be decomposed into eight individual bit planes. Both a bitwise implementation and a manual mathematical implementation are provided.

The experiment shows that different bit planes contribute differently to the appearance and information content of a grayscale image, with higher-order planes generally representing more significant image structures.
