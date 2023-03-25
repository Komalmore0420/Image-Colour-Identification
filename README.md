# Image-Colour-Identification
Image color identification with Machine Learning and Image Processing, using Python




1. The image
The first step is to get an image. I’ve used this one:


2. The libraries
Let’ s invoke some demons. You will need the Sklearn libraries for the Machine Learning part, Numpy for the vector transformations, Pandas for the final summary and some Image Processing typical libraries (cv2, skimage, matplotlib.pyplot, …)



3. The Machine Learning part
This great article gives us a really good hint. In fact, the main idea is that it is possible to use the image as a (N_rows X N_columns X N_channels) vector. Considering this vector, it is possible to apply the K Means algorithm and identify k clusters, that will be our colors.

This is super interesting for several reasons. The first one is that it does not require any specific training on a huge set of images. The second one is that you can increase the number of clusters (and, thus, the number of colors), choosing a smaller or higher amount of tones.

In order to do that, you will need these functions:
