---
title: Insert title here
key: 40c35dedada5fea64f36b2ea85529d2d

---
## Upsampling Images  with the Transposed Convolution

```yaml
type: "TitleSlide"
key: "54e0c04494"
```

`@lower_third`

name: Antonio Rueda-Toicen
title: Research Programmer at Algorithmic Dynamics Lab


`@script`
In this video we're going to explore the workings of a particularly powerful upsampling technique which is the transposed convolution. The transposed convolution is one of the main components of the original U-net segmentation algorithm and it's used in the 'decoder' of the network to perform upsampling.   

The transposed convolution takes as input an image with size $m \times n$ and produces as output an image of size $(m + k) \times (n + k)$   

The transposed convolution is an alternative to both the nearest neighbor and bilinear interpolation techniques and differs from them in that it's trained alongside the network, whereas these other techniques work in a fixed manner.

It's important to be aware that for any particular segmentation task, there's no guarantee that the tranposed convolution will outperform its simpler competitors according to the error metric of the algorithmm.


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


