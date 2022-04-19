---
aliases: [Color Theory Note 1]
tags: [computer_vision, computer_graphics, color_theory, study]
status: ongoing
created: 2022-04-01
edited: 2022-04-14
---

# Color Theory Note 1
[빛 (Light)](https://en.wikipedia.org/wiki/Light)은 아주 복잡하다. 빛은 반사되고, 흡수되고, 통과되고, 왜곡되고 별별 특성을 다 갖고 있다. [색 (Color)](https://en.wikipedia.org/wiki/Color)은 빛에서 나오기 때문에, 색도 마찬가지로 복잡하다.

색을 연구하는 것을 색체 과학/공학 (Color Science)이라고 한다. 흔한 분야는 아니고, 디자인 분야하고 많이 헷갈린다 (마치 음향 공학처럼).

물리학에서 빛/색을 연구하는 분야를 Chromatic 으로 부른다. 근데 Chromatic은 음악 분야에 너무 많이 사용되는 단어라, 색과 관련된 Chromatic은 구글 검색에서도 잘 안 뜬다.

과학과 기술을 동원해 정량적으로 색을 측정하는 것을 [색 측정법 (Colorimetry)](https://en.wikipedia.org/wiki/Colorimetry)이라고 한다.

여러 이름들이 있어서 좀 복잡한데, [Color Vision](https://en.wikipedia.org/wiki/Color_vision)이 그나마 좀 잘 검색되는 것 같다.

색은 광원-물체-관찰자의 관계로 이루어지기 때문에, 색을 이해하려면 물리학, 화학, 생물학, 신경과학, 심리학 등 여러 분야에 이해도가 좀 있어야 된다.

![[relationship_of_color.png]]

여기서 다루는 내용은 "내가 이해할 수 있는" 수준으로 간단하게 정리한 것이기 때문에, 좀 더 정확한 정보는 따로 리서치 해봐야 한다.

![[light_dispersion_prism.PNG]]

## 가시광선
[가시광선 (Visible Light)](https://en.wikipedia.org/wiki/Visible_spectrum)은 사람의 눈에 보이는 [전자기파](https://en.wikipedia.org/wiki/Electromagnetic_spectrum)의 영역을 뜻한다.

![[electromagnetic_spectrum.webp]]

가시광선의 주파수 (Frequency) 추정 범위 : $4 \times 10^{14}$ hz ~ $8 \times 10^{14}$ hz (400 THz ~ 800 THz)

가시광선의 파장 (Wavelength) 추정 범위 : 750 nm ~ 380 nm

참고 : [적외선 (Infrared)](https://en.wikipedia.org/wiki/Infrared)과 [자외선 (Ultraviolet)](https://en.wikipedia.org/wiki/Ultraviolet)은 가시광선에 속하지 않지만 전용 기기를 사용하여 관측할 수 있다.

### 단색광
물리학에선 단일 주파수 (Single Constant Frequency)로 진동하는 전자기파를 [Monochromatic Radiation](https://en.wikipedia.org/wiki/Monochromatic_radiation)이라 부른다. 따라서, 단일 주파수로 진동하는 빛 또는 단일 파장으로 대표되는 좁은 파장 범위에 포함되는 빛을 __Monochromatic Light__ 이라 부르며, 일반적으로는 [단색광 (Spectral Color)](https://en.wikipedia.org/wiki/Spectral_color)이라 부른다.

무지개 색이 무엇이냐~하면 단색광 색이 무엇인지 묻는거와 동일하다. [빨주노초파남보 (Roy G. Biv)](https://en.wikipedia.org/wiki/ROYGBIV) 라고 답할 수 있지만, 사실 가시광선의 영역은 연속적이기 때문에 단색광은 무한 (infinity)개 있다. 더불어, 완전한 단색광을 재현하는 것은 어렵다 (이유는 양자역학에 관련된 것 같아서 이해하는 것을 포기했다).

우리는 일반적으로 단색광을 7가지 색으로 분류한다 - 이는 1704년도에 출판된 [아이작 뉴턴 (Isaac Newton)](https://en.wikipedia.org/wiki/Isaac_Newton)의 책 [_Opticks_](https://en.wikipedia.org/wiki/Opticks) 에 명시된 [색 상환 (Color Cicle)](https://en.wikipedia.org/wiki/Color_wheel)으로부터 비롯되었다.

![[isaac_newton_opticks_color_circle.PNG]]

> | **color** | **Wavelength (nm)** | **Frequency (THz)** |
|:---------:|:-------------------:|:-------------------:|
|<span style="color:#7f00ff;">&block;</span> violet   |       380~450       |       670~790       |
|<span style="color:blue;">&block;</span> blue     |       450~485       |       620~670       |
|<span style="color:cyan;">&block;</span> cyan     |       485~500       |       600~620       |
|<span style="color:#00FF00;">&block;</span> green    |       500~565       |       530~600       |
|<span style="color:yellow;">&block;</span> yellow   |       565~590       |       510~530       |
|<span style="color:orange;">&block;</span> orange   |       590~625       |       480~510       |
|<span style="color:red;">&block;</span> red      |       625~750       |       400~480       |
> 단색광을 최대한 근접하게 (Approximation) 표현하여 사람이 구분할 수 있는 영역으로 나누어 보이는 색상들

단색광은 사람이 볼 수 있는 모든 색이 포함된게 아니다. 하지만 어떻게 보면 단색광은 사람이 볼 수 있는 모든 색의 경계점이라 볼 수 있다 - 모든 색은 단색광의 조합으로 이루어진다고 생각하면 될 것 같다.

참고 자료 1 : [사이언스올 과학백과사전 - 단색광](https://www.scienceall.com/%EB%8B%A8%EC%83%89%EA%B4%91monochromatic-light-3/)

### 광원
[광원 (Light Source)](https://en.wikipedia.org/wiki/Light#Light_sources)은 제 스스로 빛을 발하는 물체 또는 장치를 뜻한다.

광원을 제대로 이해하기 위해서는 물체가 어떻게 빛을 발하는지 좀 이해해야 할 필요가 있다 - 특히 빛 중에 제일 대빵이라고 볼 수 있는 [태양광 (Sunlight)](https://en.wikipedia.org/wiki/Sunlight)을 이해해야 한다.

우리는 어릴때 불 (Fire)과 태양 (Sun)을 보면서 "뜨거운 것은 밝게 빛난다"를 배운다. 좀 더 나아가, 토마스 에디슨 (Thomas Edison)의 발명품, [백열등 (Incandescent Light Bulb)](https://en.wikipedia.org/wiki/Incandescent_light_bulb)에 대하여 배우며 전기로 물체를 가열시키면 빛이 난다는 것을 배운다.

열과 빛이 관련이 있다는 사실, 이 개념은 [흑체 복사](http://www.ktword.co.kr/test/view/view.php?m_temp1=3907) [(Blackbody Radiation)](https://en.wikipedia.org/wiki/Black-body_radiation)로부터 비롯된다 (아마도). 흑체 복사에 대하여 설명하긴 너무 어려워서 일단 핵심 내용만 알아본다.
1. 흑체 (Blackbody)는 모든 파장의 전자기파를 완전히 흡수하는 가상/이상의 물체이다. __밀도를 가진 모든 물체는 에너지를 흡수하고 방출한다. 모든 물체는 흑체이지만, 완벽한 흑체는 아니다.__ 완벽한 흑체는 이론적으로만 가능하기 때문에 가상/이상의 물체라고 하는 것이다.
2. 흑체 복사 (Blackbody Radiation)는 가열된 흑체에서 나오는 [전자기파](https://en.wikipedia.org/wiki/Electromagnetic_radiation)이다.
3. 흑체 복사는 [열복사 (Thermal Radiation)](https://en.wikipedia.org/wiki/Thermal_radiation)이라 불리기도 한다.
4. 흑체 복사는 여러 범위의 주파수/파장으로서 이루어지며, (열이 충분히 높으면) 그 중 일부가 가시광선 영역에 있다. 온도에 따라서 색상 (Hue)도 변한다 - 그래서 광원의 색을 명시할 때 Kelvin (K) 단위의 [색 온도 (Color Temperature)](https://en.wikipedia.org/wiki/Color_temperatur)로 표현하게 된다.

태양 (Sun)과 별들은 거~의 흑체라고 한다.

> ![[Color_temperature_black_body_800-12200K.svg]]
> 우주에 빛나는 별들의 색 & 색 온도 (800 K ~ 12,200 K)

인간의 눈은 태양광에 최적화가 되어있다. 따라서, 어느 특정 물체의 색 (Color)을 볼때 태양광 또는 태양광에 가장 유사한 빛을 물체에 빛추어 보는게 제일 선호된다. 참고로, 색은 조건에 따라서 다르게 보일수 있기 때문에 ([[#메타메리즘]]), 어느 물체의 색을 구분할 때 최대한 일정한 환경, 즉, 일정한 광원을 사용하는게 좋다.

참고 자료 : [키르히호프의 복사 법칙 (Kirchhoff's Law of Thermal Radiation)](https://en.wikipedia.org/wiki/Kirchhoff's_law_of_thermal_radiation)

http://www.ccpo.odu.edu/SEES/ozone/class/Chap_4/4_6.htm
https://ko.wikipedia.org/wiki/%EB%B9%9B
[방전등](https://en.wikipedia.org/wiki/Gas-discharge_lamp)

#### Standard Illuminant



## 반사와 투사?

https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=loveandpic&logNo=220356463987

## 인간 생체 관련 노트


## Color Model
[색 모델 (Color Model)](https://en.wikipedia.org/wiki/Color_model)은 색과 색들의 관계를 수학으로 표현하는 추상적 모델을 뜻한다. 이 뜻은, 색을 하나 또는 여러 숫자로 표현한다거나, 덧셈, 뺄셈 등 색들의 상호작용(혼합)으로 표현한다는 뜻이다.

[색 공간 (Color Space)]는 색 모델을 시각화한 것으로 볼 수 있다. 주로 변수와 변수의 관계를 나타내는 좌표계로 표현된다. 색 모델과 색 공간은 결국엔 같은 것이니, 이 용어들은 자주 혼용된다.

색 모델/공간의 궁극적인 목표는 특정 색을 구현하기 위해 필요한 요소들의 값을 구할 수 있는 등색 함수 (Color Matching Function)를 제공함에 있다 (예: 초록 = 파랑 + 노랑).

색 모델은 여러 개 있는데, 이 중에 (내가 보기에) 제일 중요한 모델은 밑에와 같다.
1. CIE 1931 색 공간
2. 가산혼합 색 모델
3. 감산혼합 색 모델
4. 원통좌표계 색 모델
5. YUV 색 공간

### CIE 1931 색 공간
[CIE 1931 색 공간](https://en.wikipedia.org/wiki/CIE_1931_color_space)은 가시광선 (Visible Light)의 파장 (Wavelength)과 삼자극값 (Tristimulus value)의 관계를 정량적으로 표현한 최초의 색 공간이다.

CIE 1931 색 공간은 CIE RGB, CIE XYZ로 나뉘어 지는데, 일반적으로 CIE 1931 하면 CIE XYZ를 뜻한다. 여기서 다루는 내용도 XYZ를 기준으로 다룬다.

#### 삼자극값
[삼자극값 (Tristimulus value)](https://en.wikipedia.org/wiki/CIE_1931_color_space#Tristimulus_values)은 특정 색을 나타내는데 필요한 3 색상 (RGB)의 혼합비율을 뜻한다.

인간처럼 특별히 3가지 색상에 민감한 생체를 [삼색형 색각자 (trichromat)](https://en.wikipedia.org/wiki/Trichromacy)라 한다. 망막 (Retina)에 위치한 시세포 (Visual Cell) 중 색상을 구별하는 [원추세포 (Cone Cell)](https://en.wikipedia.org/wiki/Cone_cell)는 <span style="background:blue;color:white;">파랑에 반응하는 S-cone</span>, <span style="background:green;color:white;">초록에 반응하는 M-cone</span>, 그리고 <span style="background:red;color:white;">빨강에 반응하는 L-cone</span>, 이 3 종류로 구성되어 있다.

![[how_the_eye_sees_color.PNG]]

![[spectral_sensitivity_of_human_eyes_4.svg]]

여기서 자극/반응은 

각 원추 세포는 어느 특정 색 하나를 구별하는게 아니다. 여러 색들을 감지하되, 다른 원추 세포에 비해 더 많이 자극을 받는 색이 있는 것이다.

RGB 색 공간 위주로 봤을때, 원추 세포는 초록에 가장 반응이 크고, 다음은 빨강, 마지막으로 파랑이다. 이 정보가 중요한 이유는, RGB 색 공간에서 [상대적 밝기 (Relative Luminance)](https://en.wikipedia.org/wiki/Relative_luminance)를 추출할 때 이 정보를 기준으로 만들어진 공식을 사용하기 때문이다. 참고로, 현실 세계에서는 노랑-초록색에 가장 반응이 크다.

"자극값"은 어떤 단위의 값이라기 보다는 상대적 (Relative) 값이다.

삼자극값을 좀 더 이해하려면, [[#메타메리즘]]

#### 메타메리즘


[메타메리즘 (Metamerism)](https://en.wikipedia.org/wiki/Metamerism_(color)) : 광원, 관측자, 관측조건 차이에 따라 두 물체의 색이 같아 보이거나 달라 보이는 현상을 뜻한다. 조건 등색으로 불리기도 한다.

![[metamerism.PNG]]


[[#삼자극값]]을 구하기 위한 테스트를 [Metameric Color Matching (MCM)](https://isle.hanover.edu/Ch06Color/Ch06ColorMatchExp.html)이라고 한다. 테스트 방식을 간단히 설명하자면,
1. 벽 앞에는 여러개의 조명들이 있고, 벽 뒤에는 __관찰자 (Standard Observer)__ 가 있다.
2. 벽에는 구멍이 있어, 관찰자가 구멍을 통해 벽 앞을 바라볼 수 있다.
3. 벽 앞에는 가운데 칸막이로 나누어진 두 공간이 있다. 한 공간에는 [단색광 (Monochromatic Light)](https://en.wikipedia.org/wiki/Spectral_color)이 특정 색을 비추고 있고, 건너편 공간에는 빨강, 초록, 파랑 조명이 있어 혼합색을 만든다.
4. 관찰자는 빨강, 초록, 파랑 조명의 강도를 조절하여 혼합색과 단색광의 특정 색을 최대한 매칭해본다.
5. 매칭되면 빨강, 초록, 파랑 조명의 강도가 기록된다. 이 강도가 삼자극값이다.

사실 삼자극값은 MCM 테스트의 부산물이라고 볼 수 있다. MCM은 어느 물리적 객체의 색을 구분하기 위한 테스트이다. 예를 들어, 노란색 가방의 "노란색"과 바나나의 "노란색"이 같다/틀리다를 판단하기 위해, 각 객체를 동일한 하얀색 배경에 하얀색 빛 (표준 광원)

참고 : RGB 값이 원추세포가 자극받는 값하고 잘 매칭된다는 이유로 MCM 테스트에서 RGB 조명을 사용했다. 삼자극값이 원추세포의 반응이다~라고 하는게, 사실 여기서 좀 애매해진다.

![[metameric_color_matching_experiment_setup.png]]

위 연구를 실제 진행한 사례들로 1920년도 W. D. Wright 연구와 J. Guild 연구가 있다. 두 연구가 비슷한 시기에 해서 그런지 그냥 Wright-Guild 연구로 불리는 것 같다. Wright-Guild 연구 결과는 CIE 1931 색 모델을 구축하는데 기반이 되었다.

참고 : 1920년 Wright-Guild 연구는 관찰자의 시야각 (Field of View)을 2°로 해서 연구가 진행됬는데, 이 정도 시야각은 팔을 쭉 뻗고 보이는 엄지손가락 정도 크기라고 보면 된다. 이게 너무 작다고 여겨져, 1964년도에 10°(주먹만한 크기)로 변경했다고 한다 - [출처](https://www.konicaminolta.com/instruments/knowledge/color/part4/01.html).

사람마다 생체학적으로 좀 다르기 때문에, 삼자극값도 서로 미세한 차이가 보여진다. MCM 테스트는 실제로 여러 사람들을 대상으로 진행되고, 여러 결과를 취합하여 근사치 (Approximation)를 계산한다.

> ![[Stiles_and_Burch_49_trichromatic_observers_plot.png]]
> 1955년 Stiles and Burch 연구 데이터를 기반으로 plot된 그래프

MSM는 색에 대하여 아주 중요한 두 가지를 증명한다:
1. 
2. __RGB의 한계__ : 사람이 볼 수 있는 색 중 RGB로 구현할 수 없는 색이 있다. 위 그래프를 보면 RGB 값이 음수로 가는 것을 볼 수 있다. 이 뜻은, 반대편 (단색광)에 RGB 조명을 추가해야만이 색들이 매칭될 수 있었다는 것이다.

![[metameric_color_matching_experiment_full_sweep.gif]]

삼자극값은 좀 거창한 정의를 가지고 있지만, MCM 테스트를 이해하고 보면 삼자극값은 그냥 특정 색에 대한 원색 (RGB)의 비율로 볼 수 있다.

서로 다른 파장의 색들을 혼합하여 다른 하나의 색을 구현하는 [[#가산혼합]]의 기반이 된다.

#### 색 공간 시각화
색 (Color)이란 개념적으로 [휘도 (Luminance)](https://en.wikipedia.org/wiki/Luminance)와 [색도 (Chromaticity)](https://en.wikipedia.org/wiki/Chromaticity)의 조합으로 이루어진다. 이 외에 파장 (Wavelength)도 포함된다. 삼자극값의 3개의 값에 3개의 색 정보까지, 이 모두를 하나의 좌표계에 그리는 것은 좀 복잡해지고 이해하기도 난잡해진다. CIE 1931 색 공간은 색의 관계를 이해하기에 필요한 정보만 따로 추출하여 2D 좌표계에 표현한 것이다.

여기서 CIE 1931 색 공간이 만들어진 순서대로 설명을 한다.

우선, 삼자극값을 색도 좌표로 변환한다 - 


#### 참고 자료
참고 : 이 [글](https://medium.com/hipster-color-science/a-beginners-guide-to-colorimetry-401f1830b65a)이 CIE 1931에 대하여 아주 잘 정리해줬다. 위에 내용도 대부분 이 글에서 따온거다. 완전히 다 이해한게 아니기 때문에, 나중에 다시 와서 보는것도 좋을 것 같다.

unrelated: https://www.thenakedscientists.com/

http://www.ktword.co.kr/test/view/view.php?m_temp1=6210

https://it-learning.tistory.com/entry/%EB%94%94%EC%8A%A4%ED%94%8C%EB%A0%88%EC%9D%B4-%EA%B3%B5%ED%95%99-09Human-visual-systemRod-cell-Cone-cell

http://hyperphysics.phy-astr.gsu.edu/hbase/vision/visioncon.html#c1

http://hyperphysics.phy-astr.gsu.edu/hbase/vision/colviscon.html#c1

![[CIE1931XYZ_infographic.jpg]]

https://blog.hunterlab.com/blog/color-measurement/understanding-tristimulus-values-taking-guesswork-color-measurement-instrumentation/

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
