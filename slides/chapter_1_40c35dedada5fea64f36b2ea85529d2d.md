---
title: Insert title here
key: 40c35dedada5fea64f36b2ea85529d2d

---
## The U-net network for semantic segmentation

```yaml
type: "TitleSlide"
key: "54e0c04494"
```

`@lower_third`

name: Antonio Rueda-Toicen
title: Research Programmer at Algorithmic Dynamics Lab


`@script`
In this video we're going to overview the architecture of the U-net network for semantic segmentation, which is the main deep learning algorithm that we will study in the course.


---
## State-of-the-art in semantic image segmentation

```yaml
type: "FullSlide"
key: "18ebf1ba91"
```

`@part1`
![u-net paper](https://raw.githubusercontent.com/andandandand/images-for-colab-notebooks/master/u-net-paper.png)


`@script`
The paper describing this network was published in 2015 by a group led by Olaf Ronneberger at Freiburg University. It became both the state-of-the-art and its original or "vanilla" version is the current benchmark against which other semantic segmentation algorithms are compared.


---
## ISBI Challenge 2015

```yaml
type: "FullSlide"
key: "b112793dea"
center_content: true
```

`@part1`
![segmented neurons](http://brainiac2.mit.edu/isbi_challenge/sites/default/files/Challenge-ISBI-2012-sample-image.png)
+ **Semantic segmentation of neurons in electron microscopy images**


`@script`
In 2015, U-net outperformed by a wide margin other semantic segmentation methods in challenges that were focused on the segmentation of biomedical images


---
## Data Science Bowl 2018

```yaml
type: "FullSlide"
key: "80305ab9c1"
center_content: true
```

`@part1`
![data science bowl](https://raw.githubusercontent.com/andandandand/images-for-colab-notebooks/master/data-science-bowl.png)


`@script`
U-net has been shown to be one of the most successful image segmentation methods based on convolutional neural networks. Variations of the U-net architecture currently rank as the top performers in Kaggle image segmentation competitions such as the 2018 Data Science Bowl.


---
## Encoder-decoder architecture

```yaml
type: "FullSlide"
key: "6c8db6333f"
```

`@part1`
![u-net architecture](https://cdn-images-1.medium.com/max/800/1*dKPBgCdJx6zj3MpED3lcNA.png)


`@script`
The name "U-net" comes from the "U" shape of the network architecture: it has a downsampling path that compresses the image at its left side and an upsampling path at its right side that reconstructs it. The downsampled features are concatenated with the upsampled features as a data augmentation technique built-in within the network.  

In U-net, in order to label pixels as belonging to a particular image class we map a convolution operation from original or downsampled images to a synthetic or upsampled image. 

This extraction of features is done in the encoder part of the network, which is the left side of the "U" that we see in the diagram. 

When we extract features we "downsample" the image, this means that we reduce its size and pick fragments of it.  

We then do a lossy reconstruction of the original image size in the decoder so that we can classify every pixel in the original image using slightly altered versions of the image as "built-in" training examples.

This is a type of "hardwired" data augmentation technique that allows the network to generalize better its labelings and learn salient features with relatively few training images. 

In the next lessons, we're going to explore in detail each of the operations described in the network.


---
## $3 \times 3$ Convolutions

```yaml
type: "FullSlide"
key: "be71e7aa5d"
```

`@part1`
![convolutions](http://deeplearning.stanford.edu/wiki/images/6/6c/Convolution_schematic.gif)


`@script`
Since an image is just a matrix of pixel values, applying a convolution means multiplying small parts of our input images by the filter, which is also a small matrix of the same size. The small kernel matrix gets updated with the backpropagation algorithm and is comprised of weights that are trained and modified so that they reduce the pixel labeling error.


---
## Downsampling with convolutions

```yaml
type: "FullSlide"
key: "ddbf8a548f"
```

`@part1`
```python

# convolutions are defined by 3 x 3 kernels with stride = 1
nn.Conv2d(in_channels = 5, out_channels = 5, kernel_size=3, 
          stride=1, padding=0, bias=False)

```

`in_channels`: number of channels in the input image

`out_channels`: number of channels in the output image of learned features, also the **number of different kernels** that are applied to the input channels, each kernel will have different trained weights

`kernel_size`: square dimension of each convolution filter, $3 \times 3$ here


`@script`
There are a few parameters that get adjusted here:

Kernel Size – the size of the filter.

Kernel Type – the values of the actual filter. Some examples include identity, edge detection, and sharpen.

Stride – the rate at which the kernel passes over the input image. A stride of 2 moves the kernel in 2 pixel increments.

Padding – we can add layers of 0s to the outside of the image in order to make sure that the kernel properly passes over the edges of the image.

Output Layers – how many different kernels are applied to the image.

The output of the convolution process is called the “convolved feature” or “feature map.” Remember: it’s just a filtered version of our original image where we multiplied some pixels by some numbers.


---
## Downsampling with convolutions

```yaml
type: "FullCodeSlide"
key: "2b9e193b79"
```

`@part1`
```python

# convolutions are defined by 3 x 3 kernels with stride = 1
nn.Conv2d(in_channels = 5, out_channels = 5, kernel_size=3, 
          stride=1, padding=0, bias=False)

```

`stride`: is the distance in both rows and columns between applications of the convolution filter

`padding`: filling applied to the borders of the image

`bias`: refers to the inclusion of a bias unit that will be trained alongside the weights of the convolution filter


`@script`
`stride`: is the distance in both rows and columns between applications of the convolution filter, a stride equal to one means that a step of one will be applied between convolutions

`padding`: filling applied to the borders of the image, here we fill the image with zeros

`bias`: refers to the inclusion of a bias unit that will be trained alongside the weights of the convolution filter, this gives more freedom to the model as it gives one more value to train, we leave that out for now


---
## Upsampling Methods

```yaml
type: "FullSlide"
key: "b3ca88165d"
```

`@part1`
+ Transposed convolution (produces **checkerboard** artifacts) 
+ Nearest neighbors interpolation followed by $1 \times 1$ convolutions
+ Bilinear or bicubic interpolations


`@script`



---
## What is upsampling and why do we use it?

```yaml
type: "FullSlide"
key: "d6d5d80296"
```

`@part1`
+ Upsampling takes as input an image with dimensions $m \times n$ to produce as output an image with dimensions $ (m + k) \times (n + k) $ 

+ Upsampling allows us to **increase the resolution of an image**

![](https://cdn-images-1.medium.com/max/800/1*vPyOJ9-D-s2gzRhraY21YA.png)


`@script`



---
## Upsampling in U-net

```yaml
type: "FullSlide"
key: "ecffa7f52a"
```

`@part1`
+ Upsampling is used in U-net as a **data augmentation** technique to make the network learn **visual saliency** with **few training examples** 

+ Upsampling is part of the **decoder architecture** of the network

![](https://cdn-images-1.medium.com/max/800/1*vPyOJ9-D-s2gzRhraY21YA.png)


`@script`



---
## Let's give it a try!

```yaml
type: "FinalSlide"
key: "4b6438c5d3"
```

`@script`


