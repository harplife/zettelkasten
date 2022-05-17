---
aliases: [Color Theory, 색 이론]
tags: [computer_vision, computer_graphics, color_theory, study]
status: ongoing
created: 2022-04-01
edited: 2022-05-12
---

# 색 이론
[색(Color)](https://en.wikipedia.org/wiki/Color)은 무엇인가? 색은 어떻게 발생하는가? 색을 어떻게 구분하는가? 색을 이해하기 위해서 어디서 부터 시작해야 할까? 색을 이해하기 위해서, 어떤 자료를 찾아봐야 할까?

아쉽게도 색에 대한 모든 정보를 한번에 정리하는 연구 분야가 없다 - 정확히는, 색과 관련된 연구분야는 많지만, 색에 관련된 정보를 하나의 분야로 정의하기는 어렵다.

색은 빛이고, 빛은 전자기파(Electromagnetic Wave)이다. 색을 이해하기 위해서는 빛을 이해해야 하고, 빛을 이해하기 위해서는 전자기파를 이해해야 한다. 문제는 전자기파는 물리학, 화학, 천문학에서 다루는 주제이고, 심지어 아주 심오한 특수 상대성 이론과 양자역학과도 연결되어 있다.

더 나아가, 색은 사람의 지각(Perception)과도 관련되어 있기 때문에, 생체학과 심리학과 연결되어 있다.

"색을 연구하는 분야"라고 검색하면 나오는 결과는 다양하다.
1. 색체 과학(Color Science) : 말 그대로 색을 연구하는 학문인데, 흔한 학문는 아닌것 같다. 약간 음향공학과 같은 애매한 수준의 학문이 아닐까 싶다.
2. Chromatics : 물리학에서 빛/색을 연구하는 하위분야인 듯 싶다. 근데 Chromatics은 음악 분야에 너무 많이 사용되는 용어라, 색과 관련된 Chromatic은 구글 검색에서도 잘 안 뜬다.
3. [색 측정법(Colorimetry)](https://en.wikipedia.org/wiki/Colorimetry) : 과학과 기술을 동원해 정량적으로 색을 측정하는 학문이다.
4. [Color Vision](https://en.wikipedia.org/wiki/Color_vision) : 연구분야라고 하긴 어려운데, 의외로 위키에서 연결된 자료들이 많다.
5. [분광학(Spectroscopy)](https://en.wikipedia.org/wiki/Spectroscopy) : 빛과 물질 간의 상호작용을 연구하는 학문이다.
6. [광학(Optics)](https://en.wikipedia.org/wiki/Optics) : 빛의 성질 및 관련 현상을 연구하는 학문이다.

내가 정리하고자 하는 것이 어떤 학문과 일치하는지 모르겠다. 이 노트의 목표는 #computer_graphics 에 입문하기 위해 색에 대한 기초지식을 정리하되, 단순히 "빛은 흡수/반사/투과되며 사용되는 수식은 이거다" 또는 "모니터는 RGB 모델을 사용한다"보다는 더 깊게 나아가고 싶다.

기본적으로 색을 연구하기 위해서 빛-물체-사람과의 관계를 연구해야 한다. 정확히는, 각 요소의 상호작용에 있어 어떤 특성이 중요한지 알아봐야 한다.

![[relationship_of_color.png]]

![[color_relationship.PNG]]

일단 색에 대한 정리는 크게 6가지로 구분한다.
1. 색 이론의 역사
2. 색의 정의
3. 빛의 특성
4. 물체의 특성
5. 생체의 특성
6. 색 공간

참고 : 색에 대한 정리를 하면서 듣기 좋은 곡, [Colors by Black Pumas](https://youtu.be/B7PnQBn5k_E)

__주의__ : 앞으로 사용되는 용어로 _물체_ 는 어떤 모형을 갖춘 것을 뜻하는 것보다는 그냥 어떤 것(Thing)을 가리키는 용도로 사용된다. _매질/매개체(Medium)_ 등 호환되는 단어로 사용한다.

#todo 언젠가는 이 노트를 기준으로 사이트를 만들어 애니메이션(WebGL)으로 설명하고 싶다.

## 색 이론의 역사
색 이론은 아리스토텔레스(Aristotle)가 "색은 신이 천국에서부터 내려준 성스러운 광선이다"라고 주장한 것으로부터 시작되고 그 뒤로 색 조합 등 여러 이론들이 나왔지만, 색 이론의 진정한 형식화는 1704년도에 출판되었던 [아이작 뉴턴(Isaac Newton, 1642-1727)](https://en.wikipedia.org/wiki/Isaac_Newton)의 책, [_Opticks_](https://en.wikipedia.org/wiki/Opticks) 로부터 시작되었다.

#todo 번역 및 정리 - Newton is traditionally regarded as the founder of spectroscopy, but he was not the first scientist who studied and reported on the solar spectrum. The works of Athanasius Kircher (1646), Jan Marek Marci (1648), Robert Boyle (1664), and Francesco Maria Grimaldi (1665), predate Newton's optics experiments (1666–1672). - https://en.wikipedia.org/wiki/History_of_spectroscopy

[Early History of Spectroscopy: Astronomy 유투브 플레이리스트](https://youtube.com/playlist?list=PLepnjl2hm9tEauxnqXG8JjBR7Y3w-8nXg) 참고

https://www.pasco.com/resources/blog/243 참고

### 프리즘 실험
프리즘 실험은 빛을 프리즘에 비추고 프리즘에서 분리되어 나온 색들을 연구하는 실험을 뜻한다. 정확히는, 어두운 방에 작은 구멍(Slit)을 통해 들어온 광선을 가운데 프리즘에 비추고 그 반대편에 세워진 판자에 비추어진 색들을 연구하는 실험이다.

![[dispersive_prism_experiment_painting.png]]

![[dispersive_prism_pretty_one.png]]

굴절은 빛이 휘는 현상을 뜻하고, 분산은 색이 분리되는 현상을 뜻한다. 프리즘 실험과 같은 실험을 [[#굴절]] 실험 또는 __분산(Dispersion)__ 실험이라고도 한다.

프리즘 실험에 사용되는 프리즘을 [분산 프리즘(Dispersive Prism)](https://en.wikipedia.org/wiki/Dispersive_prism)이라 부른다. 분산 프리즘은 [[#굴절의 법칙]]을 따른다 - 색의 주파수에 따라 굴절각이 다르기 때문에 하얀색에서 여러 색들이 분산되어 보이는 것이다.

![[dispersive_prism_refraction_diagram.png]]

유리의 빛 굴절 특성은 과학자에게 중요한 도구이며 연구대상이 되었다 - 빛을 굴절시키는 유리, 즉, 렌즈를 사용하여 물체를 더욱 자세히 볼 수 있는 현미경(Microscope)에서부터 멀리 있는 물체를 보이게 해주는 망원경(Telescope)까지 발명될 수 있었으며, 이 도구들을 사용함으로 과학은 많은 진보를 이루었다.

![[dutch_telescope_1624.png]]

유리나 물로 인해 빛이 굴절/분산되는 것은 누구나 볼 수 있는 현상이다. 정확히 누가 프리즘 실험을 처음 시작했는지는 모르지만, [[play_of_colors_history_of_prisms.pdf | 고대 로마 시절에서부터 분산 프리즘은 여러 색이 나오는 멋진 장난감]]에 불과했다. 그나마 17세기에 이르러 뉴턴의 발견으로 인해, 분산 프리즘을 이용해 유리의 굴절 특성을 좀 더 다양한 방면으로 연구할 수 있음을 알게되었다.

시간이 지나며, 프리즘 실험을 기반으로한 여러 연구 결과로서 분산된 색들이 빛을 내는 물체([[#광원]])의 성분을 구분하는데 도움이 된다는 것이 발견되었다. 그리하여, 프리즘 실험을 통한 색의 연구는 화학, 천문학, 그리고 물리학 발전에 큰 주축이 되었다.

과거에 프리즘 실험(또는 비슷한 실험)을 통해 가시광선을 연구하는 학문을 [분광학 (Spectroscopy)](https://en.wikipedia.org/wiki/Spectroscopy)이라 불렀다 ([누가 분광학을 발명했는가?](https://www.pasco.com/resources/blog/243)). 이후에 이 개념은 확장되어 물질과 전자기파의 상호작용으로 나온 전자기 스펙트럼\*을 파장 또는 주파수의 함수로서 측정하고 해석하는 학문으로 발전되었다.

\* [전자기 스펙트럼](https://en.wikipedia.org/wiki/Electromagnetic_spectrum) : 파장이나 주파수의 함수로 주어지는 반응 값을 도표로 나타낸 차트. __분광 분포도__ 라고도 한다.

![[dispersive_prism_spectrum_01.jpg]]

![[visible_spectrum_02.svg]]

참고 : 전자기 스펙트럼을 측정하는 도구를 [분광기(Spectrometer)](https://en.wikipedia.org/wiki/Spectrometer)라고 한다. 분광계라고도 하는데, 차이가 있는지 모르겠다.

[Pink Floyd](https://en.wikipedia.org/wiki/Pink_Floyd)의 [Dark Side of the Moon](https://en.wikipedia.org/wiki/The_Dark_Side_of_the_Moon) 앨범 커버에 그려진 것이 분산 프리즘이다. 빛은 프리즘 안에서부터 여러 색으로 분산되는데, 앨범 커버는 프리즘 반대 표면에서부터 분산되는 것으로 그려서 틀린 그림이라고 지적 받는다.

그래도 [음악 앨범](https://music.youtube.com/playlist?list=OLAK5uy_mXoi-FuQb9Gw7Mguhdx5F4jltT0L1qOCw&feature=share)이 너무 좋아서 용서해준다.

![[dark_side_of_the_moon_album_cover.png]]

### 뉴턴의 발견
17세기에 [광학(Optics)](https://en.wikipedia.org/wiki/Optics)은 현미경(Microscope)을 만들 정도로 잘 발달된 학문이였다. 프리즘(Prism)으로 하얀빛을 굴절/분산시켜 여러 색을 만들수있다는 것은 알고있었지만, 이 현상을 잘 이해한 것은 아니었다. 그 당시에는 하얀색이 가장 순수한 색이며, 물질로 인해 더렵혀짐(Contaminated)으로 다른 색으로 변한다고 믿었다 (그것도 4대 고대 원소로 인해).

![[avatar_four_elements.webp]]

[눈깔 레이저빔 이론(Emissive Vision Theory)](https://en.wikipedia.org/wiki/Emission_theory_(vision)), 즉, 눈에서 광선이 나온다고 믿는 사람들도 있었다!  [눈에서 빔](https://namu.wiki/w/%EB%88%88%EC%97%90%EC%84%9C%20%EB%B9%94) 나무위키 글 읽는 재미도 있다.

![[ultraman_eye_beam.webp]]

이러한 생각은 뉴턴의 프리즘 실험으로 인해 완전히 뒤집어졌다.

__뉴턴은 프리즘 실험을 통해 하얀 색이 다른 색으로 변하는게 아니라, 하얀 색이 여러 색으로 구성되어 있음을 발견했다.__ 특정 색들을 조합하여 다른 색을 낼수 있음을 증명했고, 분산된 모든 색을 다시 합치면 하얀색이 나온다는 것을 증명했다.

뉴턴은 하얀색은 7가지 색, [빨주노초파남보(Roy G. Biv)](https://en.wikipedia.org/wiki/ROYGBIV)으로 구성되었다 하고, 이 색들을 "원색 (Primary Color)"이라 불렀다.

![[isaac_newton_opticks_color_circle_cropped.png]]

#todo 더 자세한 내용은 [[isaac_newton_color_theory|아이작 뉴턴의 색 이론]]에 정리한다.

### 스펙트럼 선
뉴턴의 발견 이후 색 이론은 한동안 큰 진전이 없었다. 거의 100년이 지나서야 (1802년) [윌리엄 하이드 울러스턴(William Hyde Wollaston, 1766-1828)](https://en.wikipedia.org/wiki/William_Hyde_Wollaston)이 뉴턴 프리즘 실험 구조에 렌즈를 추가하여 스펙트럼을 좀 더 자세히 볼 수 있게 개선했다. 울러스턴은 태양광 스펙트럼에 7개의 흑선이 있다는 것을 발견했고, 이를 색을 구분하는 경계선이라고 발표했다.

[요제프 폰 프라운호퍼(Joseph von Fraunhofer, 1787-1826)](https://en.wikipedia.org/wiki/Joseph_von_Fraunhofer)는 유리 공예가(Glass Maker)로서 프리즘 실험을 통해 분산된 각 색으로서 여러 종류의 유리의 굴절 효과를 연구하고자 했고, 1814년도에 프리즘 실험을 완전히 개선해서 첫 [분광기(Scpectrometer)](https://en.wikipedia.org/wiki/Optical_spectrometer)를 발명했다 - 덕분에, 스펙트럼을 훨씬 자세히 관찰할 수 있을 뿐더러, 색의 파장을 측정할 수 있게 되었다.

#todo 분광기에 대해 다른 노트에 정리 - https://astro-canada.ca/les_spectrometres-spectrometers-eng

프라운호퍼는 실험을 통해 울러스턴이 발견했던 흑선들을 확인해볼 수 있었고, 7개 뿐만이 아니라 수백개(570?)의 흑선이 있다는 것을 발견했다. 프라운호퍼는 이 흑선들을 일일이 그리는 노가다 정신을 보였다 (추후에 이 과정은 아주 체계적인 스펙트럼 연구 방식으로 인정되었다). 이 흑선들은 [프라운호퍼 선(Fraunhofer Line)](https://en.wikipedia.org/wiki/Fraunhofer_lines)이라 불린다.

![[fraunhofer_lines.svg]]

더불어, 프라운호퍼는 태양과 다른 광원(예: 행성, 가열된 금속, 촛불)의 스펙트럼을 비교하여 각 광원의 흑선들의 위치가 다르다는 것을 발견했고, 이 흑선들이 울러스턴이 말했던 "색의 경계선"이 아니라 빛을 발하는 광원의 특성이라는 이론을 제시하였다. 하지만 이 흑선이 의미하는 바가 정확히 무엇인지는 발견하지 못 했다.

#todo 더 자세한 내용은 [[joseph_fraunhofer|프라운호퍼의 색 이론]]에 정리한다.

참고 : 현재로서 태양광 스펙트럼의 흑선은 약 25,000개 까지 발견되었다.

[[#광원의 성분]]에서 더 자세히 설명하겠지만, 흑선을 연구하는 과정에 물질이 특정 색을 흡수한다는 사실이 발견되었다. 흑선은 그래서 흡수선(Absorption Line)으로 불리게 되었다. 흡수선의 반대 개념으로 방출선(Emission Line)이 있으며, 이는 가열된 물질이 방출하는 특정 색을 표기하는데 사용된다. 흡수선과 방출선을 통틀어서 [스펙트럼 선(Spectral Line)](https://en.wikipedia.org/wiki/Spectral_line)이라 부른다. 스펙트럼에 흡수선을 사용하여 표기한 것을 [흡수 스펙트럼(Absorption Spectrum)](https://en.wikipedia.org/wiki/Absorption_spectroscopy#Absorption_spectrum)이라 부르며, 방출선을 사용한 스펙트럼은 [방출 스펙트럼(Emission Spectrum)](https://en.wikipedia.org/wiki/Emission_spectrum)이라 부른다.

### 회절 격자
[James Gregory(1638–1675)](https://en.wikipedia.org/wiki/James_Gregory_(mathematician)) observed the diffraction patterns caused by a bird feather, which was effectively the first diffraction grating (in a natural form) to be discovered, about a year after Isaac Newton's prism experiments.

The first man-made diffraction grating was made around 1785 by Philadelphia inventor David Rittenhouse, who strung hairs between two finely threaded screws.




[이중 슬릿 실험(Double-Slit Experiment)](https://en.wikipedia.org/wiki/Double-slit_experiment)

By 1785, James Gregory discovered the principles of diffraction grating and American astronomer David Rittenhouse made the first engineered diffraction grating. In 1821, Joseph von Fraunhofer solidified this significant experimental leap of replacing a prism as the source of wavelength dispersion improving the spectral resolution and allowing for the dispersed wavelengths to be quantified. - https://en.wikipedia.org/wiki/Emission_spectrum#History



### 광원의 성분
#todo 번역 및 정리 - In 1756, Thomas Melvill observed the emission of distinct patterns of colour when salts were added to alcohol flames.  - https://en.wikipedia.org/wiki/Emission_spectrum#History

In 1835, Charles Wheatstone reported that different metals could be distinguished by bright lines in the emission spectra of their sparks, thereby introducing an alternative to flame spectroscopy. In 1849, J. B. L. Foucault experimentally demonstrated that absorption and emission lines at the same wavelength are both due to the same material, with the difference between the two originating from the temperature of the light source. In 1853, the Swedish physicist Anders Jonas Ångström presented observations and theories about gas spectra. Ångström postulated that an incandescent gas emits luminous rays of the same wavelength as those it can absorb. At the same time George Stokes and William Thomson (Kelvin) were discussing similar postulates. Ångström also measured the emission spectrum from hydrogen later labeled the Balmer lines. In 1854 and 1855, David Alter published observations on the spectra of metals and gases, including an independent observation of the Balmer lines of hydrogen.

By 1859, Gustav Kirchhoff and Robert Bunsen noticed that several Fraunhofer lines (lines in the solar spectrum) coincide with characteristic emission lines identified in the spectra of heated elements. It was correctly deduced that dark lines in the solar spectrum are caused by absorption by chemical elements in the solar atmosphere.

https://en.wikipedia.org/wiki/Emission_spectrum#History

더 자세한 디테일은 https://en.wikipedia.org/wiki/History_of_spectroscopy 참고

![[hydrogen_absorption_spectrum_and_intensity.png]]

[How do scientists determine the chemical compositions of the planets and stars?](https://astronomy.com/magazine/ask-astro/2019/06/how-do-scientists-determine-the-chemical-compositions-of-the-planets-and-stars)

![[spectroscopy_diagram.svg]]

![[absorption_by_sodium_rich_atmosphere.png]]

![[color_by_element_firework_edition.png]]

#todo 이건 사실 아주 역사가 길기 떄문에, 따른 노트로 정리한다.

## 색의 정의
#todo 색은 빛-물체 상호작용으로부터 파생된 시지각적 특성(Visual Perceptual Property)이다...라고 정의하면 될 듯 싶다. 아직 그리 마음에 드는 정의는 없는 듯 싶다.

### 가시광선
우리가 흔히 생각하는 "빛"은 일상 생활에 "보이는 빛"이다. 빛은 보이는 빛과 보이지 않는 빛이 있고, 빛과 [전자기파(Electromagnetic Radiation)](https://en.wikipedia.org/wiki/Electromagnetic_radiation)는 동의어이다. "보이는 빛"은 사람의 눈에 보이는 전자기파로서 __가시광선__ 이라 불리운다.

참고 : "보이지 않는 빛"은 적외선, 자외선 등 가시광선을 제외한 모든 전자기파이다.

색은 빛으로부터 파생된다. 보다 정확히 표현하자면, 색은 빛과 물체의 상호작용으로서 방출된 가시광선이 사람의 눈으로서 인식되는 특성이다.

위에 명시했듯이, 빛은 "보이는 빛"과 "보이지 않는 빛"이 있으며, 우리가 일반적으로 접하는 색은 "보이는 빛"과 물체의 상호작용으로 발생된 가시광선이다 (가시광선이 물체와 상호작용하여 변형된 가시광선이 나온다).

보이지 않는 빛과 물체의 상호작용으로 발생되는 가시광선도 있다. 예로서, [형광(Fluorescence)](https://en.wikipedia.org/wiki/Fluorescence)은 자외선을 받으면 가시광선을 방출하는 물질의 특성이다.

> ![[polka_dot_tree_frog_flourescence.png]]
> Polka-dot tree frog은 피부에 형광물질이 있다.

참고 : 형광등은 자외선(Ultraviolet Light)을 방출하고, 등(Bulb) 안에 있는 물질(Phosphor)들이 자외선을 가시광선으로 변환한다.

[가시광 스펙트럼(Visible Spectrum)](https://en.wikipedia.org/wiki/Visible_spectrum)은 전자기 스펙트럼 내에 가시광선의 영역을 뜻한다.

가시광선의 주파수(Frequency) 추정 범위는 $4 \times 10^{14}$ hz ~ $8 \times 10^{14}$ hz(400 THz ~ 800 THz) 이다.

가시광선의 파장(Wavelength) 추정 범위는 750 nm ~ 380 nm 이다.

![[electromagnetic_spectrum.webp]]

참고 : [적외선(Infrared)](https://en.wikipedia.org/wiki/Infrared)과 [자외선(Ultraviolet)](https://en.wikipedia.org/wiki/Ultraviolet)은 가시광선에 속하지 않지만 특수 카메라를 사용하여 볼수가 있다.

#### 광자
[파동-입자 이중성(Wave-Particle Duality)](https://en.wikipedia.org/wiki/Wave%E2%80%93particle_duality)에 의하면 빛은 파동(Wave)이며 입자(Particle)이다.

빛 입자를 광자라고 한다. [광자(Photon)](https://en.wikipedia.org/wiki/Photon)는 전자기 에너지의 묶음이며, 모든 빛을 구성하는 [기본 입자(Elementary Particle)](https://en.wikipedia.org/wiki/Elementary_particle)이다.

참고 : 기본 입자는 다른 입자를 구성하는 가장 기본이 되는 입자를 뜻한다. 가장 기본이 된다는 뜻은 다른 입자로서 구성이 되지 않는다는 것이다 (현재 파악된 바로는).

#todo 광자하고 [파동 묶음(Wave Packet)](https://en.wikipedia.org/wiki/Wave_packet) 관련되지 않는가 싶다.

![[wave_packet_propagation.gif]]

#### 단색광
단일 주파수(Single Constant Frequency)로 진동하는 전자기파를 [단색 복사(Monochromatic Radiation)](https://en.wikipedia.org/wiki/Monochromatic_radiation)라 부른다. 단일 주파수로 진동하는 가시광을 __단색광(Monochromatic Light)__ 이라 부르며,  일반적으로 [Spectral Color](https://en.wikipedia.org/wiki/Spectral_color)로 불리는 경향이 있다.

단색광이란 이름이 좀 어색한데, 그냥 "하나의 색"인 _단색_ 으로 이해해도 크게 문제 없을 듯 하다. 단색광은 그저 하나의 주파수가 하나의 색을 이룬다는 개념을 기준으로 하나의 색을 갖춘 빛이라 보면 된다.

참고 : 우리가 일반적으로 보는 빛은 여러 주파수로 이루어져 있는 [다색광(Polychromatic Light)](https://ballpen.blog/조명-다양한-용어-정리/#1__Monochromatic_light_and_Polychromatic_light)이다.

하나의 주파수가 하나의 색이라면, 여러 주파수면 여러 색이 보여야 한다는 생각이 들 수있다. 사실 여러 색이 "보여지고" 있는게 맞다. 단지, 사람에게는 여러 색이 완벽히 겹치면 하나의 색으로만 보인다. 이러한 색의 조합은 대부분 가시광선 영역에 있지만, 그렇지 않는 색들도 있다 - 이를 [특단색광(Extra-Spectral Color)](https://en.wikipedia.org/wiki/Spectral_color#Extra-spectral_colors)이라 한다 (대표적인 예는 핑크색이다).

그럼 단색광에 무슨 색들이 속할까?

우리는 일반적으로 단색광을 와 같이 7가지 색으로 분류한다 - 이는 1704년도에 출판된 [아이작 뉴턴(Isaac Newton)](https://en.wikipedia.org/wiki/Isaac_Newton)의 책 [_Opticks_](https://en.wikipedia.org/wiki/Opticks) 에 명시된 [색 상환(Color Cicle)](https://en.wikipedia.org/wiki/Color_wheel)으로부터 비롯되었다.



사실 가시광선의 영역은 연속적(Continuous)이기 때문에 단색광은 무한(infinity)개 있다. 더불어, 완전한 단색광을 재현하는 것은 어렵다 (이유는 양자역학에 관련된 것 같아서 이해하는 것을 포기했다). 우리는 색에 대한 소통을 위해 가시광선의 일부 영역들을 단색광으로 최대한 근접하게(Approximation) 표현하여 구분할 뿐이다.

> | **color** | **Wavelength(nm)** | **Frequency(THz)** |
|:---------:|:-------------------:|:-------------------:|
|<span style="color:#7f00ff;">&block;</span> violet   |       380~450       |       670~790       |
|<span style="color:blue;">&block;</span> blue     |       450~485       |       620~670       |
|<span style="color:cyan;">&block;</span> cyan     |       485~500       |       600~620       |
|<span style="color:#00FF00;">&block;</span> green    |       500~565       |       530~600       |
|<span style="color:yellow;">&block;</span> yellow   |       565~590       |       510~530       |
|<span style="color:orange;">&block;</span> orange   |       590~625       |       480~510       |
|<span style="color:red;">&block;</span> red      |       625~750       |       400~480       |

단색광을 6개로 나누든 7개로 나누든, 몇개로 나누는 것은 크게 상관이 없다. 단색광의 주파수/파장 범위도 마찬가지다. 단지, 다른 사람이 표현하는 단색광이 내가 생각하는 단색광과 주파수/파장 범위에 있어 차이가 있을수도 있다는 것은 인지하면 좋을 것 같다.

참고 : [남색(Indigo)](https://en.wikipedia.org/wiki/Indigo)을 구분할 수 없는 사람이 꽤 있어서, 단색광 구분에 제외될 때 가 있다.

![[visible_spectrum.svg]]

단색광은 무엇보다 순수한/완전적인(Pure) 색이기 때문에, 연구가치가 높다. 단색광으로부터 [[#메타메리즘]], [[#가산혼합]], [[#감산혼합]] 같은 이론들이 나온다.

참고 자료 : [사이언스올 과학백과사전 - 단색광](https://www.scienceall.com/%EB%8B%A8%EC%83%89%EA%B4%91monochromatic-light-3/)

### 광원
[광원(Light Source)](https://en.wikipedia.org/wiki/Light#Light_sources)은 제 스스로 빛을 발하는 물체 또는 장치를 뜻한다.

광원으로부터 나오는 빛은 색에 영향을 주기 때문에 광원이 무엇인지, 광원으로부터 나오는 빛의 [분광 분포(Spectral Power Distribution)](https://en.wikipedia.org/wiki/Spectral_power_distribution)가 어떻게 되는지 알아봐야 한다.

참고 : 파장 또는 주파수를 가로축(x-axis), 빛의 강도를 세로축(y-axis)으로 빛의 분포를 표현한 그래프를 분광 분포라고 한다.

#todo 자리 찾아주기 - > 단색광에 제일 근접한 것은 [레이저(Laser)](https://en.wikipedia.org/wiki/Laser)이다.

#### 흑체
광원을 제대로 이해하기 위해서는 우선 물체가 어떻게 빛을 발하는지 좀 이해해야 할 필요가 있다 - 특히 빛 중에 제일 기초라고 볼 수 있는 태양광을 이해해야 한다.

우리는 어릴때 불(Fire)과 태양(Sun)을 보면서 "뜨거운 것은 밝게 빛난다"를 배운다. 좀 더 나아가, 토마스 에디슨(Thomas Edison)의 발명품, [백열등(Incandescent Light Bulb)](https://en.wikipedia.org/wiki/Incandescent_light_bulb)에 대하여 배우며 전기로 물체를 가열시키면 빛이 난다는 것을 배운다.

열과 빛이 관련이 있다는 사실, 이 개념은 흑체 복사(Blackbody Radiation)로부터 비롯된다(아마도). 흑체 복사에 대하여 설명하긴 너무 어려워서 일단 핵심 내용만 알아본다.
1. [흑체(Blackbody)](https://en.wikipedia.org/wiki/Black_body)는 모든 파장의 전자기파를 완전히 흡수하는 가상/이상의 물체이다. __밀도를 가진 모든 물체는 에너지를 흡수하고 방출한다.__
2. __모든 물체는 흑체이지만, 완벽한 흑체는 아니다.__ 완벽한 흑체는 이론적으로만 가능하기 때문에 가상/이상의 물체라고 하는 것이다.
3. 흑체는 전자기파의 에너지를 열 에너지로 변환한다. 따라서, 흑체는 빛을 받으면 가열한다.
4. [흑체 복사](http://www.ktword.co.kr/test/view/view.php?m_temp1=3907) [(Blackbody Radiation)](https://en.wikipedia.org/wiki/Black-body_radiation)는 가열된 흑체에서 나오는 [전자기파](https://en.wikipedia.org/wiki/Electromagnetic_radiation)이다.
5. 흑체 복사는 [열 복사(Thermal Radiation)](https://en.wikipedia.org/wiki/Thermal_radiation)이라 불리기도 한다.
6. 흑체 복사는 여러 범위의 주파수/파장으로서 이루어지며,(열이 충분히 높으면) 그 중 일부가 가시광선 영역에 있다. 온도에 따라서 색상(Hue)도 변한다 - 그래서 광원의 색을 명시할 때 Kelvin(K) 단위의 [색 온도(Color Temperature)](https://en.wikipedia.org/wiki/Color_temperatur)로 표현하게 된다.

불은 뜨거울수록 파랑색으로 변한다고 들었는데, 색 온도 차트를 보면 딱 그 말이 맞다는 것을 볼 수 있다.

![[Color_temperature_black_body_800-12200K.svg]]

태양(Sun)과 별들은 거~의 완벽한 흑체라고 한다.

인간의 눈은 태양광에 최적화가 되어있다. 따라서, 어느 특정 물체의 색(Color)을 볼때 태양광 또는 태양광에 가장 유사한 빛을 물체에 빛추어 보는게 제일 선호된다.

![[sunlight_spectrum_comparison_02.PNG]]

분광분포로 봤을때 가시광선 영역 전체가 연속적\*으로 이어진 빛을 [Full Spectrum Light(FSL)](https://en.wikipedia.org/wiki/Full-spectrum_light)이라고 한다. 한 마디로, FSL은 가시광선의 모든 색을 방출한다 - 이론적인 하얀색(White)에 제일 가깝다고 보면 될 것 같다.

\* 연속성(Continuity) : 빛의 여러 주파수 사이에 급격한 하락이 없이 쭉 이어진다. 빛이 가시광선의 모든 주파수를 포함한다는 뜻이며, 그만큼 모든 색을 갖추고 있다.

태양광이 FSL이다. 태양광은 모든 색을 연속적으로 방출한다.

![[color_temperature_spectral_distribution.png]]

분광 분포의 연속성은 광원의 질(Quality)로 이어진다. #todo 아직 완전히 정리되지는 않았지만, 질은 분명 색감(색으로부터 받는 느낌)에 영향을 준다.

어떤 물체를 태양광으로 비추어본 것과 형광등으로 비추어본 것에는 색에 아주 미세한 차이가 있겠지만, 태양광으로 비추어진 색이 훨씬 생생(Vibrant)할 것이라 생각한다(증명할 방법은.. 뭐, 없다).

![[sun_vs_flourescent_spectrum_comparison.PNG]]

태양광과 백열등은 흑체 복사 기반 광원에 속한다. 반면에, 형광등과 LED는 흑체 복사 기반 광원이 아니다. 광원은 꼭 흑체 복사 기반이어야 하는 것은 아니다. 단지, 색의 연구는 태양광이 기초가 되었기에 흑체 복사에 대한 이해가 중요하다.

#todo [광원의 종류](https://en.wikipedia.org/wiki/List_of_light_sources)는 많은데, 굳이 이 섹션에서 다룰 필요는 없을 것 같다.

![[light_source_spectrums.png]]

참고 자료 1 : [키르히호프의 복사 법칙(Kirchhoff's Law of Thermal Radiation)](https://en.wikipedia.org/wiki/Kirchhoff's_law_of_thermal_radiation)
참고 자료 2 : [How objects emit radiation](http://www.ccpo.odu.edu/SEES/ozone/class/Chap_4/4_6.htm)

#### 표준 광원
#todo 메타메리즘 섹션으로 이동. 굳이 광원 관련 내용이라고 광원 밑에 있을 필요가 없다. 오히려 스토리 전개에 방해가 되는 듯 싶다.

색은 조건에 따라 다르게 보일수 있기 때문에([[#메타메리즘]]), 물체의 색을(전문적으로) 구분할 때 최대한 일정하고 적합한 환경을 구성하는게 중요하다. 대중적으로 많이 사용되는 광원이 주로 이 용도로 선택된다.

[표준 광원(Standard Illuminant)](https://en.wikipedia.org/wiki/Standard_illuminant)은 색을 기준으로 물체와 광원의 관계를 표준화하기 위해 사용되는 광원을 뜻한다. 간단하게, 물체의 색을 구분할 때 적합한 광원이라 볼 수 있다.

표준광원은 어느 특정 브랜드, 모델을 확정지는게 아니다 - 표준광원은 이론적(Theoretical)일 뿐이다. 한 마디로, "최대한 이 정도 수준의 광원을 사용하시오~"하는게 표준광원이라 볼 수 있다.

표준광원은 용도에 따라 여러 종류가 있다.

1. _광원 A_ : 일반적으로 사용되는 백열등(텅스텐 필라멘트, 색온도 2856 K)
2. _광원 B_ : 대낮 태양의 평균 태양광(색온도 4900 K)
3. _광원 C_ : 흐른 하늘 낮의 평균 태양광(색온도 6800 K)
4. _광원 D 시리즈_ : 실제 대낮의 태양광을 측정하여 얻은 평균 직사량
5. _광원 E_ : ??? 이해하는 것 포기
6. _광원 F 시리즈_ : 일반적인 형광등 수준

위 목록 외에 더 있음을 참고해야 한다. 시리즈는 해당 표준광원에 하위 카테고리가 있다는 뜻이다.

참고 자료 1 : [정보통신기술용어해설 - 표준 광원](http://www.ktword.co.kr/test/view/view.php?m_temp1=4526)

## 빛의 특성
빛은 [[#반사]], [[#투과]], [[#흡수]]라는 세 가지 중요한 성질을 갖는다. 그 외에 굴절(Refraction), 회절(Diffraction), [[#산란]], 분산(Dispersion) 등이 있다.

![[surface_effects_illumination.png]]

![[light_properties.png]]

빛의 특성에 대하여 더 자세히 정리하기 앞서 빛에 대한 이해를 보조하기 위한 모델링이 필요하다.

![[wavefronts_and_ray.png]]

### 빛의 모델링
빛은 파동이기 때문에 모델링하기 엄청 번거롭다! 심지어 양자역학(Quantum Mechanics)과 관련되어 빛이 [파동-입자 이중성(Wave-Particle Duality)](https://en.wikipedia.org/wiki/Wave%E2%80%93particle_duality)을 가진다고 하니, 이런걸 어떻게 모델링 할까? 결국에 답은 아주 간단하게 선 하나 그리는 것이고, 그게 바로 광선이다.

[광선(Ray)](https://en.wikipedia.org/wiki/Ray_(optics))은 빛의 이상적인 모델로서 에너지 흐름의 방향을 가르키는 선으로 표현되며, 실제 빛의 [파면(Wavefront)](https://en.wikipedia.org/wiki/Wavefront)에 수직(Perpendicular)인 선을 선택함으로써 얻을 수 있다. 광선은 광학계(Optical System)를 통한 빛의 전달을 모델링하는데 사용된다.

광선은 7 가지로 분류된다.
1. 입사
2. 반사
3. 투과
4. 굴절
5. 발산
6. 수렴
7. 창발

![[plane_of_incidence.PNG]]

입사파(Incident Wave) 또는 __입사광선(Incident Ray)__ 은 물체를 향해 다가가는 광선을 뜻한다.

반사파(Reflected Wave) 또는 __반사광선(Reflected Ray)__ 은 물체 표면에 부딛혀 반사되어 나오는 광선을 뜻한다.

투과파(Transmitted Wave) 또는 __투과광선(Transmitted Ray)__ 은 물체를 통과하는 빛을 뜻한다. __굴절광선(Refracted Ray)__ 라고 표현되기도 하는데, 이는 광선이  물체를 통과할 때 방향이 틀어진 광선을 뜻한다.

![[types_of_ray.svg]]

__발산 광선(Divergent Ray)__ 는 빛이 넓어지며 나가는 빛을 뜻한다. 반대로, __수렴 광선(Convergent Ray)__ 는 빛이 얇아지며 나가는 빛을 뜻한다.

[창발광선(Emergent Ray)](https://www.photonics.com/EDU/emergent_ray/d3818)은 물체의 두 표면을 투과하고 나오는 광선을 뜻한다. 일반적으로 사용되는 단어는 아닌 듯 싶은데, 주로 [[#굴절]]과 관련되어 나올때가 있다.

### 파동 전파
[파동 전파(Wave Propagation)](https://en.wikipedia.org/wiki/Wave_propagation)는 파동이 이동하는 모든 방식을 뜻한다. 빛은 입자이며 파동이니, 파동이 이동하는 방식을 우선 정리해본다.

아인슈타인이 정의한데로, 진공(Vacuum)에 [빛의 속도](https://en.wikipedia.org/wiki/Speed_of_light)는 대략 300,000 km/s 이며, [특수 상대성 이론(Special Relativity)](https://en.wikipedia.org/wiki/Special_relativity)에 따르면 빛의 속도는 상수(Constant)이다.

진공은 빈 공간이고, 빛은 진동인데, 그럼 빈 공간에서 무엇이 진동하는 것일까?

진공은 사실 "모든 것"이 비어있는게 아니다 - 세계 모든 곳에 [전자기장(Electromagnetic Field)](https://en.wikipedia.org/wiki/Electromagnetic_field)이 존재하며, 진공에도 마찬가지로 전자기장이 존재한다. [[#가시광선]] 섹션에서 정리했듯이, 빛이 [전자기파(Electromagnetic Radiation)](https://en.wikipedia.org/wiki/Electromagnetic_radiation)라는 것을 다시 상기해보면, 진공에서 빛은 전자기장의 변화 또는 진동이라고 볼 수 있다.

![[electromagnetic_wave.png]]

참고 1 : 장(field)은 사실 공간을 뜻한다. 전자기장이 "존재한다"기 보다는, __공간의 특성__ 이라 이해하는게 좋다. 좌표계(Coordinate System)와 유사하다고 생각하면 될 것 같다. 전자기장이 있는 이유까지 따지게 되면, 빅뱅 이론까지 가버리기 때문에 여기서 멈춘다..

참고 2 : 광자는 질량(Mass)이 없기 때문에 거~의(?) 붕괴(Decay)하지 않는다고 한다. 가시광선 광자는 $10^{18}$ 년 이상은 안정적일 것이라고 한다. - [소스](https://physics.aps.org/articles/v6/s96)

빛이 전자기장을 통해 이동한다면, 물체와 어떻게 상호작용을 할까?

일단 광자(Photon)와 원자(Atom)의 상호작용을 알아본다.

광자가 원자와 충돌하면, 원자는 __들뜬 상태(Excited State)__ 로 변한다. 들뜬 원자는 다시 __바닥 상태(Ground State)__ 로 안정화하기 위해 진동을 하며, 이 진동이 열 에너지를 방출하거나 또는 광자를 방출한다.

참고 1 : 원자가 열을 내는것인지, 광자가 열을 내는것인지 좀 헷갈린다.

참고 2 : 광자를 방출하는 방향은 무작위(Random)하다.

원자에는 [고유 진동수(Natural Frequency)](https://en.wikipedia.org/wiki/Natural_frequency)가 있다. 광자의 주파수와 원자의 고유 진동수의 차이로서 방출되는 열 에너지 수준과 광자 주파수가 결정이 된다.

> ![[Bohr_atom_model_of_hydrogen.svg]]
> 수소(Hydrogen) 원자의 Bohr 원자 모델. 수소 원자의 에너지 레벨이 3에서 2로 낮아질때 파장 656 nm(빨간색) 광자가 방출된다.

가시광선의 파장은 원자보다 크기 때문에 상호작용을 하지 않는다\*. 따라서, 원자는 색이 없다. 가시광선과 상호작용을 하기 위해서는, 원자들이 붙어있는 조직이어야 한다 - 원자 간의 거리와 원자들이 정리된 구조가 색에 영향을 준다.

\* 사실 전자기파는 파장보다 작은 입자와도 상호작용을 하긴 한다. 광자와 원자가 충돌할 때 원(Original) 광자 에너지와 동일한 에너지를 가진 광자 1개가 방출되거나, 또는 에너지의 합이 원 광자 에너지와 동일한 여러 개의 광자가 방출될 수 있다 - 이를 [[#산란]]이라고 한다. "상호작용을 하지 않는다"라고 표현한 이유는, 빛-물체 상호작용에 있어 산란을 따로 분리해야 좀 더 근사한(Approximation) 정리를 할 수 있기 때문이다.

참고 : (나의) 편의를 위해서 분자들의 조직을 물체 또는 물체의 입자라고 표현한다.

빛(__가시광선 광자__)이 물체(__분자들이 붙어있는 조직__)와 충돌하면, 물체는 빛을 흡수하고 열과 빛을 방출한다.

여기서 광자는 하나의 원자와 충돌하는게 아니라, 원자들로 이루어진 조직 전체와 충돌함으로, 빛-원자 상호작용과는 약간의 차이가 있다. 빛-원자 상호작용에서 방출되는 광자의 방향이 무작위한 반면, 빛-물체 상호작용에서 방출되는 광자는 방향성이 명확하다.

빛-물체 상호작용에서 빛은 흡수, 반사, 투과한다. 빛이 흡수됨은 빛 에너지가 열로 전환되었음을 뜻하고, 반사와 투과는 빛 에너지가 물체로부터 광자를 방출시켰음을 뜻한다. 반사와 투과의 구분은 광자가 방출되는 방향에 따라 정해진다.

투과는 빛이 물체를 통해 "이동"하는 것처럼 묘시가 되는데, 빛이 진공간에서 전자기장을 통해 이동하는 것과 달리, 광자가 입자에 충돌하며 새로운 광자가 방출되고 이웃 입자에도 똑같이 반복되며 "전달"된다(빛이 물체를 완전히 통과하거나 또는 완전히 흡수될때까지). 이는 마치 이어달리기(Relay)와 유사하다.

![[relay_race.PNG]]

참고 : [[light_matter_interaction|빛-물질 상호작용]] 노트

### 산란 반산 차이
#todo 파동 전파에 광자-입자 상호작용 부분을 따로 빼서 설명하고, 이를 "산란"을 위주로 다시 설명하는게 좋을 듯 하다.

광자-입자 상호작용에 있어, 
1) 광자가 흡수되고 새로운 광자가 생성되는 현상을 [Inelastic Scattering](https://en.wikipedia.org/wiki/Inelastic_scattering) 이라고 한다.
2) 광자가 흡수되지 않고 그대로 이동하거나 또는 튕겨나가 방향이 틀어지는 현상을 [Elastic Scattering](https://en.wikipedia.org/wiki/Elastic_scattering) 이라고 한다.

반사하고 산란이 헷갈렸던 이유는, 반사와 산란이 다른 개념인지 같은 개념인지가 애매했기 때문이다. 하지만 다시 알아보니, 산란은 빛-물체 상호작용 전체를 뜻하는 아주 상위 개념인 것이다.

참고
- https://physics.stackexchange.com/a/578839
- https://physics.stackexchange.com/a/485576

#### 비탄성 산란
광자가 흡수되고 새로운 광자가 생성되는 현상을 [비탄성 산란(Inelastic Scattering)](https://en.wikipedia.org/wiki/Inelastic_scattering) 이라고 한다. 

정확히는, __Inelastic Scattering은 광자와 원자가 충돌함으로 광자의 에너지가 유지되지 않는 현상을 뜻한다.__ 광자의 에너지가 유지되지 않는 다는 것은, 광자의 에너지가 원자로 전해지거나 또는 원자의 에너지가 광자로 전해지는 것을 말한다 (광자의 에너지가 흡수되거나 증가된다).

광자의 에너지가 흡수되는 경우,  원자 에너지 레벨과 광자 에너지의 차이로서 발생하는 결과가 다르다.
1. 광자 에너지가 충분하여 원자 에너지 레벨이 올라가는 경우, 원자 에너지 레벨이 내려가며 새로운 광자가 방출된다.
2. 원자 에너지 레벨이 여러 단계 올라가서, 한번에 모두 내려가는 경우 입사 광자의 에너지와 동일한 수준의 광자가 새로 방출된다.
3. 원자 에너지 레벨이 여러 단계 올라가서, 한 단계씩 내려가는 경우 여러 광자가 방출되며, 이 광자들의 에너지 총합이 입사 광자의 에너지와 동일하다.

#todo 광자의 주파수가 원자의 에너지 레벨과 일치하지 않는 경우 Elastic Scattering이 발생한다? 이 부분에 대해서 좀 더 찾아봐야 할 듯. 

광자의 에너지가 흡수되고도 광자가 발생되지 않는 경우가 있다. 이러한 경우, 에너지가 다른 에너지로 변환되거나 이웃 원자에 전달된 것일 수 있다 - [참고](https://www3.uwsp.edu/cnr-ap/KEEP/nres633/Pages/Unit2/Section-B-Energy-Transfer.aspx)

#### 탄성 산란
[탄성 산란(Elastic Scattering)](https://en.wikipedia.org/wiki/Elastic_scattering)

### 반사
[반사(Reflection)](https://en.wikipedia.org/wiki/Reflection_(physics))는 광선이 물체의 표면에 도달하여 다른 방향으로 튕겨 나가는 현상을 의미한다. 더 자세하게는, 반사는 광선이 두 물체 사이의 경계선에 도달하여 이동하던 방향의 반대 방향으로 이동하는 현상을 의미한다.

빛이 빛의 파장(Wavelength)보다 큰 장애물에 부닥칠 경우에 반사된다고 한다.

![[cat-mirror.gif]]

#### 반사 모델링
반사를 이해하려면 일단 간단한 모델링이 가능해야 한다.

물체의 표면을 기준으로 수직선을 그린 것을 [법선](https://keystagewiki.com/index.php/Normal_(Physics)) [(Normal)](https://en.wikipedia.org/wiki/Normal_(geometry))이라고 하면, 법선을 기준으로
- 입사광선이 표면에 도달하는 각도를 __입사각(Angle of Incidence)__ 이라 한다.
- 반사광선이 표면에서 반사되어 나가는 각도를 __반사각(Angle of Reflection)__ 이라 한다.

입사광선과 반사광선은 동일한 평면(Plane)에 위치하는데, 이 평면을 [입사면(PoI, Plane of Incidence)](https://en.wikipedia.org/wiki/Plane_of_incidence)이라 한다.

![[reflection_3d_model.svg]]

#### 반사의 법칙
빛은 [반사의 법칙(Law of Reflection)](https://www.physicsclassroom.com/class/refln/Lesson-1/The-Law-of-Reflection) 을 따른다 :
1. 입사각과 반사각은 동일하다.
2. 입사광선과 반사광선은 동일한 평면에 위치한다([Coplanar](https://en.wikipedia.org/wiki/Coplanarity)).

참고 : 음파(Sound Wave)도 반사의 법칙을 따른다.

> ![[wave_reflection_animation.gif]]
> 빛 파동의 반사 시뮬레이션 - [Ripple Tank Simulation](http://www.falstad.com/ripple/)

반사의 법칙은 [유클리드(Euclid, 300 BC)](https://en.wikipedia.org/wiki/Euclid)가 일부 발견했고, [르네 데카르트(René Descartes)](https://en.wikipedia.org/wiki/Ren%C3%A9_Descartes)가 [[#굴절의 법칙]]과 함께 반사의 법칙을 완성시켰다.

참고 : 유클리드는 빛이 눈에서 발산된다고 믿었다..

#### 반사의 종류
반사는 정반사와 난반사, 이 두 가지로 분류가 된다.

![[reflection_comparison_01.PNG]]

##### 정반사
[정반사(Specular Reflection)](https://en.wikipedia.org/wiki/Specular_reflection)는 거울처럼 매끈한 면을 경계로 일어나는 반사를 말한다. 거울반사 또는 경면반사로고도 부른다.

> ![[chicago_the_bean.png]]
> 시카고(일리노이주, 미국)에 있는 _The Bean_ 이다.

정반사를 광선으로 모델링해보면 - 광원으로부터 서로 근접한 여러개의 광선이 같은 방향으로 나오고 이 광선들이 동일한 평평한 면에 부탁치면, 이 광선들의 입사각이 동일하게 되며, 마찬가지로 반사의 법칙에 따라 반사각이 동일하게 된다.

![[specular_reflection_diagram.png]]

어떤 물체에 거울처럼 다른 무언가가 비춰진다면 그게 정반사라 이해하면 된다. 그 무언가는 주변에 있는 물체라던지, 또는 물건을 비추는 광원이 될 수가 있다.

굳이 거울과 같이 주변 물체를 그대로 비추는게 아니더라도, 반짝거리는 것이 보이면 그것이 정반사라 이해하면 된다. #computer_graphics 분야에서는 이렇게 반짝거리는 부분을 [Specular Highlight](https://en.wikipedia.org/wiki/Specular_highlight)이라 부른다.

![[specular_highlight_example_01.png]]

완전히 정반사를 일으키는 물체는 없다 - 어디서 주워들은 말로는 우리가 평상시 사용하는 거울이 95% 정반사를 일으킨다고 한다.

무조건 매끈한 면이라고 정반사가 일어나는 것은 아니다 - 아무리 매끈하다고, 대리석이 거울처럼 되는 것은 아니다. 다른 물질에 비해 금속이 유난히 반사를 잘 하는 것 같은데, 이는 [[#물체의 특성]]과 관련되어 있다.

![[smooth_marble.png]]

##### 난반사
[난반사(Diffuse Reflection)](https://en.wikipedia.org/wiki/Diffuse_reflection)는 거친(Rough) 면을 경계로 여러 방향으로 일어나는 반사를 말한다. 확산반사라고도 한다(근데 어떤 자료에서는 확산반사하고 난반사가 다른 것처럼 여기기도 한다).

참고 : 굳이 확산반사라 안하고 난반사라 한 이유는, "난장판"의 난(亂)이 더욱 직흥적이다 느껴서 그렇다.

난반사를 보다 정확히 설명하자면, 난반사는 서로 근접한 여러개의 광선이 같은 방향으로 이동하여 거친 면에 충돌하고, 각 광선의 입사각이 서로 다르기에 여러 방향의 반사광선이 발생하는 현상이다\*.

\* 주의 : 사실 이건 좀 잘못된 설명이다. [[#난반사의 오해]] 참고.

![[diffuse_reflection_diagram.png]]

"반사"라고 주변에 무언가가 비춰보여야 될 것 같은데, 그건 아니다. 정반사가 거울 같은 현상이라면, 난반사는 그 반대로 물체 자체가 보이는 현상이다.

> ![[wooden_ball.png | 300]]
> Blender로 그려진 나무 공이다. 반짝임(정반사)가 매우 적어 난반사 예시로 보기 좋다.

난반사가 "거친 면"에 발생한다고 하되, 아주 아주 미세하게 거친 것을 뜻한다. 빛의 크기나 광선간의 거리를 재는 것은 거의 불가능하지만, 빛의 파장(750 nm ~ 380 nm) 보다 작은 정도의 거침이 아닐까 싶다.

![[microscopic_view_on_diffuse_reflection.png]]

참고 : [인간의 촉각은 13 nm 까지 인식이 가능하다.](https://www.nationalgeographic.com/culture/article/130912-tactile-touch-perception-nanometers-psychology-science)

###### 난반사의 오해
난반사가 빛이 거친면으로 인해 여러 방향으로 반사되는 현상이라는 것은 사실 일부만 맞는 정의이다.

보다 올바른 정의는, 난반사는 [[#산란]]으로 인해 빛이 반사되어 보이는 현상을 뜻한다. 

정반사는 빛이 [[#반사의 법칙]]을 따라 광선이 입사각을 비례하여 하나의 방향으로 반사됨을 뜻하며, 난반사는 반사의 법칙을 따르지 않고 입사각에 상관없이 광선들이 여러 방향으로 반사됨을 뜻한다.

난반사와 관련되어 [[reflections_by_subsurface_scattering_hanrahan_krueger_1993.pdf | 하위 표면 산란으로 인한 반사]] 논문을 읽어보는게 좋을 것 같다.

#todo 난반사에 대하여 나중에 다시 정리할 필요가 있다 - "거친면"으로 인해 여러 방향으로 반사된다는 것은 틀린 정보인걸까? 거친면으로 인해 입사각이 달라 여러 방향으로 퍼지는 정반사도 난반사에 속하는 것일까? 거친면보다는 입자와 입자간의 "결합(Bond)"가 더 중요한게 아닐까?

정반사는 광원의 색을 그대로 본다는 것과, 난반사는 물체의 색을 본다는 것을 좀 더 깊게 생각해 볼 필요가 있다.

> "Actually, diffuse and specular reflection operate simultaneously from most materials, and evidently by quite distinct processes, in that the specular reflection typically retains the colour of the light source, while the diffuse reflection is often coloured by the material." - [_Basics of Light and Shade_](http://www.huevaluechroma.com/021.php) by David Briggs



#### 반사율
반사율은 물체 표면에 광선이 반사되는 수준을 뜻한다.. 하지만, 이게 자세히 보니까 아주 아주 복잡하다. 반사율을 영어로 보면 Albedo, Reflectivity, Reflactance가 나오는데, 이게 각각 정의가 좀 다르면서 엄청 복잡하다!! #todo 반사율은 나중에 좀 더 삽질해본다.

#### 반사에 대한 추가 정리
일반적으로 정반사와 난반사는 같이 발생한다.

물질의 특성에 따라 반사하는게 다르다. 자세한 사항은 [[#물체의 특성]]에서 정리한다.

밑에는 정반사와 난반사를 비교하는 그림들이다.

![[reflection_on_surface_comparison_01.png]]

![[reflection_comparison_02.png]]

![[diagram_roughness.png]]

![[5_lights.PNG]]

참고 자료 : [Reflection에 대한 잘못된 상식들](https://lifeisforu.tistory.com/383)

### 투과
투과(Transmission)는 빛이 물체를 통과하는 현상을 뜻한다.

![[light_transmission_example_01.webp]]

투과 자체에 대한 정보는 많이 없다. 심지어 Wiki 페이지도 없다. 대신에, 투과와 마치 동의어로 여겨지는 [[#굴절]]에 대한 정보는 많다. 투과는 빛이 물체를 통과하는 현상을 뜻하고, 굴절은 빛이 물체를 투과하며 생기는 현상을 가르키는 듯 하다.

#### 투과율
__투과율__ 은 [Transmittance](https://en.wikipedia.org/wiki/Transmittance), [Transmissivity](https://www.collinsdictionary.com/de/worterbuch/englisch/transmissivity), 또는 [투과 계수(Transmission Coefficient)](https://en.wikipedia.org/wiki/Transmission_coefficient#Optics)로 불린다.. 각 용어에 따라 정의가 다르긴 한데, 일단 여기선 넘어간다([참고 자료 1](https://www.swiftglass.com/blog/key-differences-transmission-transmittance-apply-application), [참고 자료 2](https://www.iesve.com/support/ve/knowledgebase_faq/faq/1282))

Maya의 [투과율 조절 가이드](https://docs.arnoldrenderer.com/display/A5AFMUG/Transmission)를 참고해보면 좋을 것 같다.

##### 투명도
빛이 투과한다는 것은 물체가 [투명(Transparent)](https://en.wikipedia.org/wiki/Transparency_and_translucency)하다는 것과 동일하다.

![[maya_transmission_example.png]]

투과율/투명도에 따라 적용되는 용어는 다음과 같다.
- 투명 : 빛이 물체를 완전히 통과함(투과율 1\*)
- 반투명(Translucent) : 빛이 물체를 일부 통과함(0 < 투과율 < 1)
- [불투명(Opaque)](https://en.wikipedia.org/wiki/Opacity_(optics)) : 빛이 물체를 통과할 수 없음(투과율 0)

\* 말이 투과율 1이지, 실제로 완벽한 투과는 아니다.

![[sleeping_pikachu.png | 300]]

#### 굴절
[굴절 Refraction](https://en.wikipedia.org/wiki/Refraction)은 빛이 물체를 투과하면서 방향이 뒤틀려 보이는 현상을 뜻한다.

![[light_refraction_by_water.PNG]]

굴절은 물체의 표면에서만 일어나는 현상이다 - 보다 정확한 표현은, 굴절은 서로 밀도(Density)가 다른 물체와 물체의 경계면에서만 일어나는 현상이다.

![[refraction_diagram.svg]]

굴절로 인해 광선의 각도가 영향을 받은 수준을 굴절각(Angle of Refraction)이라고 한다. 굴절각을 구하는 수식은 [스넬의 법칙(Snell's Law)](https://en.wikipedia.org/wiki/Snell%27s_law)이라고 한다.

![[refraction-of-light-through-a-rectangular-glass-slab.png]]

굴절에 영향을 주는 요소는 3가지 이다.
1. 물체의 밀도
2. 입사각
3. 파장

##### 물체의 밀도에 따른 굴절
빛이 밀도가 더 높은 물체의 표면을 넘어갈 경우, 광선의 방향은 법선(Normal)에 더 가까워진다.

![[refraction_less_dense_to_more_dense.png]]

빛이 밀도가 더 낮은 물체의 표면을 넘어갈 경우, 광선의 방향은 법선(Normal)으로부터 더 멀어진다.

![[refraction_more_dense_to_less_dense.png]]

물체의 밀도가 높을수록 물체를 투과하는 빛의 속도가 느려지며\*, 느려지는 수준을 [굴절율(Refractive Index)]이라 한다. 참고로, 빛의 속도가 느려진다고 해도 파장/진동수에는 영향을 주지 않는다.

\* 주의 : 보통 "빛의 속도가 느려진다"고 표현되는데, 사실 빛의 속도는 일정하되 빛이 전달되는 속도가 느려진다. 빛의 속도는 절대적이며, 불변하다. 빛이 물체를 투과하고 나온 창발광선의 속도는 입사광선의 속도와 동일하다.

일반적으로 밀도가 높은 경우 굴절율이 높되, 항상 선형관계(Linear Relationship)을 이루는 것은 아니다. 따라서, 굴절 또는 그 외의 현상에 대해서 설명할때 밀도 대신 굴절율 위주로 정리가 된다.

굴절율이 낮은 물체에서 높은 물체로 빛이 넘어갈 때 굴절각은 입사각보다 크다. 반대로, 굴절율이 높은 물체에서 낮은 물체로 빛이 넘어갈떄 굴절각은 입사각보다 작다.

한 마디로, 밀도가 높을수록 굴절율이 높고, 굴절율이 높을 수록 굴절각도 높아진다.

##### 입사각에 따른 굴절
입사각이 0이면 굴절각도 0이다. 입사각이 높을수록 굴절각도 높아진다.

##### 파장
https://en.wikipedia.org/wiki/Dispersion_(optics) 참고

##### 굴절 추가 정리
https://byjus.com/physics/tracing-path-of-a-ray-of-light-passing-through-a-glass-slab/


https://flexbooks.ck12.org/cbook/ck-12-middle-school-physical-science-flexbook-2.0/section/19.7/primary/lesson/refraction-ms-ps/

![[light_refraction_by_glass.PNG]]

![[light_refraction_by_heat.PNG]]

##### 굴절의 법칙
굴절의 법칙(Law of Refraction)은 입사각과 굴절각의 관계를 정의한 수식이다.

굴절의 법칙은 [빌러브로어트 스넬리우스(Willebrord Snellius, 1580-1626)](https://en.wikipedia.org/wiki/Willebrord_Snellius)가 발견했다고 [스넬의 법칙(Snell's Law)]([스넬의 법칙(Snell's Law)](https://en.wikipedia.org/wiki/Snell%27s_law))이라고 불리지만, 당시에 [르네 데카르트(René Descartes)](https://en.wikipedia.org/wiki/Ren%C3%A9_Descartes)도 이 사실을 발표했었기에 데카르트의 법칙(Descarte's Law)라고도 불리게 되었다. 관련해서 [[descartes_optics_harvard_jeffrey_mcdonough.pdf | 여러 드라마가 있었다]]고 하는데, 결국엔 서로 독립적으로 발견한 것으로 인정되었다.

사실 이 원리는 훨씬 오래전에 [클라우디오스 프톨레마이오스(Claudius Ptolemy, 100-170 AD)](https://en.wikipedia.org/wiki/Ptolemy)가 일부 발견했었고, 984년에 [이븐 사흘(Ibn Sahl, 940-1000)]이 굴절의 법칙을 완성시켰다.

누가 발견했건, 그냥 굴절의 법칙이라고 부르는게 좋을 것 같다.

참고 : [[brief_history_of_refraction.pdf | 굴절의 역사]]

### 흡수
[흡수/흡광(Absorption)](https://en.wikipedia.org/wiki/Absorption_(electromagnetic_radiation))은 빛이 물체로 인해 [광도(Luminous Intensity)](https://en.wikipedia.org/wiki/Luminous_intensity)가 줄어드는 현상을 뜻한다.

[감쇠(Attenuation)](https://en.wikipedia.org/wiki/Attenuation)라고도 불린다.

모든 물체는 빛의 에너지를 흡수하고 열 또는 다른 에너지로 변환한다. #todo 정확한 이유는 모르겠지만, 물체의 특성에 따라 흡수하는 주파수/색이 다르다.

흡수에 관련한 대표적인 예시는 검은색의 물체이다. [[#광원]] 섹션에 흑체(Blackbody)에 대하여 정리했듯이, 완전한 검은 물체는 모든 빛을 흡수한다. 반대로, 하얀색 물체는 흡수율이 아주 낮다. 

빛은 물체의 표면에서도 흡수되고, 물체를 투과하며 물체 안에서도 흡수된다. 좀 더 자세한 사항은 [[#반사 투과 흡수의 관계]] 섹션에서 정리한다.

#computer_graphics 분야에서는 반사-흡수의 관계보다는 투과-흡수의 관계를 더 중요시 하는 듯 싶다.

[흡수율? 흡수도? 흡광도?](http://www.ktword.co.kr/word/abbr_view.php?m_temp1=5096) 흡수의 수준을 측정하는 단위를 뜻하는 용어가 무엇인지 많이 헷갈린다. 영어로는 [Absorbance/Optical Density](https://en.wikipedia.org/wiki/Absorbance), [Absorptance](https://en.wikipedia.org/wiki/Absorptance), [Absorptivity / Molar Attenuation Coefficient](https://en.wikipedia.org/wiki/Molar_attenuation_coefficient) 가 있는데 차이점을 이해하기 어렵다.

위 용어들을 이해하기 위해서는 아마 감쇠의 관계를 정의하는 [비어-람베르트 법칙(Beer-Lambert Law)](https://en.wikipedia.org/wiki/Molar_attenuation_coefficient)을 봐야 할 것 같다.

`𝑨 = 𝜀𝓵𝑐`

𝑨 : Absorbance
𝜀 : Molar Attenuation Coefficient / Absorptivity
𝓵 : Optical Path length
𝑐 : [Molarity / Molar Concentration]

대충 이해한 바로는, 최종 흡수된 수준은 물질의 흡수하는 성질, 빛이 투과하는 길이, 그리고 밀도(?)의 곱으로서 나온다는 것 같다.

### 회절
Diffraction

![[wave_diffraction.gif]]

thin-film interference
![[light_diffraction_example_01.PNG]]

### 산란
[산란(Scattering)](https://en.wikipedia.org/wiki/Scattering)은 빛이 미세한 입자에 충돌하여 사방으로 퍼지는 현상을 뜻한다.

![[light_scattering_by_particle_size.PNG]]

산란은 [[#반사]]의 상위 개념이라 볼 수 있다.  반사가 Macro 개념이면, 산란은 Micro 개념이라 할 수 있다. 표면 위에 발생하는 산란을 한정지으면 그것이 반사다. 하지만 산란은 반산 뿐만이 아니라, 물체를 [[#투과]]하면서도 발생되는 현상이다.

빛을 쉽게 이해하고 싶을때는 반사와 투과만 모델링하지만, 좀 더 복잡하게는 산란과 함께 모델링 한다.

![[light_interface_interaction_models_diagram.png]]

인터넷에서 산란하고 난반사를 헷갈리게 설명한다. 심지어 오역으로 인해 난반사를 산란광이라고 부르는 자료도 몇 있다. 사실 산란-반사의 관계는 직사각형-정사각형 관계랑 비슷한데, 난반사는 산란에 속하지만 산란이 난반사인 것은 아니다.

영자역학에 속한 [산란 이론(Scattering Theory)](https://en.wikipedia.org/wiki/Scattering_theory)이란 것이 있다.. 이거 완전 클래스가 미쳤다.

산란의 방향성은 Isotropic 와 Anisotropic 으로 분류된다. 사방으로 둥글게 퍼지는가, 아니면 앞쪽으로 퍼지는가의 차이인 듯 싶다.

![[types_of_light_scattering.png]]

__빛은 파장과 입자의 크기가 비슷할 수록 더 많은 산란을 한다.__

산란의 종류 중 대표적인 것으로 레일리 산란와 미 산란이 있다.

#### 레일리 산란
[레일리 산란(Rayleigh Scattering)](https://en.wikipedia.org/wiki/Rayleigh_scattering)은 빛의 파장보다 매우 작은 입자에 빛이 산란되어 일어나는 현상이다.

낮 하늘의 파란색과 저녁 노을이 진 하늘의 빨간색의 원인이 레일리 산란에 있다.

지구 대기권(Atmosphere) 내 공기에 있는 분자(질소, 산소 등)의 크기는 빛의 파장보다 훨씬 작다. 태양광은 이런 미세한 입자들과 충돌하여 산란을 한다. 하얀색, 즉, 모든 색이 산란을 하는데, 이 중 제일 작은 파장을 가진 __파란색이 다른 색들에 비해 입자의 크기와 더 유사하기 때문에 더 많이 산란한다__. 따라서, 하늘의 색이 파란색으로 보인다.

![[blue_sky.png]]

저녁에는 하늘이 기울어 태양광이 지나가는 대기권이 길어지며, 짧은 파장의 파란색은 길어진 빛의 경로에 더 많은 산란을 일으키다가 관측자에게 도달하기 전에 소멸 해버린다. 반대로, 긴 파장의 빨간색은 산란을 덜 일으켰기 때문에 관측자에게 비교적 많이 도달한다. 따라서, 저녁 노을이 진 하늘의 색이 빨간색으로 보인다.

![[sunset_sky.PNG]]

#### 미 산란
[미 산란(Mie Scattering)](https://en.wikipedia.org/wiki/Mie_scattering)은 빛의 파장보다 크거나 비슷한 입자에 빛이 산란되어 일어나는 현상이다.

안개/구름이 흰색으로 보이는 것이 미 산란의 대표적인 예시이다.

구름 안에 작은 물방물의 크기는 빛의 파장보다 크기 때문에 모든 빛을 산란시키고, 이는 하얀색으로 보인다.

![[fog_and_cloud.PNG]]

### 반사, 투과, 흡수의 관계
반사, 투과, 흡수는 동시에 일어나며 [보존 법칙(Law of Conservation)](https://en.wikipedia.org/wiki/Conservation_law)에 따른다.

빛의 에너지를 1이라고 보면, `R(반사율) + A(흡수율) + T(투과율) = 1` 관계가 성립된다.

[[#광원]] 섹션에서 알아본 흑체(Blackbody)는 반사율 0%, 투과율 0%, 흡수율 100% 인 이상적인 완전 물체로 `A = 1`이라 정의할 수 있다.

불투명한 물체는 투과율 0%에 가까우며 `R + A = 1`이라 정의할 수 있다.

__빛에 비추어진 물체의 색은 물체로 인해 흡수되지 않고 투과 또는 반사된 광선의 색이라 볼 수 있다.__

#### 반사와 흡수의 관계
반사와 흡수의 관계를 이해하기 위해서, 투과율이 0인 가상의 불투명 물체를 위주로 정리한다.

투과율이 0이기 때문에, 불투명 물체의 색은 오로지 반사와 흡수된 빛의 색이다. 이 섹션에서는 흡수와 반수 위주로 정리해본다.

빛에 여러 파장이 있다는 것을 고려하면, 하얀색 빛은 [[#단색광]]의 여러 광선으로 표현할 수 있다. RGB(빨강,초록,파랑)로 이루어진 하얀 빛이 하얀 물체, 빨간 물체, 초록 물체, 파란 물체, 그리고 검은 물체에 비추어진다 하면, 결과는 밑에 그림과 같다.

![[reflection_and_absorption_of_light_on_colored_objects.PNG]]

RGB 기준으로 불투명 물체와 빛의 상호작용에 대한 식을 정의한다면, 밑에와 같다.

`W - B =(R + G + B) - B = R + G = Y`

어떤 물체가 파란색의 광선만 반사하고 그 나머지 색의 광선들을 흡수한다면, 그 물체는 파란색으로 인식이 된다.

#todo 여기서 사실 엄청 복잡해지는 것은, 하얀색 빛에서 파란색을 흡수하는 물체는 빨간색과 초록색을 반사한다는 것인데, 이 두 색이 합치면 노란색이 된다는 것이다. 그러면, 물체가 노란색을 제외한 모든 색을 흡수해서 노란색으로 보이는 것과, 빨간색과 초록색만 반사해서 노란색으로 보이는 것과 어떻게 달라 보일까?

그러면 빨간 빛이 파란 물체에 비추어지면 어떻게 될까?

![[colored_lights_on_colored_objects.PNG]]

여기서 더 나아가기 전에, 앞으로 빛의 색과 물체의 색의 상호작용에 관련하여 정리하는 것은 이론적이라는 것을 주의해야 한다. [[#단색광]]에 명시했듯이, 단색광은 이론적인 것이며 실제로 재현하기는 어렵다 - __앞으로 명시될 "어떤 색 빛"(예: 빨간 빛)은 이론적이며, 이 빛에 대한 상호작용 또한 이론적이다.__ 현실 세계에서 "어떤 색 빛"은 생각 외로 여러 색과 섞여 있는 빛일 수도 있으며, 이론적으로 계산된 색과 다른 결과를 보여줄 수 있다. __더불어, 물체의 색 또한 이론적인 요소로, 하나의 색만 완벽히 반사하는 물체는 없다고 볼 수 있다__([불가능은 아니다](https://physics.aps.org/articles/v8/20)).

물체로부터 반사되는 광선이 없으면, 그 물체는 검은색으로 보인다.
- 빛이 없으면 물체는 검은색으로 보인다.
- 빛이 있어도 물체가 검은색이면(모든 빛이 흡수되면) 그 물체는 검은색으로 보인다.
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

#### 투과와 흡수의 관계
투과와 흡수의 관계를 이해하기 위해서, 반사율이 0인 가상의 투명 물체를 위주로 정리한다.


#### 반사와 투과의 관계
[[#반사]]와 [[#투과]]의 관계를 정의하고자 하는 것은 아니다. 단지, 이런 질문을 하고 싶다 - _"반사는 표면에서만 이루어지는가?"_.

보통 Quora 답변들을 안 좋아하는 편인데, 유난히 눈에 띄는 [답변](https://www.quora.com/Why-does-water-only-reflect-on-the-surface/answer/Vivienne-Marcus)을 찾았다.

일단 답은 __"아니다"__ 이다.

이유에 대해서는 좀 더 신빙성있는 자료로 확인해봐야 되지만, 일단 간단히 정리해본다.

애초에 "표면"이란 무엇일까?에 대한 고민을 해볼 필요가 있다. [[#굴절]]을 설명할 때 표면 대신에 두 물체 간의 "경계선"이라 표현한 적이 있다. 이러한 경계선은 추상적인 표현으로, 물체와 물체가 "구분"되는 지점으로 좀 더 자세히 정의할 수 있다. 그럼 구분은 어떻게 되는가? 우리가 인식할 수 있는 "차이(Difference)"가 발생되는 지점으로서 구분이 이루어진다고 본다.

__표면 → 경계선 → 구분 → 차이__

빛에 있어 물체의 "차이"는 무엇이 있을까? 여러가지 있을것 같은데, 일단 여기서는 굴절율(Refractive Index)을 살펴본다.

Quora 답변에 의하면, __반사는 굴절율에 차이가 클 때 발생__ 한다. 반사가 물체 표면에 발생하는 것이 맞되, 딱히 표면에 한정되어 발생한다는 것은 아니다. 이론적으로, 빛이 물체로 투과되었을 경우에도 물체 안에 굴절율의 차이가 있는 경우 반사가 발생할 수 있다. 하지만, 일반 물체 안의 굴절율은 일정하거나 차이가 미미하기 때문에 반사 현상을 관측하기 매우 어렵다.

좀 더 생각해보면, 표면은(시각적으로) 두 면이 있다 - 물체 바깥에서 표면을 바라보는 시각하고, 물체 안에서 표면을 바라보는 시각이 있다.

우리는 흔히 물체 바깥에서 표면을 바라보는 시각만 생각하며, 이 표면 "위"에만 반사가 생긴다고 생각할 수도 있다. 하지만 빛이 물체를 투과할 경우, 표면 "아래"에서도 반사가 일어날 수 있으며, 이러한 반사를 [전반사(Total Internal Reflection)](https://en.wikipedia.org/wiki/Total_internal_reflection)라고 부른다.

![[total_internal_reflection_01.PNG]]

#todo 전반사는 근데 특정 각도에서만 관측된다고 하는데, 이건 더 연구해볼 필요가 있다.

더 나아가, 물체의 표면은 하나 뿐일까? 빛은 물체를 투과하면서 다른 표면에 반사되고 또 반사될 수 있다.

### 빛의 특성 참고자료
참고 자료 1 : [삼성디스플레이 뉴스룸 : 재귀반사](https://news.samsungdisplay.com/29873)

참고 자료 2 : [네이버 블로그 글 : 색상/색체 이론](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=loveandpic&logNo=220356463987)

참고 자료 3 : [물체의 색](https://en.wikipedia.org/wiki/Color#Color_of_objects)

참고 자료 4 : [정보통신기술용어해설 : 입사파, 반사파, 투과파](http://www.ktword.co.kr/test/view/view.php?m_temp1=3863)

참고 자료 5 : [Sciencing - Search "light"](https://sciencing.com/search?google_kw=light)

참고 자료 6 : [유리를 통과하는 빛은 느려지는가?](https://www.physlink.com/education/askexperts/ae217.cfm) - #todo 나중에 글이 없어질 수 있으니, 따로 글로 정리할 것.

참고 자료 7 : [빛이 느려진다면 어떻게 보일까?](https://www.livescience.com/what-if-speed-of-light-slowed-down) - #todo 이걸 [게임](http://gamelab.mit.edu/games/a-slower-speed-of-light/)으로 구현한게 있으니, 나중에 해보자.

참고 자료 8 : http://www.thestargarden.co.uk/Reflection-refraction-and-diffraction.html

<iframe width="560" height="315" src="https://www.youtube.com/embed/cv0bBfiCWAk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

https://ctsciencecenter.org/blog/science-at-play-change-the-color-of-the-world-around-you/

#### 참고할 책
[QED: The Strange Theory of Light and Matter _by Richard P.Feynman_](https://www.amazon.com/QED-Strange-Theory-Light-Matter-ebook/dp/B00BR40XJ6/ref=sr_1_1)

## 물체의 특성
물체는 빛과 관련해서 전도체와 유전체로 분류된다.

#todo 모든 물체가 전도체/유전체로 구분되는지는 모르겠다. 

### 전도체의 특성
[전도체(Electrical Conductor)](https://en.wikipedia.org/wiki/Electrical_conductor)는 전기가 통하는 물질이다. 대표적으로 [금속(Metal)](https://en.wikipedia.org/wiki/Metal)이 전도체이다.

[[#반사]] 섹션에서 정리했듯이, 모든 물체는 빛을 반사 한다. 하지만 전도체는 일반적인 물체보다 더욱 반사하는 특징이 있다. 정확한 이유는 너무 깊게 들어가는 것 같아서, [거울의 원리](https://www.scientificamerican.com/article/what-is-the-physical-proc/)를 설명하는 글에 일부를 가져온다.

> "The oscillating electrical field in the incoming light wave produces a force on the charges inside the mirror. Most of the charges are either too heavy(as is true for the nuclei of the atoms) or too tightly bound(as is true for most of the electrons) to vibrate significantly in response to this field. The comparatively loosely held bonding electrons, along with the free electrons present in metals, can move in response to these electrical forces, however. These electrons oscillate at the same frequency as the incident light, which gives rise to the reflected wave." - Peter N. Saeta, 1999

완전히 이해되는 것은 아닌데, 다른 글들을 참고해보면 비슷한 맥락이다 - __전도체의 전자(Electron)가 빛의 주파수와 동일하게 진동하여 빛을 반사한다__.

동일하게 진동하는 것과 반사하는 것이 어떻게 관련되어 있는가?

[Quora 답변](https://www.quora.com/If-light-reflecting-off-a-mirror-is-due-to-photons-being-absorbed-and-radiated-by-electrons-in-the-reflective-material-why-do-the-photons-reflect-at-the-same-angle-at-which-they-strike-the-mirror-How-do-the/answer/Bill-Otto-5)에 의하면, __전자가 빛의 주파수와 동일하게 진동하여 그 빛을 반사하는게 아니라, 빛을 흡수하고 새로운 빛을 발산하는 것이다__.

#todo 금속 자체의 색이 있어보이는 이유는 금속의 전자가 진동하는 주파수가 그 색의 주파수와 비슷하거나, 또는 흡수하고 반사하는 수준이 주파수마다 다르기 떄문이다 - 라고 생각드는데, 확인이 필요하다.

![[reflection_on_gold.png]]

"금속은 난반사를 하지 않는다"라는 주제로 좀 찾아보면 아주 재밌는 자료들이 나온다.. [참고 1](https://google.github.io/filament/Filament.html#materialsystem/dielectricsandconductors), [참고 2](https://physics.stackexchange.com/a/213535/333609)

### 유전체의 특성
[유전체(Dielectric)](https://en.wikipedia.org/wiki/Dielectric) 또는 [절연체(Insulator)](https://en.wikipedia.org/wiki/Insulator_(electricity))는 전기가 통하지 않는 물질이다. 세라믹, 플라스틱, 유리, 고무 등이 유전체이다.

편의를 위해서 유전체는 일반적인 물체로 생각하는게 좋을 듯 하다. [[#반사]]에 대해서 정리한 내용도 유전체 위주로 이해하는게 좋다.

#### 하위-표면 산란
모든 유전체는 

[하위-표면 산란(Subsurface Scattering)](https://en.wikipedia.org/wiki/Subsurface_scattering)은 


## 메타메리즘
[메타메리즘(Metamerism)](https://en.wikipedia.org/wiki/Metamerism_(color)) : 광원, 관측자, 관측조건 차이에 따라 두 물체의 색이 같아 보이거나 달라 보이는 현상을 뜻한다. 조건 등색으로 불리기도 한다.

![[metamerism.PNG]]

### MCM
[[#삼자극값]]을 구하기 위한 테스트를 [Metameric Color Matching(MCM)](https://isle.hanover.edu/Ch06Color/Ch06ColorMatchExp.html)이라고 한다. 테스트 방식을 간단히 설명하자면,
1. 벽 앞에는 여러개의 조명들이 있고, 벽 뒤에는 __관찰자(Standard Observer)__ 가 있다.
2. 벽에는 구멍이 있어, 관찰자가 구멍을 통해 벽 앞을 바라볼 수 있다.
3. 벽 앞에는 가운데 칸막이로 나누어진 두 공간이 있다. 한 공간에는 [단색광(Monochromatic Light)](https://en.wikipedia.org/wiki/Spectral_color)이 특정 색을 비추고 있고, 건너편 공간에는 빨강, 초록, 파랑 조명이 있어 혼합색을 만든다.
4. 관찰자는 빨강, 초록, 파랑 조명의 강도를 조절하여 혼합색과 단색광의 특정 색을 최대한 매칭해본다.
5. 매칭되면 빨강, 초록, 파랑 조명의 강도가 기록된다. 이 강도가 삼자극값이다.

사실 삼자극값은 MCM 테스트의 부산물이라고 볼 수 있다. MCM은 어느 물리적 객체의 색을 구분하기 위한 테스트이다. 예를 들어, 노란색 가방의 "노란색"과 바나나의 "노란색"이 같다/틀리다를 판단하기 위해, 각 객체를 동일한 하얀색 배경에 하얀색 빛(표준 광원)

참고 : RGB 값이 원추세포가 자극받는 값하고 잘 매칭된다는 이유로 MCM 테스트에서 RGB 조명을 사용했다. 삼자극값이 원추세포의 반응이다~라고 하는게, 사실 여기서 좀 애매해진다.

![[metameric_color_matching_experiment_setup.png]]

위 연구를 실제 진행한 사례들로 1920년도 W. D. Wright 연구와 J. Guild 연구가 있다. 두 연구가 비슷한 시기에 해서 그런지 그냥 Wright-Guild 연구로 불리는 것 같다. Wright-Guild 연구 결과는 CIE 1931 색 모델을 구축하는데 기반이 되었다.

참고 : 1920년 Wright-Guild 연구는 관찰자의 시야각(Field of View)을 2°로 해서 연구가 진행됬는데, 이 정도 시야각은 팔을 쭉 뻗고 보이는 엄지손가락 정도 크기라고 보면 된다. 이게 너무 작다고 여겨져, 1964년도에 10°(주먹만한 크기)로 변경했다고 한다 - [출처](https://www.konicaminolta.com/instruments/knowledge/color/part4/01.html).

사람마다 생체학적으로 좀 다르기 때문에, 삼자극값도 서로 미세한 차이가 보여진다. MCM 테스트는 실제로 여러 사람들을 대상으로 진행되고, 여러 결과를 취합하여 근사치(Approximation)를 계산한다.

> ![[Stiles_and_Burch_49_trichromatic_observers_plot.png]]
> 1955년 Stiles and Burch 연구 데이터를 기반으로 plot된 그래프

MSM는 색에 대하여 아주 중요한 두 가지를 증명한다:
1. 
2. __RGB의 한계__ : 사람이 볼 수 있는 색 중 RGB로 구현할 수 없는 색이 있다. 위 그래프를 보면 RGB 값이 음수로 가는 것을 볼 수 있다. 이 뜻은, 반대편(단색광)에 RGB 조명을 추가해야만이 색들이 매칭될 수 있었다는 것이다.

![[metameric_color_matching_experiment_full_sweep.gif]]

삼자극값은 좀 거창한 정의를 가지고 있지만, MCM 테스트를 이해하고 보면 삼자극값은 그냥 특정 색에 대한 원색(RGB)의 비율로 볼 수 있다.

서로 다른 파장의 색들을 혼합하여 다른 하나의 색을 구현하는 [[#가산혼합]]의 기반이 된다.

참고 자료 1 : [색 매칭 웹 게임](https://color.method.ac/) - MCM하고 크게 관련 있는 것은 아닌데, 프로세스는 비슷하고 색 매칭하는게 얼마나 힘든지 알 수 있다 ㅋ

### 혼합 색상
https://en.wikipedia.org/wiki/Color_mixing

#todo 혼합 색상 내용 넣고 원색 내용 여기로 옮기기

#### 가산혼합
[가산혼합(Additive Color)](https://en.wikipedia.org/wiki/Additive_color)은 3개 색을 혼합하여 모든 색을 구현하는 방식이다.

가산(Additive)의 의미는 빛이 없는 공간(검은색)에 빛을 "더하여" 하얀색으로 만든다는 뜻이다. 다른 말로는, 검은색에 각 색을 "더하여" 여러 색을 구현한다는 뜻이다. 최종적으로 모든 색을 최대 비율로 더하면 하얀색이 나온다.

가산혼합에 사용되는 색을 [원색(Primary Color)](https://en.wikipedia.org/wiki/Primary_color)이라고 부르며, 서로 독립적인 색을 뜻한다 - 서로 독립적인 색은, 둘을 혼합해도 남은 셋째의 색을 만들 수 없다.

#### 감산혼합
[감산혼합(Subtractive Color)](https://en.wikipedia.org/wiki/Subtractive_color)은 가산혼합과 마찬가지로 3개 색을 혼합하여 모든 색을 구현하는 방식이다.

감산(Subtractive)의 의미는 빛이 반사하는 공간(하얀색)에 빛을 "빼서" 검은색으로 만든다는 뜻이다. 다른 말로는, 하얀색에 각 색을 "빼서" 여러 색을 구현한다는 뜻이다. 최종적으로 모든 색을 최대 비율로 빼면 검은색이 나온다.

#### 혼합 색상의 오해
우리는 흔히 파란색과 노란색이 초록색을 만든다고 생각한다. 맞긴 맞을거다, 적어도 감산혼합에 있어서는..

#todo 밑에 자료 위주로 다시 정리

https://colourware.org/2018/05/18/why-yellow-and-blue-dont-make-green

![[blue_yellow_spin.webp]]

## 인간 생체 관련 노트

## 국제조명위원회
[국제조명위원회(CIE, Commission Internationale de l'Eclairage)](https://en.wikipedia.org/wiki/International_Commission_on_Illumination), 영어로는 _International Commission on Illumination_ 이라 불리는 단체는 "조명 과학/기술과 관련한 모든 문제에 대해 국제적 협력 및 정보의 교환을 위한 국제 기국"이다.

[CIE 홈페이지](https://cie.co.at/)

![[cie.png]]

__CIE는 측광, 측색 등에 대한 표준과 측정 수단을 개발하고 결정하는 기관이다.__ CIE 측에서 발표한 표준의 대표적인 예시로 [[#CIE 1931 색 공간]]이 있다. 그 외에 [[#표준 광원]]도 CIE에서 관리한다.

참고 자료 1 : [정보통신기술용어해설 - 국제조명위원회](http://www.ktword.co.kr/test/view/view.php?m_temp1=2643)

## Color Model
[색 모델(Color Model)](https://en.wikipedia.org/wiki/Color_model)은 색과 색들의 관계를 수학으로 표현하는 추상적 모델을 뜻한다. 이 뜻은, 색을 하나 또는 여러 숫자로 표현한다거나, 덧셈, 뺄셈 등 색들의 상호작용(혼합)으로 표현한다는 뜻이다.

[색 공간(Color Space)]는 색 모델을 시각화한 것으로 볼 수 있다. 주로 변수와 변수의 관계를 나타내는 좌표계로 표현된다. 색 모델과 색 공간은 결국엔 같은 것이니, 이 용어들은 자주 혼용된다.

색 모델/공간의 궁극적인 목표는 특정 색을 구현하기 위해 필요한 요소들의 값을 구할 수 있는 등색 함수(Color Matching Function)를 제공함에 있다(예: 초록 = 파랑 + 노랑).

색 모델은 여러 개 있는데, 이 중에(내가 보기에) 제일 중요한 모델은 밑에와 같다.
1. CIE 1931 색 공간
2. 가산혼합 색 모델
3. 감산혼합 색 모델
4. 원통좌표계 색 모델
5. YUV 색 공간

### CIE 1931 색 공간
[CIE 1931 색 공간](https://en.wikipedia.org/wiki/CIE_1931_color_space)은 가시광선(Visible Light)의 파장(Wavelength)과 삼자극값(Tristimulus value)의 관계를 정량적으로 표현한 최초의 색 공간이다.

CIE 1931 색 공간은 CIE RGB, CIE XYZ로 나뉘어 지는데, 일반적으로 CIE 1931 하면 CIE XYZ를 뜻한다. 여기서 다루는 내용도 XYZ를 기준으로 다룬다.

#### 삼자극값
[삼자극값(Tristimulus value)](https://en.wikipedia.org/wiki/CIE_1931_color_space#Tristimulus_values)은 특정 색을 나타내는데 필요한 3 색상(RGB)의 혼합비율을 뜻한다.

인간처럼 특별히 3가지 색상에 민감한 생체를 [삼색형 색각자(trichromat)](https://en.wikipedia.org/wiki/Trichromacy)라 한다. 망막(Retina)에 위치한 시세포(Visual Cell) 중 색상을 구별하는 [원추세포(Cone Cell)](https://en.wikipedia.org/wiki/Cone_cell)는 <span style="background:blue;color:white;">파랑에 반응하는 S-cone</span>, <span style="background:green;color:white;">초록에 반응하는 M-cone</span>, 그리고 <span style="background:red;color:white;">빨강에 반응하는 L-cone</span>, 이 3 종류로 구성되어 있다.

![[how_the_eye_sees_color.PNG]]

![[spectral_sensitivity_of_human_eyes_4.svg]]

여기서 자극/반응은 

각 원추 세포는 어느 특정 색 하나를 구별하는게 아니다. 여러 색들을 감지하되, 다른 원추 세포에 비해 더 많이 자극을 받는 색이 있는 것이다.

RGB 색 공간 위주로 봤을때, 원추 세포는 초록에 가장 반응이 크고, 다음은 빨강, 마지막으로 파랑이다. 이 정보가 중요한 이유는, RGB 색 공간에서 [상대적 밝기(Relative Luminance)](https://en.wikipedia.org/wiki/Relative_luminance)를 추출할 때 이 정보를 기준으로 만들어진 공식을 사용하기 때문이다. 참고로, 현실 세계에서는 노랑-초록색에 가장 반응이 크다.

"자극값"은 어떤 단위의 값이라기 보다는 상대적(Relative) 값이다.

삼자극값을 좀 더 이해하려면, [[#메타메리즘]]

#### 색 공간 시각화
색(Color)이란 개념적으로 [휘도(Luminance)](https://en.wikipedia.org/wiki/Luminance)와 [색도(Chromaticity)](https://en.wikipedia.org/wiki/Chromaticity)의 조합으로 이루어진다. 이 외에 파장(Wavelength)도 포함된다. 삼자극값의 3개의 값에 3개의 색 정보까지, 이 모두를 하나의 좌표계에 그리는 것은 좀 복잡해지고 이해하기도 난잡해진다. CIE 1931 색 공간은 색의 관계를 이해하기에 필요한 정보만 따로 추출하여 2D 좌표계에 표현한 것이다.

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


https://en.wikipedia.org/wiki/Optical_phenomena

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

모든 인쇄기는 CMY(정확히는 CMYK) 색 모델을 사용한다.

마찬가지로 CMY가 아닌 다른 감산혼합 원색도 있지만, CMY가 "얕은 색"을 구현하기 제일 쉬운 조합이기 때문에 사용된다(얕은 색에서 찐한 색으로 가는 것은 가능하지만, 그 반대는 불가능하다).

![[color_mixes.png]]

참고: 모니터에 출력되는 색은 인쇄기로 출력된 색과 다르게 보일 수 있다. 서로 색 모델이 다를 뿐더러, 잉크(Ink)의 한계가 있다. 인쇄기 출력물과 매칭되는 색을 봐야한다면, 포토샵 같은 디자인 전용 프로그램에서 보정을 해줘야 한다.

![[cmyk_conversion.PNG]]

### 원통좌표계 색 모델
원통좌표계(Cylindrical Coordinates)로 표현되는 색 모델이다.

#### HSL & HSV
[HSL & HSV 색 모델](https://en.wikipedia.org/wiki/HSL_and_HSV)은 

### YUV 색 공간
[YUV 색 공간](https://en.wikipedia.org/wiki/YUV)은 [휘도(Luminance)](https://en.wikipedia.org/wiki/Relative_luminance)와 [색차(Chrominance)](https://en.wikipedia.org/wiki/Chrominance)의 관계를 표현한다.

참고 : 색에서 밝기만 따로 추출한게 휘도, 색상만 따로 추출한게 색차라고 볼 수 있다.

![[YUV_UV_plane.svg]]

![[luminance_chrominance_comparison.PNG]]

#todo Luminance, Relative Luminance, Luma의 차이를 잘 모르겠다..

[YCbCr 색 공간](https://en.wikipedia.org/wiki/YCbCr)