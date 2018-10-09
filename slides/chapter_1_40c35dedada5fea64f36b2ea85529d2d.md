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
In this video we're going to explore the architecture of the U-net network for semantic segmentation. U-net has been shown to be one of the most successful image segmentation methhods based on deep learning and convolutional networks. Variations of the U-net architecture usually rank as the the top performers in Kaggle image segmentation competitions.


---
## Encoder and decoder u-net architecture

```yaml
type: "FullSlide"
key: "6c8db6333f"
```

`@part1`
![](https://cdn-images-1.medium.com/max/800/1*dKPBgCdJx6zj3MpED3lcNA.png)


`@script`
In the semantic segmentation algorithm U-net, in order to label pixels as belonging to a particular image class we map a convolution operation from original or downsampled images high image to a synthetic or upsampled image, as the image at the right shows. We're going to explore in detail each of these operations. 

This extraction of features is done in the encoder part of the network, which is the left side of the "U" that we see in the diagram. 

When we extract features we "downsample" the image, this means that we reduce its size and pick fragments of it.  

We then "restore" the original image size in the decoder so that that we can classify every pixel in the original image.


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


