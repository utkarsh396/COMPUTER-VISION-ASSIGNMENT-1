import cv2
import matplotlib.pyplot as plt
import numpy as np

# Place an image file named 'input.jpg' in the same directory, or specify your path
image_path = "input.jpg"

# ==========================================
# FUNDAMENTALS & BASIC I/O
# ==========================================

# Q1. Read an image using OpenCV and display it.
img = cv2.imread(image_path)
if img is not None:
    cv2.imshow("Q1 - Original Image", img)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

# Q2. Check whether an image was loaded successfully.
# If loading fails, print a meaningful error message.
if img is None:
    print(
        f"Error: Unable to load image from '{image_path}'. Please check the file path."
    )
    exit()

# Q3. Print the image height, width, and number of channels.
height, width, channels = img.shape
print(f"Q3: Height = {height}, Width = {width}, Channels = {channels}")

# Q4. Calculate and print the total number of pixels in an image.
total_pixels = img.size  # Total elements (height * width * channels)
pixel_count = height * width  # Spatial pixel count
print(
    f"Q4: Spatial Pixels = {pixel_count}, Total Matrix Elements = {total_pixels}"
)

# Q5. Print the data type (dtype) of the image matrix.
print(f"Q5: Image Data Type = {img.dtype}")

# Q6. Read an image and save it with a different filename using OpenCV.
cv2.imwrite("output_saved.jpg", img)
print("Q6: Image successfully saved as 'output_saved.jpg'.")

# Q7. Read an image directly in grayscale mode and display it.
gray_direct = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)
cv2.imshow("Q7 - Direct Grayscale", gray_direct)
cv2.waitKey(0)
cv2.destroyAllWindows()

# Q8. Convert a color image to grayscale using cv2.cvtColor().
gray_converted = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Q9. Display an image using Matplotlib and hide the axis.
# OpenCV uses BGR by default, so convert to RGB for Matplotlib display
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img_rgb)
plt.axis("off")
plt.title("Q9 - Matplotlib Display (Axis Hidden)")
plt.show()

# Q10. Resize an image to 50% of its original width and height.
resized_50 = cv2.resize(img, (0, 0), fx=0.5, fy=0.5)
print(f"Q10: Resized Resolution = {resized_50.shape[1]}x{resized_50.shape[0]}")


# ==========================================
# PIXEL & IMAGE REPRESENTATION
# ==========================================

# Q11. Access and print the pixel value at a user-provided (x, y) coordinate.
# Note: In NumPy indexing, row = y, column = x
x, y = 50, 50
pixel_val = img[y, x]
print(f"Q11: Pixel value at (x={x}, y={y}) [BGR] = {pixel_val}")

# Q12. Modify the intensity/value of a selected pixel and save the modified image.
img_modified = img.copy()
img_modified[y, x] = [0, 0, 255]  # Change pixel to bright Red in BGR
cv2.imwrite("modified_pixel.jpg", img_modified)
print("Q12: Modified pixel saved as 'modified_pixel.jpg'.")

# Q13. Read a color image and print the B, G, and R values of a selected pixel.
b, g, r = img[y, x]
print(f"Q13: At (x={x}, y={y}) -> Blue={b}, Green={g}, Red={r}")

# Q14. Split a color image into its B, G, and R channels and display each channel.
b_chan, g_chan, r_chan = cv2.split(img)
cv2.imshow("Q14 - Blue Channel", b_chan)
cv2.imshow("Q14 - Green Channel", g_chan)
cv2.imshow("Q14 - Red Channel", r_chan)
cv2.waitKey(0)
cv2.destroyAllWindows()

# Q15. Merge three separate image channels into a single color image.
merged_img = cv2.merge([b_chan, g_chan, r_chan])

# Q16. Calculate and print the minimum and maximum intensity values of a grayscale image.
min_val, max_val, _, _ = cv2.minMaxLoc(gray_converted)
print(f"Q16: Grayscale Min Intensity = {min_val}, Max Intensity = {max_val}")

# Q17. Calculate and print the mean intensity of a grayscale image.
mean_val = np.mean(gray_converted)
print(f"Q17: Mean Intensity = {mean_val:.2f}")

# Q18. Calculate and print the mean and standard deviation of a grayscale image using NumPy/OpenCV.
mean_cv, std_cv = cv2.meanStdDev(gray_converted)
print(
    f"Q18: Mean = {mean_cv[0][0]:.2f}, Standard Deviation = {std_cv[0][0]:.2f}"
)

# Q19. Create a 256 x 256 grayscale image in which every pixel has intensity value 128.
constant_gray = np.full((256, 256), 128, dtype=np.uint8)

# Q20. Create and display a grayscale intensity ramp whose intensity gradually changes from 0 to 255.
ramp_row = np.linspace(0, 255, 256, dtype=np.uint8)
intensity_ramp = np.tile(ramp_row, (256, 1))

cv2.imshow("Q19 - Constant Gray (128)", constant_gray)
cv2.imshow("Q20 - Intensity Ramp", intensity_ramp)
cv2.waitKey(0)
cv2.destroyAllWindows()


# ==========================================
# SAMPLING, QUANTIZATION & GEOMETRIC OPERATIONS
# ==========================================

# Q21. Convert an 8-bit grayscale image into a 4-bit quantized image and display the result.
# 4-bit has 16 levels ($2^4$). Shift right by 4 bits, then scale back for visualization.
quant_4bit = (gray_converted // 16) * 16
cv2.imshow("Q21 - 4-bit Quantized Image", quant_4bit)

# Q22. Convert an 8-bit grayscale image into a 2-bit quantized image and display the result.
# 2-bit has 4 levels ($2^2$). Shift right by 6 bits, then scale back.
quant_2bit = (gray_converted // 64) * 64
cv2.imshow("Q22 - 2-bit Quantized Image", quant_2bit)
cv2.waitKey(0)
cv2.destroyAllWindows()

# Q23. Downsample an image by a factor of 2 in both width and height and print the original and new resolutions.
downsampled = cv2.resize(
    img, (width // 2, height // 2), interpolation=cv2.INTER_NEAREST
)
print(
    f"Q23: Original Resolution = {width}x{height} | Downsampled Resolution = {downsampled.shape[1]}x{downsampled.shape[0]}"
)

# Q24. Crop a rectangular Region of Interest (ROI) from an image using user-provided coordinates.
# Coordinates: y_start:y_end, x_start:x_end
y_start, y_end = int(height * 0.25), int(height * 0.75)
x_start, x_end = int(width * 0.25), int(width * 0.75)
roi = img[y_start:y_end, x_start:x_end]

cv2.imshow("Q24 - Cropped ROI", roi)
cv2.waitKey(0)
cv2.destroyAllWindows()

# Q25. Rotate an image by 90 degrees, display it, and save the rotated image.
rotated_90 = cv2.rotate(img, cv2.ROTATE_90_CLOCKWISE)
cv2.imshow("Q25 - Rotated 90 Degrees Clockwise", rotated_90)
cv2.imwrite("rotated_90.jpg", rotated_90)
print("Q25: Rotated image saved as 'rotated_90.jpg'.")

cv2.waitKey(0)
cv2.destroyAllWindows()
