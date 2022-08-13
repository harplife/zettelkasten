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

## 강의2
2022/08/13 토요일 (10:00~18:00) SBA 아카데미 빌딩에서 진행함.
- 빅데이터 처리 시스템에 대한 개념을 다시 정리
- Hadoop, Yarn, MapReduce, Zookeeper 등이 무엇인지 간단하게 알아봄

# 빅데이터

- [데이터 레이크(Data Lake)](https://en.wikipedia.org/wiki/Data_lake) : a system or repository of data stored in its natural/raw format, usually object blobs or files
- [데이터 웨어하우스(Data Warehouse)](https://en.wikipedia.org/wiki/Data_warehouse) : central repositories of integrated data from one or more disparate sources. They store current and historical data in one single place that are used for creating analytical reports for workers throughout the enterprise.

## Big Data Pipeline
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


1. 수집
2. 정제
3. 적재
4. 분석
5. 시각화

## 데이터 처리의 요소
1. 하둡
2. 스파크
3. NoSQL

1. Scalable
2. Fault Tolerant
3. Variety


## 데이터 수집 기술
- Flume
- Kafka
- Sqoop
- Nifi
- Flink
- Splunk
- Logstash
- Fluentd

## 데이터 정제 단계
1. Identification
2. Filtration
3. Validation
4. Noise Reduction
5. Transformation
6. Compression
7. Integration

## 하둡
![[Hadoop_logo.svg]]

### Hadoop Stack
![[hadoop_stack_0.png]]

### HDFS
HDFS (Hadoop Distributed File System) : 하둡 플랫폼의 파일 분산 관리 시스템
- 대용량의 데이터를 여러 노드(컴퓨터)에 나누어 분산적으로 처리함
- 확장성 (Scalable)
- 결함 허용 (Fault Tolerant)
- 기본 운영 체계 파일 시스템 위에 탑재됨
- 작은 파일보단 대용량 파일에 최적화됨 (100MB 이상) : 옵션이긴 하지만, 블록 사이즈 128 MB가 de facto standard 임
- Write Once 방식으로 동작함 - 각 데이터가 IMMUTABLE 함
- NameNode : 각 데이터 블록이 어느 파일이 일부이며 어느 위치에 저장되는지 등 관리하는 Master
- DataNode : 데이터를 저장하는 블록, Slave/Worker로 본다
- [edit log 와 fsimage](https://eyeballs.tistory.com/255)
- OLAP 에 최적화된 구조 - [OLAP vs. OLTP](https://jins-dev.tistory.com/entry/%EA%B0%84%EB%9E%B5%ED%95%98%EA%B2%8C-%EC%A0%95%EB%A6%AC%ED%95%B4%EB%B3%B4%EB%8A%94-OLTP-OLAP-%EC%9D%98-%EA%B0%9C%EB%85%90)
- 각 블록은 중복 저장됨 (기본 3개)
- NameNode는 2개 정도 사용 (좋은 사양의 컴퓨터를 사용)

분산된 자료를 병렬적으로 처리하는 시스템이 Yarn과 MapReduce 임.

#### HDFS 구조
![[hdfsarchitecture.png]]

#### 인터페이스

- CLI interface
- [HUE (Hadoop User Experience)](https://gethue.com/)
    - https://docs.cloudera.com/documentation/enterprise/6/6.3/topics/hue.html
- NameNode Web UI

#### 참고자료
1. https://www.ibm.com/topics/hdfs
2. https://www.techtarget.com/searchdatamanagement/definition/Hadoop-Distributed-File-System-HDFS
3. https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html
4. https://docs.cloudera.com/runtime/7.2.10/hdfs-overview/topics/hdfs-introduction-hdfs.html


### 하둡 실습

1. 다른 구글 계정으로 로그인 - bd.multi.lab01 // global0810! // 복구계정 bd.multi.master@gmail.com
2. 구글 리모트 데스크탑으로 접속 - 핀 번호 220810
3. 로그인 student // student
4. 터미널 열어서
    1. mkdir work // cd work
    2. cp ~/Data/alice_in_wonderland.txt .
    3. ~/Scripts/start_all_services.sh
5. [[hdfs_hands_on_lab1.pdf]] 가이드를 따라서 실습 진행 (5.6.3 전까지만)

## 참고자료
- [빅데이터 - 하둡, 하이브로 시작하기](https://wikidocs.net/book/2203)
- [쿠팡 데이터 플랫폼의 진화](https://medium.com/coupang-engineering/%EC%BF%A0%ED%8C%A1-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%94%8C%EB%9E%AB%ED%8F%BC%EC%9D%98-%EC%A7%84%ED%99%94-26c827c1ec09)