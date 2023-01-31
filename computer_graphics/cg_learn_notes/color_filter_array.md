---
aliases: [What is CFA, Color Filter Array, CFA, How Digital Cameras work]
tags: [computer_science, computer_vision, WHAT-IS, HOW, camera]
status: complete
edited: 2021-12-17
---

# What is Color Filter Array
A _Color Filter Array (CFA)_ is a mosaic of tiny color filters placed over the pixel sensors of an image sensor (inside a camera) to capture color information.

- aka Color Filter Mosaic (CFM)

- (Below) An example of CFA, _Bayer Filter_, which is a 2x2 filter that uses one blue, one red, and two greens. It is a very common filter.
![[Bayer_pattern_on_sensor.svg|300]]

- Color Filters are needed because the typical photosensors only detect light intensity and cannot separate color information.

- Color Filters filter the light by wavelength range (e.g. Red, Blue, Green).

- The raw image data captured by the image sensor (using a CFA filter) is converted back to a full-color image by _[Demosaicing](https://en.wikipedia.org/wiki/Demosaicing)_, which is also referred to as "De-Bayering" or "CFA interpolation".

- The responses of the filters do not generally correspond to the [CIE color matching functions](https://en.wikipedia.org/wiki/CIE_1931_color_space#Color_matching_functions), so a color translation is required to convert the [tristimulus values](https://en.wikipedia.org/wiki/CIE_1931_color_space#Tristimulus_values) into a common, [absolute color space](https://en.wikipedia.org/wiki/Color_space#Absolute_color_space).
__(Author's note)__ basically, how a filter sees color doesn't exactly match how a human sees color. Therefore, colors that are captured by the filter needs to be converted.

- Foveon X3 sensor is one image sensor that doesn't require a demosaicing, because its sensors are on top of each other. Its approach is referred to as "Vertical color filter", whereas CFA is "lateral color filter".

- There are many other variations of CFA, other than the classic Bayer Filter. I guess it's worth checking out which filter is used for any camera.

Source : [wikipedia](https://en.wikipedia.org/wiki/Color_filter_array)

## Side Note
This note basically summarizes out how Digital Cameras work; there is an image sensor that consists of tiny pixel sensors (e.g. megapixel) with a CFA filter that captures color information, which is then also ran through demosaicing and other filters to convert the information back to an image.

## Video
There is a nice video explaining how CFA works - ["Capturing Digital Images (The Bayer Filter) by Computerphile"](https://www.youtube.com/watch?v=LWxu4rkZBLw)

## Related Topics
- Paper: [Demosaicing First or Denoising First?](https://www.researchgate.net/publication/340939215_A_Review_of_an_Old_Dilemma_Demosaicking_First_or_Denoising_First). Spoiler, demosaicing first.
- [[color_image_pipepine|Color Image Pipeline]]