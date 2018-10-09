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
This network was originally proposed in 2012 by a group led by Olaf Ronneberger of Freiburg University.


---
## ISBI Challenge 2012

```yaml
type: "FullSlide"
key: "b112793dea"
center_content: true
```

`@part1`
![segmented neurons](http://brainiac2.mit.edu/isbi_challenge/sites/default/files/Challenge-ISBI-2012-sample-image.png)
+ **Semantic segmentation of neurons in electron microscopy images**


`@script`
U-net outperformed other semantic segmentation methods in the ISBI challenge, that was focused on the segmentation of neurons in electron microscopy.


---
## Data Science Bowl

```yaml
type: "FullSlide"
key: "80305ab9c1"
center_content: true
```

`@part1`
![](https://raw.githubusercontent.com/andandandand/images-for-colab-notebooks/master/data-science-bowl.png)


`@script`
Since then, U-net has been shown to be one of the most successful image segmentation methods based on deep learning and convolutional networks. Variations of the U-net architecture currently rank as the top performers in Kaggle image segmentation competitions.


---
## Encoder-Decoder Architecture

```yaml
type: "FullSlide"
key: "6c8db6333f"
```

`@part1`
![](https://cdn-images-1.medium.com/max/800/1*dKPBgCdJx6zj3MpED3lcNA.png)


`@script`
U-net, in order to label pixels as belonging to a particular image class we map a convolution operation from original or downsampled images to a synthetic or upsampled image. In the next lessons, we're going to explore in detail each of these operations. 

This extraction of features is done in the encoder part of the network, which is the left side of the "U" that we see in the diagram. 

When we extract features we "downsample" the image, this means that we reduce its size and pick fragments of it.  

We then "restore" the original image size in the decoder so that that we can classify every pixel in the original image.


---
## Downsampling with $3 \times 3$ convolutions

```yaml
type: "FullSlide"
key: "ddbf8a548f"
```

`@part1`



`@script`



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
## Test slide with two rows and two columns

```yaml
type: "TwoRowsTwoColumns"
key: "885c2e73d6"
```

`@part1`



`@part2`



`@part3`



`@part4`



`@script`



---
## Test slide with two columns

```yaml
type: "TwoColumns"
key: "912e3c0817"
```

`@part1`



`@part2`



`@script`



---
## Test slide with two rows

```yaml
type: "TwoRows"
key: "da7c4bf5e9"
```

`@part1`



`@part2`



`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "4b6438c5d3"
```

`@script`


