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
Hi! In this video we're going to overview the architecture of the U-net network for semantic segmentation, which is the main deep learning algorithm that we will explore in the course.


---
## State-of-the-art in semantic image segmentation

```yaml
type: "FullSlide"
key: "18ebf1ba91"
```

`@part1`
![u-net paper](https://raw.githubusercontent.com/andandandand/images-for-colab-notebooks/master/u-net-paper.png)


`@script`
The paper describing this network was published in 2015. It's original version is the current benchmark against which other semantic segmentation algorithms are compared.


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
Variations of the U-net architecture currently rank as the top performers in Kaggle image segmentation competitions such as the 2018 Data Science Bowl.


---
## Carvana Challenge

```yaml
type: "FullSlide"
key: "da59395e65"
```

`@part1`
![carvana](https://assets.datacamp.com/production/repositories/3732/datasets/bebc3d87266f391b1bac3c3d92c9f1d945f99148/carvana.png)


`@script`



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

In U-net, in order to label pixels as belonging to a particular image class, we map a convolution operation from original or downsampled images to a synthetic or upsampled image. 

This encoding of features is done in the encoder part of the network, which is the left side of the "U" that we see in the diagram. 

When we encode features we "downsample" the image, this means that we reduce its size and pick fragments of it.  

In the decoder, we do a lossy reconstruction of the original image size in the decoder so that we can classify every pixel in the original image using slightly altered versions of the image as "built-in" training examples.

This is a type of "hardwired" data augmentation technique that allows the network to learn features with relatively few training images. 

We're gonna start exploring the role of convolutions in the architecture.


---
## $3 \times 3$ Convolutions

```yaml
type: "FullSlide"
key: "be71e7aa5d"
```

`@part1`
![convolutions](http://deeplearning.stanford.edu/wiki/images/6/6c/Convolution_schematic.gif)


`@script`
Since an image is just a matrix of pixel values, applying a convolution means multiplying small parts of our input images by the filter, which is also a matrix. This small kernel matrix gets updated with the backpropagation algorithm and is comprised of weights that are trained and modified so that they reduce the pixel labeling error.


---
## Downsampling with convolutions in PyTorch

```yaml
type: "FullSlide"
key: "ddbf8a548f"
```

`@part1`
```python

# convolutions are defined by 3 x 3 kernels with stride = 1
nn.Conv2d(in_channels = 5, out_channels = 2, kernel_size=3, 
          stride=1, padding=0, bias=False)

```

`in_channels`: number of channels in the input image

`out_channels`: number of channels in the output image of learned features, also the **number of different kernels** that are applied to the input channels, each kernel will have different trained weights

`kernel_size`: square dimension of each convolution filter, $3 \times 3$ here


`@script`
Here we look at a sample convolution in PyTorch
 
`in_channels`: refers to the number of channels in the input image

`out_channels`: refers to the number of channels in the output image of learned features, also the **number of different kernels** that are applied to the input channels, each kernel will have different trained weights

`kernel_size`: square dimension of each convolution filter, $3 \times 3$ here


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
`stride`: is the distance in both rows and columns between applications of the convolution filter

`padding`: filling applied to the borders of the image

`bias`: refers to the inclusion of a bias unit that will be trained alongside the weights of the convolution filter, giving the network more generalization power


---
## Let's give it a try!

```yaml
type: "FinalSlide"
key: "4b6438c5d3"
```

`@script`


