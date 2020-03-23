# Image-denoising

Image Denoising: Implementation

Test image: 

![Artificially-created-image](https://github.com/gandalf1819/Image-denoising/blob/master/images/lena.png)

## Box Filter

Using box filter, the image gets blurred. It removes noise by reducing the intensity variance since the new distribution is closer to the mean.

## Gaussian Filter

A Gaussian filter is a linear filter. It's usually used to blur the image or to reduce noise. We reduce noise by reducing variance in pixel intensities, but now nearby pixels have a greater influence on blurring depending on the sigma.

## Median Filter

We can see the difference between the original ground-truth image and the images after applying box, gaussian and median filters. Image gets blurred because the values are shifted towards the median. Thus, reducing variance of intensities.

## Comparison: 

### Low Noise:
Sigma = 12

![low-noise-comparison](https://github.com/gandalf1819/Image-denoising/blob/master/images/low-noise.png)

### Medium Noise:
Sigma = 22

![medium-noise-comparison](https://github.com/gandalf1819/Image-denoising/blob/master/images/medium-noise.png)

### High Noise:
Sigma = 32

![high-noise-comparison](https://github.com/gandalf1819/Image-denoising/blob/master/images/high-noise.png)

## Inference:

From the above comparison, we can conclude that there is no particular formula or a mathematical derivation to decide the **optimal sigma**. It will depend on image factors like - the resolution of the image, the size of your objects in the image. Sigma controls how fat your kernel function is going to be. Higher the sigma values, wider the radius to blur away the images. Higher values of sigma would force you to use a larger kernel matrix to capture enough of the function's energy.

For your specific case, you want your kernel to be big enough to cover most of the object but not so large that it starts overlapping multiple neighboring objects at a time. Therefore, object separation is an important factor along with size.

Based on the results for each of the filters, we can say that we can use **Median filter** for ‘Salt and Pepper noise’. If you have a smooth surface with no texture which corresponds to a low frequency image, **Gaussian filter** would be the best to use. **Box or Mean filter** would be ideal to approx. gaussian and used widely in the rest of the use cases.

## Runtime comparison:

**Box > Gaussian > Median**

Box filter is the fastest, then comes gaussian and median at the bottom and slowest among them.

## Template Matching:

Test image:

![Test-image](https://github.com/gandalf1819/Image-denoising/blob/master/images/multiplekeys.png)

### Thresholding:

![Thresholding-keys](https://github.com/gandalf1819/Image-denoising/blob/master/images/thresholding-keys.png)

Sample key:

![Sample-key](https://github.com/gandalf1819/Image-denoising/blob/master/images/sample-key.png)

### Thresholding results:

![Thresholding-results](https://github.com/gandalf1819/Image-denoising/blob/master/images/thresholding-results.png)

We could observe the peak at (515, 28) and for rest of the keys we couldn’t observe a peak. The position of peak is the same position as of the key which validates that our function works correctly.


