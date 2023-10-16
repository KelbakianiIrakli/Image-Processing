Student: Irakli Kelbakiani
Email:	Irakli.Kelbakiani@students.unibe.ch
Github: https://github.com/KelbakianiIrakli/Image-Processing/tree/main/Exercise-3

1.
(a) Use an existing library to separate the three channels of your RGB image and show each of them separately.

image = cv2.imread('Lena.png')

# Split the image into R, G, and B channels
r, g, b = cv2.split(image)

# Display the channels
plt.subplot(131)
plt.imshow(r, cmap='gray')
plt.title('Red Channel')

plt.subplot(132)
plt.imshow(g, cmap='gray')
plt.title('Green Channel')

plt.subplot(133)
plt.imshow(b, cmap='gray')
plt.title('Blue Channel')

plt.show()

(b) Write your own algorithm to separate an RGB image into the three channels of the HSL color space (H, S, L). See https://www.rapidtables.com/convert/color/ rgb-to-hsl.html

convert RGB image into its corresponding HSL (Hue, Saturation, Lightness) color space representation. It does this by iterating through each pixel in the image and performing the following steps for each pixel:

1.Extract the RGB values for the pixel and scale them to the range [0, 1].

2.Use the colorsys.rgb_to_hls function to convert the scaled RGB values to HSL values (Hue, Saturation, Lightness).

3.Store the calculated HSL values in the output HSL image.

4.Scale the HSL values back to the range [0, 255] and convert them to 8-bit unsigned integers (uint8) to match typical image representations.

(c) Write your own algorithm to reconstruct an RGB image from the H, S, L channels. See https://www.rapidtables.com/convert/color/hsl-to-rgb.html

I scale h,s,l to the expected normalized ranges before using colorsys.hlt_to_rgb to convert to RGB.

360 represents the maximum value for the Hue component in the HSL color space. Hue is typically measured in degrees, and the valid range is [0, 360 degrees]. In the code, h is divided by 360 to scale it to the [0, 1] range, as the colorsys.hls_to_rgb function expects the Hue value to be normalized to this range.

100 represents the maximum value for the Saturation and Lightness components in the HSL color space. Saturation and Lightness are often expressed as percentages, and the valid range for both is [0, 100]. In the code, s and l are divided by 100 to scale them to the [0, 1] range, as the colorsys.hls_to_rgb function also expects these values to be in this normalized range.

2.
(a) Write your own histogram equalization algorithm based on the method presented in the lecture.

1.histogram_equalization is a function that takes a grayscale image (gray_image) as input and returns an equalized grayscale image.

2.The code calculates the histogram (hist) of the input grayscale image using the np.histogram function. The histogram represents the frequency of occurrence of each intensity level (from 0 to 255).

3.cdf (cumulative distribution function) is computed as the cumulative sum of the histogram. The CDF represents the cumulative probability of pixel intensities.

4.cdf_normalized is calculated by scaling the CDF values so that they span the entire intensity range (0 to 255). This scaling ensures that the highest CDF value corresponds to the maximum intensity level.

5.The actual histogram equalization is performed using np.interp. It maps the input grayscale image (gray_image) to the CDF values (cdf_normalized) to redistribute the pixel intensities.

6.Finally, the equalized image is returned as an 8-bit unsigned integer image (np.uint8), ensuring that the intensity values are in the [0, 255] range.
(b) Apply your algorithm on the greyscale images provided on ILIAS.

Please, see results in ipynb file.

3.
(a) Firstly, apply your histogram equalization algorithm on the R, G, and B channels
and reconstruct your image.
(b) Secondly, apply the histogram equalization on the L channel of your HSL image and
reconstruct your image with the new L channel and the original H and S channels.
Convert the result on an RGB image.
(c) Visually compare the result of the two
1.I notice that equalization leads to artifacts or exaggerate noise in the image.
2.When we equalize the RGB image directly, we are manipulating the color channels independently. As a result, the colors change, and the image exhibits a different color balance
