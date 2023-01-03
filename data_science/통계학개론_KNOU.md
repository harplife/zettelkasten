# 통계학개론

## Chapter 1
- **기술통계 (Descriptive Statistics)** : 데이터를 수치나 표, 그래프 등으로 요약하여 데이터의 특징을 드러내는 통계 방법
- **추측통계 (Inferential Statistics)** : 데이터를 이용하여 그 데이터가 대표하는 불확실한 전체에 관해 추측하고 그 추측의 신뢰성을 계량화하는 통계방법
- **단위 (Unit)** : 관측되는 개별 대상. 관측 단위 (Observational Unit), 개인 (Individual), 케이스 (Case) 등의 다양한 이름으로 불린다.
- **변수 (Variable)** : 각 단위에 대해 관측되는 특성 (Characteristic, Feature). 필드 (Field) 등의 이름으로도 불린다.
- **관찰값/관측치 (Observation)** : 각 단위로부터 관측한 특성의 값.
- **데이터 (Data)** : 하나 이상의 변수에 대한 관찰값의 모음.
- **모집단 (Population)** : 관심 대상이 되는 모든 개체의 모임.
- **유한모집단 (Finite Sample)** : 개체 수가 유한개인 모집단.
- **무한모집단 (Infinite Sample)** : 개체 수가 무한개인 모집단.
- **표본 (Sample)** : 모집단을 알기 위해 실제로 관측한 모집단의 일부.
- **단순랜덤표집 (Simple Random Sampling)** : 유한모집단에서 n개의 개체로 이루어진 가능한 모든 부분집합이 표본으로 선택될 확률이 같도록 설계된 표본 표집 방법.
- **모수 (Parameter)** : 모집단의 특성을 나타내는 대푯값.
- **통계량 (Statistic)** : 표본의 특성을 나타내는 대푯값.
- 모수의 값을 정확히 추정하기 위해 표본을 표집하는 방법이나, 모수에 근접한 통계량을 구하는 방법, 통계량을 이용한 모수 추정의 신뢰도를 계량화하는 방법 등이 모두 **통계학의 문제**라고 할 수 있다.
- **R**은 통계 분석과 그래프 작성에 쓰이는 무료 소프트웨어이자 프로그래밍 언어이다. **R Development Core Team**에 의하여 지속적으로 유지, 개선되고 있다.
- R은 [CRAN (Comprehensive R Archive Network)](https://cran.r-project.org/) 에서 다운로드 할 수 있다.
- R 설치 도중 '구성 요소 설치' 단계에서 'Message translations' 요소의 체크박스를 해제하는 것이 추천된다 - 이로서 R의 출력 언어가 한글 대신 영어가 된다.
- R 전용 편집기는 RStudio 이다. 하지만 현재 [Posit](https://posit.co/) 으로 이름이 변경되었다. 변경된 이유는 R 뿐만 아니라 Python도 사용될 수 있고, 앞으로 데이터 과학과 관련된 모든 언어와 호환될 것을 목표로 하기 때문이라고 한다.
- 

### 개인 노트
- A singular person or a group of people is a **unit** of people. A **characteristic** or a feature of people can include weight, height, gender, or anything that be observed. An **observation** is the value(s) of a characteristic. A collection of observation(s) is referred to as **data**.
- Example A : There is a group of people. Each person from that group is considered a unit. Weight is the characteristic of people that we are interested in. An observation is made by measuring the weight of each person. This collection of measured values of weight is the data.