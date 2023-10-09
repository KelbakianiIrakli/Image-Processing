Student: Irakli Kelbakiani
Email:	Irakli.Kelbakiani@students.unibe.ch
Github: https://github.com/KelbakianiIrakli/Image-Processing/tree/main/Exercise-1


Horizontal Flipping (flip_image_horizontally):

To flip an image horizontally we should reverse the left-to-right arrangement of pixels.
The code creates a new blank image with the same dimensions as the input image.
It then iterates over each pixel in the input image. For each pixel, it calculates its new position in the flipped image by subtracting its current x-coordinate from the width of the image minus one (width - x - 1), of course y coordinate stays same.
The pixel at the current position in the input image is copied to the new position in the flipped image.
After processing all pixels, we have horizontally flipped image .



Vertical Flipping (flip_image_vertically):
To flip an image vertically we should reverse top-to-bottom arrangement of pixels.
The code creates a new blank image with the same dimensions as the input image.
It iterates over each pixel in the input image.
For each pixel, it calculates its new position in the flipped image by subtracting its current y-coordinate from the height of the image minus one (height - y - 1).
The pixel at the current position in the input image is copied to the new position in the flipped image.
After processing all pixels, we have an image that is flipped vertically.


Both Horizontal and Vertical Flipping (flip_image_both):

This function combines both horizontal and vertical flipping.
The result is an image that is flipped both horizontally and vertically.