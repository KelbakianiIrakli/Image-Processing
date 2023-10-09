Student: Irakli Kelbakiani
Email:	Irakli.Kelbakiani@students.unibe.ch
Github: https://github.com/KelbakianiIrakli/Image-Processing/tree/main/Exercise-2


(a) Define a universal color table with a maximum of 256 different colors.
I define 216 colors in a following way:
for r in range(0, 256, 51):  # Red channel values (0, 51, 102, 153, 204, 255)
    for g in range(0, 256, 51):  # Green channel (0, 51, 102, 153, 204, 255)
        for b in range(0, 256, 51):  # Blue channel (0, 51, 102, 153, 204, 255)
            color_table.append((r, g, b))

Each of the three nested loops iterates over the red, green, and blue channels, respectively, with step increments of 51. Given this structure, we can calculate the total number of colors generated as follows:
For the red channel (r), there are (256 - 0) / 51 + 1 possible values, which is 6 values (0, 51, 102, 153, 204, 255).
For the green channel (g), there are also 6 possible values.
For the blue channel (b), there are 6 possible values.
So, as 6*6*6=216 I have total 216 colors defined.


(b) Write an algorithm that transforms the initial pixel values with an index to the color
table so that the return image looks as similar as possible to the original image.
def find_closest_color_index(pixel, color_table):
    min_distance = float("inf")
    closest_index = 0

    for i, color in enumerate(color_table):
        # Calculate Euclidean distance between pixel and color
        distance = sum((a - b) ** 2 for a, b in zip(pixel, color)) ** 0.5

        if distance < min_distance:
            min_distance = distance
            closest_index = i

    return closest_index
I created a function, in which we calculate Euclidean distance of this pixel and each color in color table. We will take value from the color map which has smallest distance.

(c) Replace the universal color table by an adaptive colour table, which is optimized for
the given input image.
generate_adaptive_color_table(image, num_colors)-  function generates an adaptive color table using K-Means clustering by extracting representative 256 colors from lena image.

(d) Apply your two algorithms on the image ”Lena” which is on ILIAS.
Please, see images in the same dir as this file.

