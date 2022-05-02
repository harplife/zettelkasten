---
aliases: [Color Theory Note 1]
tags: [computer_vision, computer_graphics, color_theory, study]
status: ongoing
created: 2022-04-01
edited: 2022-04-22
---

# Color Theory Note 1
[빛 (Light)](https://en.wikipedia.org/wiki/Light)은 아주 복잡하다. 빛은 반사되고, 흡수되고, 통과되고, 왜곡되고 별별 특성을 다 갖고 있다. [색 (Color)](https://en.wikipedia.org/wiki/Color)은 빛에서 나오기 때문에, 색도 마찬가지로 복잡하다.

색을 연구하는 것을 색체 과학/공학 (Color Science)이라고 한다. 흔한 분야는 아니고, 디자인 분야하고 많이 헷갈린다 (마치 음향 공학처럼).

물리학에서 빛/색을 연구하는 분야를 Chromatic 으로 부른다. 근데 Chromatic은 음악 분야에 너무 많이 사용되는 단어라, 색과 관련된 Chromatic은 구글 검색에서도 잘 안 뜬다.

과학과 기술을 동원해 정량적으로 색을 측정하는 것을 [색 측정법 (Colorimetry)](https://en.wikipedia.org/wiki/Colorimetry)이라고 한다.

여러 이름들이 있어서 좀 복잡한데, [Color Vision](https://en.wikipedia.org/wiki/Color_vision)이 그나마 좀 잘 검색되는 것 같다.

왜 이렇게 이름들이 많은지.. 물리학 분야에 빛의 특성을 연구하는 필드를 [광학 (Optics)](https://en.wikipedia.org/wiki/Optics)이라 한다.

색은 광원-물체-관찰자의 관계로 이루어지기 때문에, 색을 이해하려면 물리학, 화학, 생물학, 신경과학, 심리학 등 여러 분야에 이해도가 좀 있어야 된다.

![[relationship_of_color.png]]

![[color_relationship.PNG]]

여기서 다루는 내용은 "내가 이해할 수 있는" 수준으로 간단하게 정리한 것이기 때문에, 좀 더 정확한 정보는 따로 리서치 해봐야 한다.

> ![[light_dispersion_prism.PNG]]
> 색 연구의 시작, [회절격자 (Diffraction Grating)](https://en.wikipedia.org/wiki/Diffraction_grating)

## 가시광선
[가시광선 (Visible Light)](https://en.wikipedia.org/wiki/Visible_spectrum)은 사람의 눈에 보이는 [전자기파](https://en.wikipedia.org/wiki/Electromagnetic_spectrum)의 영역을 뜻한다.

![[electromagnetic_spectrum.webp]]

가시광선의 주파수 (Frequency) 추정 범위 : $4 \times 10^{14}$ hz ~ $8 \times 10^{14}$ hz (400 THz ~ 800 THz)

가시광선의 파장 (Wavelength) 추정 범위 : 750 nm ~ 380 nm

참고 1 : [적외선 (Infrared)](https://en.wikipedia.org/wiki/Infrared)과 [자외선 (Ultraviolet)](https://en.wikipedia.org/wiki/Ultraviolet)은 가시광선에 속하지 않지만 특수 카메라를 사용하여 볼수가 있다.

### 단색광
물리학에선 단일 주파수 (Single Constant Frequency)로 진동하는 전자기파를 [Monochromatic Radiation](https://en.wikipedia.org/wiki/Monochromatic_radiation)이라 부른다. 따라서, 단일 주파수로 진동하는 빛 또는 단일 파장으로 대표되는 좁은 파장 범위에 포함되는 빛을 __Monochromatic Light__ 이라 부르며, 일반적으로는 [단색광 (Spectral Color)](https://en.wikipedia.org/wiki/Spectral_color)이라 부른다.

단색광이란 이름이 좀 어색한데, 그냥 "하나의 색"인 _단색_ 으로 이해해도 크게 문제 없을 듯 하다. 단색광은 그저 하나의 주파수가 하나의 색을 이룬다는 개념을 기준으로 하나의 색을 갖춘 빛이라 보면 된다.

우리가 일반적으로 보는 빛은 여러 주파수로 이루어져 있는 [다색광 (Polychromatic Light)](https://ballpen.blog/조명-다양한-용어-정리/#1__Monochromatic_light_and_Polychromatic_light)이다. 단색광에 제일 근접한 것은 [레이저 (Laser)](https://en.wikipedia.org/wiki/Laser)다.

하나의 주파수가 하나의 색이라면, 여러 주파수면 여러 색이 보여야 한다는 생각이 들 수있다. 사실 여러 색이 "보여지고" 있는게 맞다. 단지, 사람에게는 여러 색이 완벽히 겹치면 하나의 색으로만 보인다. 이러한 색의 조합은 대부분 가시광선 영역에 있지만, 그렇지 않는 색들도 있다 - 이를 [특단색광 (Extra-Spectral Color)](https://en.wikipedia.org/wiki/Spectral_color#Extra-spectral_colors)이라 한다 (대표적인 예는 핑크색이다).

그럼 단색광은 무슨 색일까?

우리는 일반적으로 단색광을 [빨주노초파남보 (Roy G. Biv)](https://en.wikipedia.org/wiki/ROYGBIV)와 같이 7가지 색으로 분류한다 - 이는 1704년도에 출판된 [아이작 뉴턴 (Isaac Newton)](https://en.wikipedia.org/wiki/Isaac_Newton)의 책 [_Opticks_](https://en.wikipedia.org/wiki/Opticks) 에 명시된 [색 상환 (Color Cicle)](https://en.wikipedia.org/wiki/Color_wheel)으로부터 비롯되었다.

![[isaac_newton_opticks_color_circle_cropped.png]]

사실 가시광선의 영역은 연속적 (Continuous)이기 때문에 단색광은 무한 (infinity)개 있다. 더불어, 완전한 단색광을 재현하는 것은 어렵다 (이유는 양자역학에 관련된 것 같아서 이해하는 것을 포기했다). 우리는 색에 대한 소통을 위해 가시광선의 일부 영역들을 단색광으로 최대한 근접하게 (Approximation) 표현하여 구분할 뿐이다.

> | **color** | **Wavelength (nm)** | **Frequency (THz)** |
|:---------:|:-------------------:|:-------------------:|
|<span style="color:#7f00ff;">&block;</span> violet   |       380~450       |       670~790       |
|<span style="color:blue;">&block;</span> blue     |       450~485       |       620~670       |
|<span style="color:cyan;">&block;</span> cyan     |       485~500       |       600~620       |
|<span style="color:#00FF00;">&block;</span> green    |       500~565       |       530~600       |
|<span style="color:yellow;">&block;</span> yellow   |       565~590       |       510~530       |
|<span style="color:orange;">&block;</span> orange   |       590~625       |       480~510       |
|<span style="color:red;">&block;</span> red      |       625~750       |       400~480       |

단색광을 6개로 나누든 7개로 나누든, 몇개로 나누는 것은 크게 상관이 없다. 단색광의 주파수/파장 범위도 마찬가지다. 단지, 다른 사람이 표현하는 단색광이 내가 생각하는 단색광과 주파수/파장 범위에 있어 차이가 있을수도 있다는 것은 인지하면 좋을 것 같다.

참고 : [남색 (Indigo)](https://en.wikipedia.org/wiki/Indigo)을 구분할 수 없는 사람이 꽤 있어서, 단색광 구분에 제외될 때 가 있다.

![[visible_spectrum.svg]]

단색광은 무엇보다 순수한/완전적인 (Pure) 색이기 때문에, 연구가치가 높다. 단색광으로부터 [[#메타메리즘]], [[#가산혼합]], [[#감산혼합]] 같은 이론들이 나온다.

참고 자료 1 : [사이언스올 과학백과사전 - 단색광](https://www.scienceall.com/%EB%8B%A8%EC%83%89%EA%B4%91monochromatic-light-3/)

### 광원
[광원 (Light Source)](https://en.wikipedia.org/wiki/Light#Light_sources)은 제 스스로 빛을 발하는 물체 또는 장치를 뜻한다.

광원을 제대로 이해하기 위해서는 물체가 어떻게 빛을 발하는지 좀 이해해야 할 필요가 있다 - 특히 빛 중에 제일 대빵이라고 볼 수 있는 [태양광 (Sunlight)](https://en.wikipedia.org/wiki/Sunlight)을 이해해야 한다.

우리는 어릴때 불 (Fire)과 태양 (Sun)을 보면서 "뜨거운 것은 밝게 빛난다"를 배운다. 좀 더 나아가, 토마스 에디슨 (Thomas Edison)의 발명품, [백열등 (Incandescent Light Bulb)](https://en.wikipedia.org/wiki/Incandescent_light_bulb)에 대하여 배우며 전기로 물체를 가열시키면 빛이 난다는 것을 배운다.

열과 빛이 관련이 있다는 사실, 이 개념은 흑체 복사 (Blackbody Radiation)로부터 비롯된다 (아마도). 흑체 복사에 대하여 설명하긴 너무 어려워서 일단 핵심 내용만 알아본다.
1. [흑체 (Blackbody)](https://en.wikipedia.org/wiki/Black_body)는 모든 파장의 전자기파를 완전히 흡수하는 가상/이상의 물체이다. __밀도를 가진 모든 물체는 에너지를 흡수하고 방출한다. 모든 물체는 흑체이지만, 완벽한 흑체는 아니다.__ 완벽한 흑체는 이론적으로만 가능하기 때문에 가상/이상의 물체라고 하는 것이다.
2. [흑체 복사](http://www.ktword.co.kr/test/view/view.php?m_temp1=3907) [(Blackbody Radiation)](https://en.wikipedia.org/wiki/Black-body_radiation)는 가열된 흑체에서 나오는 [전자기파](https://en.wikipedia.org/wiki/Electromagnetic_radiation)이다.
3. 흑체 복사는 [열복사 (Thermal Radiation)](https://en.wikipedia.org/wiki/Thermal_radiation)이라 불리기도 한다.
4. 흑체 복사는 여러 범위의 주파수/파장으로서 이루어지며, (열이 충분히 높으면) 그 중 일부가 가시광선 영역에 있다. 온도에 따라서 색상 (Hue)도 변한다 - 그래서 광원의 색을 명시할 때 Kelvin (K) 단위의 [색 온도 (Color Temperature)](https://en.wikipedia.org/wiki/Color_temperatur)로 표현하게 된다.

불은 뜨거울수록 파랑색으로 변한다고 들었는데, 색 온도를 보면 딱 그 말이 떠오른다. 

![[Color_temperature_black_body_800-12200K.svg]]

태양 (Sun)과 별들은 거~의 완벽한 흑체라고 한다.

인간의 눈은 태양광에 최적화가 되어있다. 따라서, 어느 특정 물체의 색 (Color)을 볼때 태양광 또는 태양광에 가장 유사한 빛을 물체에 빛추어 보는게 제일 선호된다.

![[sunlight_spectrum_comparison_02.PNG]]

[분광 분포 (Spectral Power Distribution)](https://en.wikipedia.org/wiki/Spectral_power_distribution)로 봤을때 가시광선 영역 전체가 연속적\*으로 이어진 빛을 [Full Spectrum Light (FSL)](https://en.wikipedia.org/wiki/Full-spectrum_light)이라고 한다. 한 마디로, FSL은 가시광선의 모든 색을 방출한다 - 이론적인 하얀색 (White)에 제일 가깝다고 보면 될 것 같다.

\* 연속성 (Continuity) : 빛의 여러 주파수 사이에 급격한 하락이 없이 쭉 이어진다. 빛이 가시광선의 모든 주파수를 포함한다는 뜻이며, 그만큼 모든 색을 갖추고 있다.

태양광이 FSL이다. 태양광은 모든 색을 연속적으로 방출한다.

![[color_temperature_spectral_distribution.png]]

분광 분포의 연속성은 광원의 질 (Quality)로 이어진다. #todo 아직 완전히 정리되지는 않았지만, 질은 분명 색감 (색으로부터 받는 느낌)에 영향을 준다.

어떤 물체를 태양광으로 비추어본 것과 형광등으로 비추어본 것에는 색에 아주 미세한 차이가 있겠지만, 태양광으로 비추어진 색이 훨씬 생생 (Vibrant)할 것이라 생각한다 (증명할 방법은.. 뭐, 없다).

![[sun_vs_flourescent_spectrum_comparison.PNG]]

태양광과 백열등은 흑체 복사 기반 광원에 속한다. 반면에, 형광등과 LED는 복사 기반 광원이 아니다. 광원은 꼭 흑체 복사 기반이어야 하는 것은 아니다. 단지, 색의 연구는 태양광이 기초가 되었기에 흑체 복사에 대한 이해가 중요할 뿐이다.

#todo [광원의 종류](https://en.wikipedia.org/wiki/List_of_light_sources)는 많은데, 굳이 이 섹션에서 다룰 필요는 없을 것 같다.

참고 자료 1 : [키르히호프의 복사 법칙 (Kirchhoff's Law of Thermal Radiation)](https://en.wikipedia.org/wiki/Kirchhoff's_law_of_thermal_radiation)
참고 자료 2 : [How objects emit radiation](http://www.ccpo.odu.edu/SEES/ozone/class/Chap_4/4_6.htm)

#### 표준 광원
색은 조건에 따라 다르게 보일수 있기 때문에 ([[#메타메리즘]]), 물체의 색을 (전문적으로) 구분할 때 최대한 일정하고 적합한 환경을 구성하는게 중요하다. 대중적으로 많이 사용되는 광원이 주로 이 용도로 선택된다.

[표준 광원 (Standard Illuminant)](https://en.wikipedia.org/wiki/Standard_illuminant)은 색을 기준으로 물체와 광원의 관계를 표준화하기 위해 사용되는 광원을 뜻한다. 간단하게, 물체의 색을 구분할 때 적합한 광원이라 볼 수 있다.

표준광원은 어느 특정 브랜드, 모델을 확정지는게 아니다 - 표준광원은 이론적 (Theoretical)일 뿐이다. 한 마디로, "최대한 이 정도 수준의 광원을 사용하시오~"하는게 표준광원이라 볼 수 있다.

표준광원은 용도에 따라 여러 종류가 있다.

1. _광원 A_ : 일반적으로 사용되는 백열등 (텅스텐 필라멘트, 색온도 2856 K)
2. _광원 B_ : 대낮 태양의 평균 태양광 (색온도 4900 K)
3. _광원 C_ : 흐른 하늘 낮의 평균 태양광 (색온도 6800 K)
4. _광원 D 시리즈_ : 실제 대낮의 태양광을 측정하여 얻은 평균 직사량
5. _광원 E_ : ??? 이해하는 것 포기
6. _광원 F 시리즈_ : 일반적인 형광등 수준

위 목록 외에 더 있음을 참고해야 한다. 시리즈는 해당 표준광원에 하위 카테고리가 있다는 뜻이다.

참고 자료 1 : [정보통신기술용어해설 - 표준 광원](http://www.ktword.co.kr/test/view/view.php?m_temp1=4526)

## 물체와 빛의 상호작용

빛은 [[#반사]], [[#투과]], 흡수 (Absorption)라는 세 가지 중요한 성질을 갖는다. 그 외에 굴절 (Refraction), 회절 (Diffraction), [[#산란]], 분산 (Dispersion) 등이 있다.

![[surface_effects_illumination.png]]

![[light_properties.png]]

더 자세히 설명하기 전에 일단 빛에 대한 용어를 정의할 필요가 있다. 굳이 물리학적으로 복잡하게 정리하진 않는다 ㅎ.

일단 앞으로 빛을 광선으로 표현한다 - [광선 (Ray)](https://en.wikipedia.org/wiki/Ray_(optics))은 빛의 이상적인 모델로서 에너지 흐름의 방향을 가르키는 선으로 표현되며, 실제 빛의 [파면 (Wavefront)](https://en.wikipedia.org/wiki/Wavefront)에 수직 (Perpendicular)인 선을 선택함으로써 얻을 수 있다. 광선은 광학계 (Optical System)를 통한 빛의 전달을 모델링하는데 사용된다.

![[wavefronts_and_ray.png]]

빛은 파동이기 때문에 모델링하기 엄청 번거롭다! 심지어 양자역학 (Quantum Mechanics)과 관련되어 빛이 [파동-입자 이중성 (Wave-Particle Duality)](https://en.wikipedia.org/wiki/Wave%E2%80%93particle_duality)을 가진다고 하니, 이런걸 어떻게 모델링 할까? 결국에 답은 아주 간단하게 선 하나 그리는 것이고, 그게 바로 광선이다.

물체와 상호작용을 하기 전/후를 기준으로 광선은 세 가지로 분류된다.
1. 입사
2. 반사
3. 투과

![[plane_of_incidence.PNG]]

입사파 (Incident Wave) 또는 __입사광선 (Incident Ray)__ 은 물체를 향해 다가가는 광선을 뜻한다.

반사파 (Reflected Wave) 또는 __반사광선 (Reflected Ray)__ 은 물체 표면에 부딛혀 반사되어 나오는 광선을 뜻한다.

투과파 (Transmitted Wave) 또는 __투과광선 (Transmitted Ray)__ 은 물체를 통과하는 빛을 뜻한다. __굴절파 (Refracted Wave)__ 라고 표현되기도 하는데, 이는 광선이  물체를 통과할 때 방향이 틀어진 광선을 뜻한다.

![[types_of_ray.svg]]

용어를 정의했으니, 다시 돌아와서 반사, 투과, 흡수에 대해서 정리해본다.

### 반사
[반사 (Reflection)](https://en.wikipedia.org/wiki/Reflection_(physics))는 광선이 물체의 표면에 도달하여 다른 방향으로 튕겨 나가는 현상을 의미한다. 빛이 빛의 파장 (Wavelength)보다 큰 장애물에 부닥칠 경우에 반사된다고 한다.

![[cat-mirror.gif]]

왜 빛이 반사되는가? 빛이 어떻게 반사되는가? 반사의 원리는 진짜 너무 어렵다. 물리학적, 양자역학적, 화학적 작용 등등이 일어난다는 것을 대충 깨달았을때, 아~ 이건 무리다 싶었다. 여기서 내가 정리하고자 하는 것은 반사를 시각적으로 이해하기에 충분한 정보로 한정지어야 될 듯 싶다.

> ![[wave_reflection_animation.gif]]
> 빛 파동의 반사 시뮬레이션 - [Ripple Tank Simulation](http://www.falstad.com/ripple/)

#### 반사 모델링

반사를 이해하려면 일단 간단한 모델링이 가능해야 한다.

물체의 표면을 기준으로 수직선을 그린 것을 [법선](https://keystagewiki.com/index.php/Normal_(Physics)) [(Normal)](https://en.wikipedia.org/wiki/Normal_(geometry))이라고 하면, 법선을 기준으로
- 입사광선이 표면에 도달하는 각도를 __입사각 (Angle of Incidence)__ 이라 한다.
- 반사광선이 표면에서 반사되어 나가는 각도를 __반사각 (Angle of Reflection)__ 이라 한다.

입사광선과 반사광선은 동일한 평면 (Plane)에 위치하는데, 이 평면을 [입사면 (PoI, Plane of Incidence)](https://en.wikipedia.org/wiki/Plane_of_incidence)이라 한다.

![[reflection_3d_model.svg]]

#### 반사의 법칙

빛은 [반사의 법칙 (Law of Reflection)](https://www.physicsclassroom.com/class/refln/Lesson-1/The-Law-of-Reflection) 을 따른다 :
1. 입사각과 반사각은 동일하다.
2. 입사광선과 반사광선은 동일한 평면에 위치한다 ([Coplanar](https://en.wikipedia.org/wiki/Coplanarity)).

참고 : 음파 (Sound Wave)도 반사의 법칙을 따른다.

#### 반사율

반사율은 물체 표면에 광선이 반사되는 수준을 뜻한다.. 하지만, 이게 자세히 보니까 아주 아주 복잡하다. 반사율을 영어로 보면 Albedo, Reflectivity, Reflactance가 나오는데, 이게 각각 정의가 좀 다르면서 엄청 복잡하다!! #todo 반사율은 나중에 좀 더 삽질해본다.

#### 반사의 종류

반사는 정반사와 난반사, 이 두 가지로 분류가 된다.

![[reflection_comparison_01.PNG]]

##### 정반사
[정반사 (Specular Reflection)](https://en.wikipedia.org/wiki/Specular_reflection)는 거울처럼 매끈한 면을 경계로 일어나는 반사를 말한다. 거울반사 또는 경면반사로고도 부른다.

> ![[chicago_the_bean.png]]
> 시카고 (일리노이주, 미국)에 있는 _The Bean_ 이다.

정반사를 광선으로 모델링해보면 - 광원으로부터 서로 근접한 여러개의 광선이 같은 방향으로 나오고 이 광선들이 동일한 평평한 면에 부탁치면, 이 광선들의 입사각이 동일하게 되며, 마찬가지로 반사의 법칙에 따라 반사각이 동일하게 된다.

![[specular_reflection_diagram.png]]

어떤 물체에 거울처럼 다른 무언가가 비춰진다면 그게 정반사라 이해하면 된다. 그 무언가는 주변에 있는 물체라던지, 또는 물건을 비추는 광원이 될 수가 있다.

굳이 거울과 같이 주변 물체를 그대로 비추는게 아니더라도, 반짝거리는 것이 보이면 그것이 정반사라 이해하면 된다. #computer_graphics 분야에서는 이렇게 반짝거리는 부분을 [Specular Highlight](https://en.wikipedia.org/wiki/Specular_highlight)이라 부른다.

![[specular_highlight_example_01.png]]

완전히 정반사를 일으키는 물체는 없다 - 어디서 주워들은 말로는 우리가 평상시 사용하는 거울이 95% 정반사를 일으킨다고 한다.

무조건 매끈한 면이라고 정반사가 일어나는 것은 아니다 - 아무리 매끈하다고, 대리석이 거울처럼 되는 것은 아니다. 애초에 "매끈하다"의 정의가 애매하다.

![[smooth_marble.png]]

##### 난반사
[난반사 (Diffuse Reflection)](https://en.wikipedia.org/wiki/Diffuse_reflection)는 거친 (Rough) 면을 경계로 여러 방향으로 일어나는 반사를 말한다. 확산반사라고도 한다 (근데 어떤 자료에서는 확산반사하고 난반사가 다른 것처럼 여기기도 한다).

참고 : 굳이 확산반사라 안하고 난반사라 한 이유는, "난장판"의 난(亂)이 더욱 직흥적이다 느껴서 그렇다.

"반사"라고 주변에 무언가가 비춰보여야 될 것 같은데, 그건 아니다. 정반사가 거울 같은 현상이라면, 난반사는 그 반대로 물체가 보이는 현상이다.

> ![[wooden_ball.png | 300]]
> Blender로 그려진 나무 공이다. 반짝임(정반사)가 매우 적어 난반사 예시로 보기 좋다.

난반사 광선으로 모델링해보면 - 광원으로부터 서로 근접한 여러개의 광선이 같은 방향으로 나오고 이 광선들이 동일한 거친 면에 부탁치면, 이 광선들의 입사각이 서로 다르게 되며, 마찬가지로 반사의 법칙에 따라 반사각이 다르게 된다.

![[diffuse_reflection_diagram.png]]

참고 : 인터넷에 찾다보면 난반사는 반사의 법칙을 따르지 않는다는 설명이 있는데, 내가 보기엔 이건 틀린 정보인 것 같다.

난반사가 "거친 면"에 발생한다고 하되, 아주 아주 미세하게 거친 것을 뜻한다. 빛의 크기나 광선간의 거리를 재는 것은 거의 불가능하지만, 빛의 파장 (750 nm ~ 380 nm) 보다 작은 정도의 거침이 아닐까 싶다.

![[microscopic_view_on_diffuse_reflection.png]]

참고 : [인간의 촉각은 13 nm 까지 인식이 가능하다.](https://www.nationalgeographic.com/culture/article/130912-tactile-touch-perception-nanometers-psychology-science)

##### 산란
[산란 (Scattering)](https://en.wikipedia.org/wiki/Scattering)은 전자기파가 진행하다가 만난 물체의 표면에서 물체의 특성에 따라 사방으로 전자기파가 퍼지는 특성을 뜻한다.

산란은 사실 반사보다는 더 큰 개념이다. 반사 섹션에 굳이 명시하는 이유는,
1. 인터넷에서 산란하고 난반사를 헷갈리게 설명한다. 심지어 오역으로 인해 난반사를 산란광이라고 부르는 자료도 몇 있다. 사실 산란-반사의 관계는 직사각형-정사각형 관계랑 비슷한데, 난반사는 산란에 속하지만 산란이 난반사인 것은 아니다.
2. 산란이 난반사와 유사하게 보일수도 있다. 난반사는 물체의 표면에 의해 빛이 여러 방면으로 반사되는 현상인 반면, 산란은 빛이 표면을 통과하여 물질/물체 내에서 반사되어 표면 바깥으로 다시 보이는 현상이다.
3. 위에 정반사에 대하여 알아볼때, 대리석이 아무리 매끈해도 거울처럼 되는거는 아니다라고 했었다. 산란의 정의에 "물체의 특성에 따라"라는 문구가 있는데, 아마 이게 연관된게 아닌가 싶다. "금속은 난반사를 하지 않는다"라는 주제로 좀 찾아보면 아주 재밌는 자료들이 나온다.. [참고 1](https://google.github.io/filament/Filament.html#materialsystem/dielectricsandconductors), [참고 2](https://physics.stackexchange.com/a/213535/333609)

![[light_interface_interaction_models_diagram.png]]

#computer_graphics 분야에서는 주로 [투명도 (Transparency/Translucency)](https://en.wikipedia.org/wiki/Transparency_and_translucency)와 관련해서 산란을 다루는 듯 싶다.

![[sleeping_pikachu.png | 300]]

영자역학에 속한 [산란 이론 (Scattering Theory)](https://en.wikipedia.org/wiki/Scattering_theory)이란 것이 있다.. 이거 완전 클래스가 미쳤다.

#todo 빛의 특성으로 큰 카타고리를 만들어서 정리해야 할 듯 싶다.

#### 반사에 대한 추가 정리
일반적으로 정반사와 난반사는 같이 발생한다.

반사는 빛이 에너지를 모두 소모하기 전까지 계속 반사된다.

![[reflection_on_surface_comparison_01.png]]

![[reflection_comparison_02.png]]

![[diagram_roughness.png]]

![[5_lights.PNG]]

참고 자료 : [Reflection에 대한 잘못된 상식들](https://lifeisforu.tistory.com/383)

### 투과
투과 (Transmission)는 빛이 물체를 통과하는 것을 뜻한다.

![[light_transmission_example_01.webp]]

투과의 원리는 끔찍하게도 복잡하다. 심지어 너무 복잡해서 wiki 페이지도 없다.

그나마 "대충" 이해한 바로, 물체의 전자 (Electron)의 진동하는 수준과 빛의 파장 (Wavelength)과 관련되어 있다는 것이며, 충분히 진동하면 투과 (Transmission)되는 것이고, 그렇지 않으면 반사 (Reflection)되는 것이다.

이게 [파동-입자 이중성 (Wave-Particle Duality)](https://en.wikipedia.org/wiki/Wave%E2%80%93particle_duality)과 관련된 사항이니, 더 깊숙하게 이해하려는 것은 깨끗하게 포기한다!

그러면 투과에 대해서 무엇을 이해해야 할까?

일단 용어에 대해서 좀 정리해본다.

__투과율__ 은 [Transmittance](https://en.wikipedia.org/wiki/Transmittance), [Transmissivity](https://www.collinsdictionary.com/de/worterbuch/englisch/transmissivity), 또는 [투과 계수 (Transmission Coefficient)](https://en.wikipedia.org/wiki/Transmission_coefficient#Optics)로 불린다.. 각 용어에 따라 정의가 다르긴 한데, 일단 여기선 넘어간다 ([참고 자료 1](https://www.swiftglass.com/blog/key-differences-transmission-transmittance-apply-application), [참고 자료 2](https://www.iesve.com/support/ve/knowledgebase_faq/faq/1282))

Maya의 [투과율 조절 가이드](https://docs.arnoldrenderer.com/display/A5AFMUG/Transmission)를 참고해보면 좋을 것 같다.

![[maya_transmission_example.png]]

투과와 관련해서 물체의 특성을 가르킨다면, 투과율에 따라 사용되는 용어는 다음과 같다.
- [투명 (Transparent)](https://en.wikipedia.org/wiki/Transparency_and_translucency) : 빛이 물체를 완전히 통과함 (투과율 1)
- [반투명 (Translucent)](https://en.wikipedia.org/wiki/Transparency_and_translucency) : 빛이 물체를 일부 통과함 (0 < 투과율 < 1)
- [불투명 (Opaque)](https://en.wikipedia.org/wiki/Opacity_(optics)) : 빛이 물체를 통과할 수 없음 (투과율 0)

#### 굴절
Refraction

#### Diffraction

![[light_diffraction_example_01.PNG]]

### 흡수
[흡수/흡광 (Absorption)](https://en.wikipedia.org/wiki/Absorption_(electromagnetic_radiation))은 물체의 표면을 통과한 상태에서 결국 물체 자체를 벗어나지 못하는 현상을 의미한다.

### 반사, 투과, 흡수의 관계
반사, 투과, 흡수는 동시에 일어나며 [보존 법칙 (Law of Conservation)](https://en.wikipedia.org/wiki/Conservation_law)에 따른다.

빛의 에너지를 1이라고 보면, `R(반사율) + A(흡수율) + T(투과율) = 1` 관계가 성립된다.

[[#광원]] 섹션에서 알아본 흑체 (Blackbody)는 반사율 0%, 투과율 0%, 흡수율 100% 인 이상적인 완전 물체로 `A = 1`이라 정의할 수 있다.

불투명한 물체는 투과율 0%에 가까우며 `R + A = 1`이라 정의할 수 있다.

### 물체와 빛의 상호작용 (정리)
__빛에 비추어진 물체의 색은 물체로 인해 흡수되지 않고 투과 또는 반사된 광선의 색이라 볼 수 있다.__

#### 불투명 물체와 빛의 상호작용
투과율이 0%이기 때문에, 불투명 물체의 색은 오로지 반사된 광선의 색이다. 이 섹션에서는 흡수와 반수 위주로 정리해본다.

빛에 여러 파장이 있다는 것을 고려하면, 하얀색 빛은 [[#단색광]]의 여러 광선으로 표현할 수 있다. RGB (빨강,초록,파랑)로 이루어진 하얀 빛이 하얀 물체, 빨간 물체, 초록 물체, 파란 물체, 그리고 검은 물체에 비추어진다 하면, 결과는 밑에 그림과 같다.

![[reflection_and_absorption_of_light_on_colored_objects.PNG]]

RGB 기준으로 불투명 물체와 빛의 상호작용에 대한 식을 정의한다면, 밑에와 같다.

`W - B = (R + G + B) - B = R + G = Y`

어떤 물체가 파란색의 광선만 반사하고 그 나머지 색의 광선들을 흡수한다면, 그 물체는 파란색으로 인식이 된다.

#todo 여기서 사실 엄청 복잡해지는 것은, 하얀색 빛에서 파란색을 흡수하는 물체는 빨간색과 초록색을 반사한다는 것인데, 이 두 색이 합치면 노란색이 된다는 것이다. 그러면, 물체가 노란색을 제외한 모든 색을 흡수해서 노란색으로 보이는 것과, 빨간색과 초록색만 반사해서 노란색으로 보이는 것과 어떻게 달라 보일까?

그러면 빨간 빛이 파란 물체에 비추어지면 어떻게 될까?

![[colored_lights_on_colored_objects.PNG]]

여기서 더 나아가기 전에, 앞으로 빛의 색과 물체의 색의 상호작용에 관련하여 정리하는 것은 이론적이라는 것을 주의해야 한다. [[#단색광]]에 명시했듯이, 단색광은 이론적인 것이며 실제로 재현하기는 어렵다 - __앞으로 명시될 "어떤 색 빛" (예: 빨간 빛)은 이론적이며, 이 빛에 대한 상호작용 또한 이론적이다.__ 현실 세계에서 "어떤 색 빛"은 생각 외로 여러 색과 섞여 있는 빛일 수도 있으며, 이론적으로 계산된 색과 다른 결과를 보여줄 수 있다. __더불어, 물체의 색 또한 이론적인 요소로, 하나의 색만 완벽히 반사하는 물체는 없다고 볼 수 있다__ ([불가능은 아니다](https://physics.aps.org/articles/v8/20)).

물체로부터 반사되는 광선이 없으면, 그 물체는 검은색으로 보인다.
- 빛이 없으면 물체는 검은색으로 보인다.
- 빛이 있어도 물체가 검은색이면 (모든 빛이 흡수되면) 그 물체는 검은색으로 보인다.
- 빛이 있고 물체가 검은색이 아니어도, 반사되는 빛이 없으면 물체는 검은색으로 보인다.

빨간 빛이 파란 물체에 비추어지면, 빨간 빛은 모두 흡수되고 반사될 빛이 없다. 그러므로, 파란 물체는 아무 색이 없는 검은색으로 인식된다. #todo 파란 빛이 빨간 물체에 비추어질때도 마찬가지 일까?

빛의 색도 아니고 물체의 색도 아닌 색이 반사될 경우가 있다. 실제로는 빛의 파동 일부만 반사되는 것인데, 우리가 인식하기에는 완전히 색이 달라보이는 것이다.

위 예시가 헷갈릴 수도 있다. 아는 사람은 알겠지만, [[#가산혼합]]에 원리로, 파란색과 빨간색이 합치면 보라색이 나온다. 빨간 빛을 파란 물체에 비추어봤을때 보라색으로 보일거라는 생각을 할수가 있다. 하지만 그건 파란 빛과 빨간 빛이 합쳐야만 가능한 것이고, 어떠한 이유로 파란 빛이 물체로부터 발생되고 빨간 빛이 일부 반사되지 않는 이상 보라색이 나오는 것은 불가능하다.

반사되는 광선이 의외에 색인 경우가 있다. 파란 빛이 노란 물체에 비추어지면 초록색으로 보이는 경우가 그렇다. 이러한 경우가 발생되는 이유는,
1. 빛이 단색광이 아니다 - 파란색 주파수와 초록색 주파수는 아주 근접하며, 이 "파란 빛"은 초록색을 약간 품은 파란색 대역의 주파수들을 갖추고 있는 다색광이다.
2. 물체가 여러 주파수를 반사한다 - 노랑색 주파수와 초록색 주파수는 아주 근접하며, 이 "노란 물체"는 초록색을 약간 품은 노란색 대역의 주파수들을 반사한다.

결론적으로, 우리 눈에는 파란 빛이 노란 물체에 비추어 초록색을 띄운다고 인식하지만, 사실 초록 빛이 초록 물체에 비추어 초록색을 띄우고 있는 것이다.

노란 빛이 파란 물체에 비추어도 초록색이 보인다. #todo 그림에서는 이 경우, 훨씬 어두운 초록색이 보이는데, 이건 빛의 파장과 광도에 연관된게 아닐까 싶다.

#todo 초록 빛이 빨간 물체에 비추어진다면 무슨 색으로 보일까? 단색광이면 그냥 검은색으로 보이겠지만, 노란색이 섞인 초록 대역 주파수들이 포함된 다색광이면 위에 이론에 따라서 노란색이 보일까? 

빨간 빛이 노란 물체에 비추어지면 빨간색으로 보인다. 왜? 반대로, 노란 빛이 빨간 물체에 비추어지면, 주황으로 보인다.

빛의 색에 따라 물체의 색이 달라보이는 현상, 이를 [[#메타메리즘]]이라 한다.

### 빛의 특성 참고자료
참고 자료 1 : [삼성디스플레이 뉴스룸 : 재귀반사](https://news.samsungdisplay.com/29873)

참고 자료 2 : [네이버 블로그 글 : 색상/색체 이론](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=loveandpic&logNo=220356463987)

참고 자료 3 : [물체의 색](https://en.wikipedia.org/wiki/Color#Color_of_objects)

참고 자료 4 : [정보통신기술용어해설 : 입사파, 반사파, 투과파](http://www.ktword.co.kr/test/view/view.php?m_temp1=3863)

참고 자료 5 : [Sciencing - Search "light"](https://sciencing.com/search?google_kw=light)

참고 자료 6 : [유리를 통과하는 빛은 느려지는가?](https://www.physlink.com/education/askexperts/ae217.cfm) - #todo 나중에 글이 없어질 수 있으니, 따로 글로 정리할 것.

참고 자료 7 : [빛이 느려진다면 어떻게 보일까?](https://www.livescience.com/what-if-speed-of-light-slowed-down) - #todo 이걸 [게임](http://gamelab.mit.edu/games/a-slower-speed-of-light/)으로 구현한게 있으니, 나중에 해보자.

<iframe width="560" height="315" src="https://www.youtube.com/embed/cv0bBfiCWAk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

https://ctsciencecenter.org/blog/science-at-play-change-the-color-of-the-world-around-you/

## 메타메리즘
[메타메리즘 (Metamerism)](https://en.wikipedia.org/wiki/Metamerism_(color)) : 광원, 관측자, 관측조건 차이에 따라 두 물체의 색이 같아 보이거나 달라 보이는 현상을 뜻한다. 조건 등색으로 불리기도 한다.

![[metamerism.PNG]]

### MCM
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

참고 자료 1 : [색 매칭 웹 게임](https://color.method.ac/) - MCM하고 크게 관련 있는 것은 아닌데, 프로세스는 비슷하고 색 매칭하는게 얼마나 힘든지 알 수 있다 ㅋ

### 혼합 색상
https://en.wikipedia.org/wiki/Color_mixing

#todo 혼합 색상 내용 넣고 원색 내용 여기로 옮기기

#### 가산혼합
[가산혼합 (Additive Color)](https://en.wikipedia.org/wiki/Additive_color)은 3개 색을 혼합하여 모든 색을 구현하는 방식이다.

가산 (Additive)의 의미는 빛이 없는 공간 (검은색)에 빛을 "더하여" 하얀색으로 만든다는 뜻이다. 다른 말로는, 검은색에 각 색을 "더하여" 여러 색을 구현한다는 뜻이다. 최종적으로 모든 색을 최대 비율로 더하면 하얀색이 나온다.

가산혼합에 사용되는 색을 [원색 (Primary Color)](https://en.wikipedia.org/wiki/Primary_color)이라고 부르며, 서로 독립적인 색을 뜻한다 - 서로 독립적인 색은, 둘을 혼합해도 남은 셋째의 색을 만들 수 없다.

#### 감산혼합
[감산혼합 (Subtractive Color)](https://en.wikipedia.org/wiki/Subtractive_color)은 가산혼합과 마찬가지로 3개 색을 혼합하여 모든 색을 구현하는 방식이다.

감산 (Subtractive)의 의미는 빛이 반사하는 공간 (하얀색)에 빛을 "빼서" 검은색으로 만든다는 뜻이다. 다른 말로는, 하얀색에 각 색을 "빼서" 여러 색을 구현한다는 뜻이다. 최종적으로 모든 색을 최대 비율로 빼면 검은색이 나온다.

#### 혼합 색상의 오해
우리는 흔히 파란색과 노란색이 초록색을 만든다고 생각한다. 맞긴 맞을거다, 적어도 감산혼합에 있어서는..

#todo 밑에 자료 위주로 다시 정리

https://colourware.org/2018/05/18/why-yellow-and-blue-dont-make-green

![[blue_yellow_spin.webp]]

## 인간 생체 관련 노트

## 국제조명위원회
[국제조명위원회 (CIE, Commission Internationale de l'Eclairage)](https://en.wikipedia.org/wiki/International_Commission_on_Illumination), 영어로는 _International Commission on Illumination_ 이라 불리는 단체는 "조명 과학/기술과 관련한 모든 문제에 대해 국제적 협력 및 정보의 교환을 위한 국제 기국"이다.

[CIE 홈페이지](https://cie.co.at/)

![[cie.png]]

__CIE는 측광, 측색 등에 대한 표준과 측정 수단을 개발하고 결정하는 기관이다.__ CIE 측에서 발표한 표준의 대표적인 예시로 [[#CIE 1931 색 공간]]이 있다. 그 외에 [[#표준 광원]]도 CIE에서 관리한다.

참고 자료 1 : [정보통신기술용어해설 - 국제조명위원회](http://www.ktword.co.kr/test/view/view.php?m_temp1=2643)

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



#### RGB 색 모델
가산혼합에 일반적으로 사용되는 원색은 RGB: Red, Green, Blue이다. 이 색들을 사용하는 가산혼합을 [RGB 색 모델](https://en.wikipedia.org/wiki/RGB_color_model)이라 부른다.

모든 모니터/프로젝터는 RGB 색 모델을 사용한다.

이론적으로 RGB가 아닌 다른 가산혼합 원색도 있다. 하지만 사람은 RGB 색에 가장 민감하게 반응하기 때문에 RGB가 사용된다.

![[rgb_summation.webp]]


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
