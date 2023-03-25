# Image-Colour-Identification
Image color identification with Machine Learning and Image Processing, using Python




1. The image
The first step is to get an image. I’ve used this one:
![nature](https://user-images.githubusercontent.com/120296734/227698223-6c74f04e-4da8-42fa-b93a-4ec71f8c7600.jpg)


2. The libraries
Let’ s invoke some demons. You will need the Sklearn libraries for the Machine Learning part, Numpy for the vector transformations, Pandas for the final summary and some Image Processing typical libraries (cv2, skimage, matplotlib.pyplot, …)



3. The Machine Learning part
Now, the main idea is that it is possible to use the image as a (N_rows X N_columns X N_channels) vector. Considering this vector, it is possible to apply the K Means algorithm and identify k clusters, that will be our colors.
This is super interesting for several reasons. The first one is that it does not require any specific training on a huge set of images. The second one is that you can increase the number of clusters (and, thus, the number of colors), choosing a smaller or higher amount of tones.
In order to do that, you will need these functions:  [1]  get_image   [2] RGB2HEX

Once it is done, you will have your 10 colors (I have chosen them to be 10 by setting “number_of_colors=10”)

 






3. The Image Processing part
So we have our colors. The difficult part is that while we can see them and identify them, we can’t associate each element of the “label” list to its correspondent color. In fact, K Means is an unsupervised learning method.

So if we want to automatically detect the color of the sky and associate it to one of the color in the pie chart, we need to be a little more creative.

The main idea is pretty basic. In fact, the image is RGB encoded. That means that if we compute the difference between the image and the rgb expression of one of the 10 colors, we get [0,0,0] exactly when the image is equal to the color.

Let me tell you, this is not orthodox. In fact, you will have negative pixels. But it works, and if it works, don’t touch it :)

The first step is technical, and it is based on converting the RGB in integer values.

Then, if we want to identify the colors of the image, the idea is to break this image into smaller squares. In this case, I’ve chosen the dimension of each square to be N_rows/10 X N_columns/10, thus obtaining 100 squares. These squares are obtained by using the following function.


Of course, the squares are not monochromatic. This means that each square will have multiple colors. Nonetheless, the average distance between the image is the indicator that we need: we pick the color that, in average, is closer to 0 than the others. In particular, we do that by using this function:


With this function, we can plot the “best color” for each square.
![MergedImages](https://user-images.githubusercontent.com/120296734/227699183-98d43101-8366-49ba-8ec5-856cbf9ea433.png)


4. The final result
To get the summary of this experiment for all the squares of the image, the following function can be used:


