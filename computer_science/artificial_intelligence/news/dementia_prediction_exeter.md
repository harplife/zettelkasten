---
aliases: [Dementia Prediction Model, Predicting Progression to Dementia]
tags: [computer_science, artificial_intelligence, research_paper, news]
status: complete
edited: 2021-12-20
---

# Predicting Progression to Dementia
A research team from University of Exeter (United Kingdom) published a study on JAMA Network Open (American Medical Association) titled ___Performance of Machine Learning Algorithms for Predicting Progression to Dementia in Memory Clinic Patients___ in year 2021.

- Objectives :
    1) Assess the ability of machine learning algorithms to predict dementia incidence within 2 years (compared with existing models)
    2) Determine the optimal analytic approach and variables required
- Dataset : medical records of 15,307 patients afflicted with dementia [(NACC)](https://naccdata.org/requesting-data/nacc-data)
- Variables : 258 variables spanning domains of dementia-related clinical measures and risk factors
- Results :
    1) Trained a model to predict dementia (within 2 years) with accuracy around 92%
    2) Identified 6 variables that are critical to dementia prediction (details below)

## 6 Core Variables
1. Clinical judgment of decline
2. Time to complete _[Trail Making Test](https://en.wikipedia.org/wiki/Trail_Making_Test)_ Part B
3. [CDR](https://en.wikipedia.org/wiki/Clinical_Dementia_Rating) : Orientation
4. [CDR](https://en.wikipedia.org/wiki/Clinical_Dementia_Rating) : Memory
5. [CDR](https://en.wikipedia.org/wiki/Clinical_Dementia_Rating) : Home & Hobbies
6. Level of independence

There isn't much explanation on those variables in the study.
From what I can guess :
1. "Clinical judgment of decline" means clinician's evaluation of how much patient's cognitive functions have declined over the years. How that's converted to numbers, I have no idea.
2. "Level of independence" means how much a patient can do (expected to do) without assistance. It might be the same as [FIM](https://www.physio-pedia.com/Functional_Independence_Measure_(FIM)), but I'm not sure. See also [ADL](https://en.wikipedia.org/wiki/Activities_of_daily_living)

## Citation

James C, Ranson JM, Everson R, Llewellyn DJ. Performance of Machine Learning Algorithms for Predicting Progression to Dementia in Memory Clinic Patients. _JAMA Netw Open._ 2021;4(12):e2136553. doi:10.1001/jamanetworkopen.2021.36553

## Source
https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2787228

# Notes
- They mention this in the _Limitations_ section of the paper; further study is required to see if this study is applicable to populations other than USA.
- I think there should be a further study in Korea to see if the clinical test methods (measuring levels of dementia and related functional abilities) are valid.
- They should really clarify how "clinical judgment of decline" is translated, and normalized.
- Are there NACC data in Korea?
- Why did a group of researchers in UK use data from USA?
- Could there have been any other variables that they could've checked? Like, other illness and conditions? Diet?
- If there are 6 variables that indicate dementia, then can it mean that a treatment that affects those 6 variables can be most effective?

## References
- [Korean News Article](http://www.aitimes.kr/news/articleView.html?idxno=23664)
- [CDR explanation in Korean](https://www.dementianews.co.kr/news/articleView.html?idxno=3289)
- [Trail Making Test explanation in Korean](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=ls_slp&logNo=221704833213)