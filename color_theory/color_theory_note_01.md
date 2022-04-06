---
aliases: [Color Theory Note 1]
tags: [computer_vision, computer_graphics, color_theory, study]
status: ongoing
created: 2022-04-01
edited: 2022-04-05
---

# Color Theory Note 1
[빛 (Light)](https://en.wikipedia.org/wiki/Light)은 아주 복잡하다. 빛은 반사되고, 흡수되고, 통과되고, 왜곡되고 별별 특성을 다 갖고 있다. [색 (Color)](https://en.wikipedia.org/wiki/Color)은 빛에서 나오기 때문에, 색도 마찬가지로 복잡하다. 여기서 다루는 내용은 "내가 이해할 수 있는" 수준으로 간단하게 정리한 것이기 때문에, 좀 더 정확한 정보는 따로 리서치 해봐야 한다.

![[light_dispersion_prism.PNG]]

## Color Model
[색 모델 (Color Model)](https://en.wikipedia.org/wiki/Color_model)은 색과 색들의 관계를 수학으로 표현하는 추상적 모델을 뜻한다. 이 뜻은, 색을 하나 또는 여러 숫자로 표현한다거나, 덧셈, 뺄셈 등 색들의 상호작용(혼합)으로 표현한다는 뜻이다.

[색 공간 (Color Space)]는 색 모델을 시각화한 것으로 볼 수 있다. 주로 변수와 변수의 관계를 나타내는 좌표계로 표현된다. 색 모델과 색 공간은 결국엔 같은 것이니, 이 용어들은 자주 혼용된다.

색 모델은 여러 개 있는데, 이 중에 (내가 보기에) 제일 중요한 모델은 밑에와 같다.
1. CIE 1931 색 공간
2. 가산혼합 색 모델
3. 감산혼합 색 모델
4. 원통좌표계 색 모델
5. YUV 색 공간

### CIE 1931 색 공간
[CIE 1931 색 공간](https://en.wikipedia.org/wiki/CIE_1931_color_space)은 가시광선 (Visible Light)의 파장 (Wavelength)과 삼색 자극값 (Tristimulus value)의 관계를 정량적으로 표현한 최초의 색 공간이다.

CIE 1931 색 공간은 CIE RGB, CIE XYZ로 나뉘어 지는데, 일반적으로 CIE 1931 하면 CIE XYZ를 뜻한다. 여기서 다루는 내용도 XYZ를 기준으로 다룬다.

[삼색 자극값 (Tristimulus value)](https://en.wikipedia.org/wiki/CIE_1931_color_space#Tristimulus_values)은 특정 색에 대하여 사람의 눈이 반응하는 수준을 뜻한다.

_좀 더 정확히는_, 망막 (Retina)에 위치한 시세포 (Visual Cell) 중 색상을 구별하는 원추세포 (Cone Cell)는 <span style="background:blue;color:white;">파랑에 반응하는 S cell</span>, <span style="background:green;color:white;">초록에 반응하는 M cell</span>, 그리고 <span style="background:red;color:white;">빨강에 반응하는 L cell</span>로 구성되어 있으며, 특정 색이 각 원추 세포에 자극을 주는 수준을 측정한게 삼색 자극값이다.

![[spectral_sensitivity_of_human_eyes.svg]]

![[spectral_sensitivity_of_human_eyes_2.png]]

http://www.ktword.co.kr/test/view/view.php?m_temp1=6210

https://it-learning.tistory.com/entry/%EB%94%94%EC%8A%A4%ED%94%8C%EB%A0%88%EC%9D%B4-%EA%B3%B5%ED%95%99-09Human-visual-systemRod-cell-Cone-cell

http://hyperphysics.phy-astr.gsu.edu/hbase/vision/visioncon.html#c1

http://hyperphysics.phy-astr.gsu.edu/hbase/vision/colviscon.html#c1

CIE 1936 색 

![[CIE1931XYZ_infographic.jpg]]

https://blog.hunterlab.com/blog/color-measurement/understanding-tristimulus-values-taking-guesswork-color-measurement-instrumentation/

참고 : 인간처럼 특별히 3가지 색상에 민감한 생체를 [trichromat](https://en.wikipedia.org/wiki/Trichromacy)이라 한다.

일반적인 모니터로는 CIE 1931 색 공간의 전체 색들을 볼 수 가 없다. 현재 2022년 기준으로 CIE 1931 색 공간 전체를 보여줄 수 있는 모니터도 없다. 밑에 있는 그림은 단순히 이론적인 좌표계와 추론되는 색을 구현한 것으로, "잘만 보이는데 왜 못본다는 거지?"라는 오해를 하면 안 된다.

![[CIE1931xy.svg]]




참고 : [Luma](https://en.wikipedia.org/wiki/Luma_(video))

참고 : https://stackoverflow.com/questions/596216/formula-to-determine-perceived-brightness-of-rgb-color

![[gray_conversion_comparisons.png]]

참고 : http://www.ktword.co.kr/test/view/view.php?no=3183

#todo 더 자세한 사항은 나중에~

### 가산혼합
[가산혼합 (Additive Color)](https://en.wikipedia.org/wiki/Additive_color)은 3개 색을 혼합하여 모든 색을 구현하는 방식이다.

가산 (Additive)의 의미는 빛이 없는 공간 (검은색)에 빛을 "더하여" 하얀색으로 만든다는 뜻이다. 다른 말로는, 검은색에 각 색을 "더하여" 여러 색을 구현한다는 뜻이다. 최종적으로 모든 색을 최대 비율로 더하면 하얀색이 나온다.

가산혼합에 사용되는 색을 [원색 (Primary Color)](https://en.wikipedia.org/wiki/Primary_color)이라고 부르며, 서로 독립적인 색을 뜻한다 - 서로 독립적인 색은, 둘을 혼합해도 남은 셋째의 색을 만들 수 없다.

#### RGB 색 모델
가산혼합에 일반적으로 사용되는 원색은 RGB: Red, Green, Blue이다. 이 색들을 사용하는 가산혼합을 [RGB 색 모델](https://en.wikipedia.org/wiki/RGB_color_model)이라 부른다.

모든 모니터/프로젝터는 RGB 색 모델을 사용한다.

이론적으로 RGB가 아닌 다른 가산혼합 원색도 있다. 하지만 사람은 RGB 색에 가장 민감하게 반응하기 때문에 RGB가 사용된다.

![[rgb_summation.webp]]

### 감산혼합
[감산혼합 (Subtractive Color)](https://en.wikipedia.org/wiki/Subtractive_color)은 가산혼합과 마찬가지로 3개 색을 혼합하여 모든 색을 구현하는 방식이다.

감산 (Subtractive)의 의미는 빛이 반사하는 공간 (하얀색)에 빛을 "빼서" 검은색으로 만든다는 뜻이다. 다른 말로는, 하얀색에 각 색을 "빼서" 여러 색을 구현한다는 뜻이다. 최종적으로 모든 색을 최대 비율로 빼면 검은색이 나온다.

#### CMY 색 모델
감산혼합에 일반적으로 사용되는 원색은 CMY: Cyan, Magenta, Yellow이다. 이 색들을 사용하는 감산혼합을 [CMY 색 모델](https://en.wikipedia.org/wiki/CMY_color_model)이라 부른다.

모든 인쇄기는 CMY (정확히는 CMYK) 색 모델을 사용한다.

마찬가지로 CMY가 아닌 다른 감산혼합 원색도 있지만, CMY가 "얕은 색"을 구현하기 제일 쉬운 조합이기 때문에 사용된다 (얕은 색에서 찐한 색으로 가는 것은 가능하지만, 그 반대는 불가능하다).

![[color_mixes.png]]

참고: 모니터에 출력되는 색은 인쇄기로 출력된 색과 다르게 보일 수 있다. 서로 색 모델이 다를 뿐더러, 잉크 (Ink)의 한계가 있다. 인쇄기 출력물과 매칭되는 색을 봐야한다면, 포토샵 같은 디자인 전용 프로그램에서 보정을 해줘야 한다.

![[cmyk_conversion.PNG]]

### 원통좌표계 색 모델
원통좌표계 (Cylindrical Coordinates)로 표현되는 색 모델이다.

#### HSL & HSV
[HSL & HSV 색 모델](https://en.wikipedia.org/wiki/HSL_and_HSV)은 

### YUV 색 공간
[YUV 색 공간](https://en.wikipedia.org/wiki/YUV)은 [휘도 (Luminance)](https://en.wikipedia.org/wiki/Relative_luminance)와 [색차 (Chrominance)](https://en.wikipedia.org/wiki/Chrominance)의 관계를 표현한다.

참고 : 색에서 밝기만 따로 추출한게 휘도, 색상만 따로 추출한게 색차라고 볼 수 있다.

![[YUV_UV_plane.svg]]

![[luminance_chrominance_comparison.PNG]]

#todo Luminance, Relative Luminance, Luma의 차이를 잘 모르겠다..

[YCbCr 색 공간](https://en.wikipedia.org/wiki/YCbCr)
