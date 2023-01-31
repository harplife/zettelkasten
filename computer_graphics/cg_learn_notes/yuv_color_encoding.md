---
aliases: [What is YUV, YUV, YUV Color Encoding, YCbCr, YPbPr]
tags: [computer_science, computer_vision, WHAT-IS]
status: complete
edited: 2021-12-17
---

# What is YUV Color Encoding
_YUV_ is a color encoding system typically used as part of a [[color_image_pipepine|Color Image Pipeline]]. 

- It defines a color space in terms of one luma component (Y) and two chrominance components, U (blue) and V (red).

- (Below) An example of U-V color plane, with Y value at 0.5 (represented within RGB color gamut)
![[YUV_UV_plane.svg|300]]

- It encodes a color image or video taking into account that human eyes are less perceptive to chrominance(color) than to luminance(brightness), allowing reduced bandwidth for chrominance components, thereby typically enabling transmission errors or compression artifacts to be more efficiently masked by the human perception than using a "direct" RGB representation.

- Although ambiguous, it's easier to think of YUV as model, _YPbPr_ is its application in analog system, and _[YCbCr](https://en.wikipedia.org/wiki/YCbCr)_ in digital system.

- (Below) These retro video cables were used to carry video signal in YPbPr format. Green cable carries Y, blue for Pb and red for Pr.
![[ypbpr_cable.jpg|300]]

source : [wikipedia](https://en.wikipedia.org/wiki/YUV)

## Related Topics
- The root topic for digital colors is [Color Space](https://en.wikipedia.org/wiki/Color_space)
- Check out [Visual Perception](https://en.wikipedia.org/wiki/Visual_perception)
- Check out [Color Vision](https://en.wikipedia.org/wiki/Color_vision)

## Reference
- A really nice note on YUV in Korean - [link](https://aigong.tistory.com/198)