---
aliases: [How does image compression work, Image Compression]
tags: [computer_science, computer_vision, HOW, image, compression]
status: ongoing
edited: 2021-12-18
---

# How does image compression work
(2021-12-18: this is a very quick note that needs more detail)

When it comes to compression, there are two types:
- _Lossy_, meaning some data are lost during compression
- _Lossless_, meaning no data are lost during compression

`.png` image file is typical example of a lossless compression.

`.jpg` image file is typical example of a lossy compression.

NOTE: it would be more fitting to have a separate note about compression (general). Refer to the Youtube playlist on [Information Theory by Professor Brailsford - Computerphile](https://www.youtube.com/playlist?list=PLzH6n4zXuckpKAj1_88VS-8Z6yn9zX_P6).

## Lossy Compression
There are several ways implementing lossy compression, but the most commonly used is the [JPEG](https://en.wikipedia.org/wiki/JPEG).

### How JPEG works
The term "JPEG" is an acronym for the Joint Photographic Experts Group, which created the standard in 1992.

Note that [JFIF](https://en.wikipedia.org/wiki/JPEG_File_Interchange_Format) is a supplementary specifications for the JPEG. Most of the times, when anyone refers to the JPEG, they are referring to the JFIF.

The JPEG compression process:
1. Convert RGB to [[yuv_color_encoding|YCbCr]]. The rest of the steps apply to each of the channel (Y, Cb, Cr).
2. Apply 8x8 [Discrete Cosine Transform](https://en.wikipedia.org/wiki/Discrete_cosine_transform). This step reduces a huge amount of high frequency information in color. Check out this [video](https://youtu.be/Q2aEzeMDHMA) to see the whole process applying DCT.
3. Serialize the output of DCT (Transform Coefficients) into a long line with a Zig-Zag scan.
4. Apply [Entropy Coding](https://en.wikipedia.org/wiki/Entropy_coding), such as [Huffman Coding](https://en.wikipedia.org/wiki/Huffman_coding).

There are some minor details removed, but that's the gist of it.

For better understanding of the whole process, check out this Youtube playlist, [How JPEG works](https://youtube.com/playlist?list=PLzH6n4zXuckoAod3z31QEST1ZaizBuNHh) by Computerphile (feat. [Mike Pound](https://en.wikipedia.org/wiki/Michael_Pound)).

#### High Frequency in Color
During the JPEG compression process, "High Frequency" color information is reduced. _High Frequency_, in this context, means there are a lot more details within a block of image; details being level of changes in intensity.

An example of a low frequency information, if intensity was described by 0 and 1, would be a block that consists mostly of 0s, or a block with mostly 1s.

High frequency information, in this case, is a block with each pixel alternating between 0 and 1 - like 0,1,0,1,0,1 - creating something like a checker board.

Visually, if we were to reduce high frequency information, we would see loss of sharpness. Edges, where there are high contrast between two sides, would be a bit blurred. Check out Compression Artifact below.

#### Human Perception on Color
Humans are more sensitive to brightness than to colors.
The JPEG compression uses this fact and applies heavier compression on color than on brightness.

#### Compression Artifact
Below is an example image of lossy compression at work, with high compression going from right-to-left (higher quality left-to-right).

![[gradual_compression.png|300]]

For more info on visual aspect of lossy compression, check out [Compression Artifact](https://en.wikipedia.org/wiki/Compression_artifact).