---
aliases: [SBA 빅데이터 강의]
tags: [lessons, study, big_data, data_science, hadoop]
status: ongoing
created: 2022-08-13
edited: 2022-08-13
---

# SBA 빅데이터 강의
2022년 재직자 DT스쿨
중소/스타트업을 위한 **빅데이터 처리 시스템구축 및 기술 실무**

2022/08/10 ~ 2022/09/03

무료 강의

수요일 온라인 강의, 토요일 오프라인 강의

## 강의 1
2022/08/10 수요일 (7:30~10:30) Zoom으로 첫 강의 진행함.
- 빅데이터 처리 시스템에 대한 개념을 배움
- Hadoop, Zookeeper 등이 무엇인지 간단하게 알아봄
- [데이터 레이크(Data Lake)](https://en.wikipedia.org/wiki/Data_lake) : a system or repository of data stored in its natural/raw format, usually object blobs or files
- [데이터 웨어하우스(Data Warehouse)](https://en.wikipedia.org/wiki/Data_warehouse) : central repositories of integrated data from one or more disparate sources. They store current and historical data in one single place that are used for creating analytical reports for workers throughout the enterprise.


### Big Data Pipieline
1. Collect
    - Streaming & Data Flow
2. Curate
    - Data Engineering
3. Report
    - Data Warehouse
4. Serve
    - Operational Database
5. Predict
    - Artificial Intelligence

### 하둡
![[Hadoop_logo.svg]]

참고자료
1. [빅데이터 - 하둡, 하이브로 시작하기](https://wikidocs.net/book/2203)

### Hadoop Stack
![[hadoop_stack_0.png]]

### Data Processing
1. 하둡
2. 스파크
3. NoSQL

1. Scalable
2. Fault Tolerant
3. Variance

### HDFS
HDFS (Hadoop Distributed File System) : 하둡 플랫폼의 파일 분산 관리 시스템
- 대용량의 데이터를 여러 노드(컴퓨터)에 나누어 분산적으로 처리함
- 확장성 (Scalable)
- 결함 허용 (Fault Tolerant)
- 기본 운영 체계 파일 시스템 위에 탑재됨
- 작은 파일보단 대용량 파일에 최적화됨 (100MB 이상)
- Write Once 방식으로 동작함 - 각 데이터가 IMMUTABLE 함
- NameNode : 각 데이터 블록이 어느 파일이 일부이며 어느 위치에 저장되는지 등 관리하는 Master
- DataNode : 데이터를 저장하는 블록, Slave/Worker로 본다
- [edit log 와 fsimage](https://eyeballs.tistory.com/255)
- OLAP 에 최적화된 구조 - [OLAP vs. OLTP](https://jins-dev.tistory.com/entry/%EA%B0%84%EB%9E%B5%ED%95%98%EA%B2%8C-%EC%A0%95%EB%A6%AC%ED%95%B4%EB%B3%B4%EB%8A%94-OLTP-OLAP-%EC%9D%98-%EA%B0%9C%EB%85%90)

분산된 자료를 병렬적으로 처리하는 시스템이 Yarn과 MapReduce 임.


참고자료
1. https://www.ibm.com/topics/hdfs
2. https://www.techtarget.com/searchdatamanagement/definition/Hadoop-Distributed-File-System-HDFS
3. https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html

## 강의2
2022/08/13 토요일 (10:00~18:00) SBA 아카데미 빌딩에서 진행함.
