OpenCV Image Processing Fundamentals

A beginner-friendly Python project covering fundamental image-processing operations using OpenCV, NumPy, and Matplotlib.

The project implements 25 practical questions (Q1–Q25) covering image input/output, pixel manipulation, grayscale conversion, image statistics, quantization, sampling, cropping, and geometric transformations.

Features

This project demonstrates:

Reading and displaying images with OpenCV

Checking whether an image was loaded successfully

Extracting image dimensions and channels

Calculating pixel counts

Inspecting image data types

Saving images with OpenCV

Reading images directly in grayscale

Converting BGR images to grayscale

Displaying images with Matplotlib

Resizing images

Accessing and modifying individual pixels

Splitting and merging color channels

Calculating minimum, maximum, mean, and standard deviation

Creating constant grayscale images

Creating grayscale intensity ramps

4-bit and 2-bit image quantization

Image downsampling

Cropping Regions of Interest (ROI)

Rotating and saving images

Requirements

Make sure Python 3.x is installed.

Install the required Python libraries using:

pip install opencv-python matplotlib numpy

Libraries Used
Library	Purpose
OpenCV (cv2)	Image reading, writing, processing, and display
NumPy	Numerical operations and image arrays
Matplotlib	Image visualization
Project Structure
project/
│
├── main.py
├── input.jpg
├── output_saved.jpg
├── modified_pixel.jpg
├── rotated_90.jpg
└── README.md


output_saved.jpg, modified_pixel.jpg, and rotated_90.jpg are generated automatically when the program runs.

Input Image

Place an image named:

input.jpg


in the same directory as the Python script.

Alternatively, change the following line in the code to use another image path:

image_path = "input.jpg"


For example:

image_path = "images/my_photo.jpg"

Questions Covered
Fundamentals & Basic I/O
Q1 — Read and Display an Image

The program reads an image using:

cv2.imread()


and displays it using:

cv2.imshow()

Q2 — Check Image Loading

The program verifies whether the image was successfully loaded.

If loading fails, an error message is displayed:

Error: Unable to load image from 'input.jpg'. Please check the file path.

Q3 — Image Dimensions

The program prints:

Height

Width

Number of channels

Example:

Q3: Height = 720, Width = 1280, Channels = 3

Q4 — Pixel Count

Two values are calculated:

Spatial pixel count: height × width

Total matrix elements: height × width × channels

Q5 — Image Data Type

The program prints the NumPy data type of the image matrix.

For a typical OpenCV image:

uint8

Q6 — Save an Image

The original image is saved as:

output_saved.jpg


using:

cv2.imwrite()

Q7 — Read an Image in Grayscale

The image is directly loaded in grayscale mode using:

cv2.IMREAD_GRAYSCALE

Q8 — Convert Color Image to Grayscale

A color image is converted to grayscale using:

cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

Q9 — Display Using Matplotlib

OpenCV stores color images in BGR order, while Matplotlib expects RGB.

Therefore, the program converts:

BGR → RGB


before displaying the image with Matplotlib.

The axis is hidden using:

plt.axis("off")

Q10 — Resize to 50%

The image is resized to half its original width and height:

cv2.resize(img, (0, 0), fx=0.5, fy=0.5)

Pixel & Image Representation
Q11 — Access a Pixel

A pixel is accessed using an (x, y) coordinate.

For example:

x, y = 50, 50
pixel_val = img[y, x]


NumPy uses:

[row, column]


which corresponds to:

[y, x]

Q12 — Modify a Pixel

The selected pixel is changed to bright red.

Because OpenCV uses BGR ordering:

img_modified[y, x] = [0, 0, 255]


The modified image is saved as:

modified_pixel.jpg

Q13 — Print B, G, and R Values

The individual color-channel values are extracted:

b, g, r = img[y, x]


and printed.

Q14 — Split Color Channels

The image is separated into:

Blue channel

Green channel

Red channel

using:

cv2.split(img)


Each channel is displayed separately.

Q15 — Merge Color Channels

The individual channels are combined again using:

cv2.merge([b_chan, g_chan, r_chan])

Q16 — Minimum and Maximum Intensity

The minimum and maximum grayscale intensity values are calculated using:

cv2.minMaxLoc()


For an 8-bit grayscale image, intensity values range from:

0 → 255

Q17 — Mean Intensity

NumPy is used to calculate the average grayscale intensity:

np.mean(gray_converted)

Q18 — Mean and Standard Deviation

OpenCV's:

cv2.meanStdDev()


is used to calculate:

Mean intensity

Standard deviation

Q19 — Constant Grayscale Image

A 256 × 256 grayscale image is created where every pixel has intensity:

128


The image is generated with:

np.full((256, 256), 128, dtype=np.uint8)

Q20 — Grayscale Intensity Ramp

An intensity ramp is created where pixel values gradually increase:

0 → 255


This demonstrates the transition from black to white.

Sampling, Quantization & Geometric Operations
Q21 — 4-bit Quantization

An 8-bit grayscale image is converted to a 4-bit representation.

An image with 4 bits can represent:

2⁴ = 16 intensity levels


The resulting image is displayed for visualization.

Q22 — 2-bit Quantization

An 8-bit grayscale image is converted to a 2-bit representation.

A 2-bit image has:

2² = 4 intensity levels

Q23 — Downsampling

The image is reduced by a factor of 2 in both dimensions.

For example:

Original:     1280 × 720
Downsampled:   640 × 360


Nearest-neighbor interpolation is used:

cv2.INTER_NEAREST

Q24 — Crop an ROI

A rectangular Region of Interest (ROI) is extracted from the image.

The current implementation crops the central 50% of the image:

25% → 75% of height
25% → 75% of width


The cropped region is then displayed.

Q25 — Rotate Image

The image is rotated by 90 degrees clockwise using:

cv2.rotate(img, cv2.ROTATE_90_CLOCKWISE)


The result is displayed and saved as:

rotated_90.jpg

How to Run

Clone or download the project.

Place your image in the project directory:

input.jpg


Install the dependencies:

pip install opencv-python matplotlib numpy


Run the Python script:

python main.py


The program will display several image-processing results and print numerical results in the terminal.

Important Note About cv2.imshow()

The program uses OpenCV GUI functions such as:

cv2.imshow()
cv2.waitKey(0)
cv2.destroyAllWindows()


Therefore, it is recommended to run the project in a local environment with GUI support.

If you are using a headless environment such as some cloud servers or notebook environments, cv2.imshow() may not work. In that case, use Matplotlib or save the resulting images to files instead.

Concepts Demonstrated

This project provides practical exposure to several fundamental Digital Image Processing concepts:

Image Acquisition
       ↓
Image Representation
       ↓
Color Spaces
       ↓
Pixel Manipulation
       ↓
Image Statistics
       ↓
Sampling
       ↓
Quantization
       ↓
Geometric Transformations

Technologies

Python 3

OpenCV

NumPy

Matplotlib

Learning Objectives

After completing this project, you should understand:

How digital images are represented as NumPy arrays

How OpenCV reads and writes images

The difference between BGR and RGB

How grayscale images differ from color images

How to access and modify individual pixels

How image dimensions and channels work

How sampling and quantization affect images

How to perform basic geometric transformations

How to calculate basic image statistics

How to visualize images using OpenCV and Matplotlib

Output Files

Running the program generates the following files:

File	Description
output_saved.jpg	Copy of the original image
modified_pixel.jpg	Image with a modified pixel
rotated_90.jpg	Image rotated 90° clockwise
License

This project is intended for educational and learning purposes.
