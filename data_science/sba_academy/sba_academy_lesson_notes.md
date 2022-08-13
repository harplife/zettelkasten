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

강사진
- [정진석 강사](https://www.linkedin.com/in/jinseok-jeong-a589341b/)
- [박현우 강사](https://www.linkedin.com/in/henrypark)

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

## Hadoop
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

#### HDFS 폴더 및 파일 조회
명령어 : `hdfs dfs -ls /경로`

`hdfs dfs -ls /` 실행 시 `tmp`와 `user` 정보가 나옴.
1. `tmp`는 모든 유저가 사용할 수 있는 경로
2. `user`는 현재 접속된 유저가 사용할 수 있는 경로

![[hadoop_ls_command_results.png]]

#### HDFS 폴더 생성
명령어 : `hdfs dfs -mkdir 폴더명`

`hdfs dfs -mkdir MRtest` 실행 시
1. `user/student/` 경로 안에 `MRtest`라는 폴더가 생김

![[hadoop_mkdir_command_result.png]]

#### HDFS 파일 업로드
명령어 : `hdfs dfs -put 파일명 경로`

밑에 명령어 실행 시,
```bash
hdfs dfs -put \
/home/student/Data/alice_in_wonderland.txt \
/user/student/MRtest
```
1. `MRtest` 경로 안에 `alice_in_wonderland.txt` 파일이 저장됨

#### HDFS 파일 제거
명령어 : `hdfs dfs -rm 경로/파일명`

3개 파일들을 생성하고 HDFS에 업로드 해줌.

`hdfs dfs -rm /user/student/MRtest/testfile1` 실행 시,
1. 해당 파일이 제거됨.

![[hadoop_rm_command_result_0.png]]

`hdfs dfs -rm -skipTrash 경로/파일명` 실행 시 완전 삭제됨.
#todo 그럼 완전 삭제 안 하면 유지되는 기간 또는 한계 사이즈는??

`hdfs dfs -rm -r 경로` 실행 시 폴더와 안에 있는 파일 모두 삭제됨 (`rmdir`도 됨).

`hdfs dfs -expunge` 실행 시 임시 삭제된 파일 모두 제거됨.

#### HDFS NameNode Web UI
`localhost:50070`으로 접속하여 HDFS를 모니터링 할 수 있다.



## YARN
YARN (Yet Another Resource Negotiator) is a platform for managing resources in a Hadoop cluster.

수행할 프로그램을 받아 자원을 할당하고, 실행시키고, 결과를 로그하는 시스템.

YARN을 통해 실행할 수 있는 프로그램/기능 :
- MapReduce
- Spark (분산 메모리 처리 시스템)
- Fez

### Daemons
- Resource Manager (RM) per cluster
- Node Manager (NM) per node
- Application Master (AM) per application

## MapReduce
MapReduce is a programming model
- Record oriented data processing (Key and Value)
- 병렬 분산 처리 방식

### MapReduce 프로세스
1. Mapper
    - HDFS 블록으로 나누어 분산 처리
    - 가능한 데이터를 가지고 있는 노드에서 Task 실행
    - 수행 결과는 임시파일에 저장
2. Shuffle and Sort
    - Mapper의 중간 결과를 통합하고 정렬해서 Reducer에게 전달
3. Reducer
    - Mapper 중간 결과로 최종 결과를 조합하여 저장


## Sqoop
[Apache Sqoop](https://attic.apache.org/projects/sqoop.html)

DB에서 데이터를 가져와서 Hadoop 에 저장하는 작업을 하는 데이터 수집 시스템

### File Types
- [Hive tables](https://en.wikipedia.org/wiki/Apache_Hive)
- [Avro](https://en.wikipedia.org/wiki/Apache_Avro) / [Parquet (Apala)](https://en.wikipedia.org/wiki/Apache_Parquet) / Text / [ORC (Hive)](https://en.wikipedia.org/wiki/Apache_ORC)
- [HBase tables](https://en.wikipedia.org/wiki/Apache_HBase)
- [Accumulo tables](https://en.wikipedia.org/wiki/Apache_Accumulo)

### Connector
JDBC 사용

### 명령 예시
1. 데이터베이스 목록 조회 : `sqoop list-databases`
2. 데이터베이스에 테이블 목록 조회 : `sqoop list-tables`
3. 데이터베이스의 모든 테이블 import : `sqoop import-all-tables`
4. 데이터베이스에 특정 테이블 import : `sqoop import --table 테이블명`

파라미터:
- `--connect jdbc:mysql://호스트주소/데이터베이스명`
- `--username 유저명`
- `--password 비밀번호`
- `--table 테이블명`

Default 옵션:
- `import` 수행 시 HDFS의 Home 경로에 저장됨
- 테이블명과 동일한 폴더가 생성됨
- 테이블 데이터는 Plain Text로 쉼표(`,`)로 delimit되어 저장됨

### Sqoop 실습
[[sba_ingest_lab_1.pdf]] 가이드에서 Lab 1 세션을 진행해봄.

1. 미리 설치된 MySQL 에 접속해보고 `show databases;`로 데이터베이스들 확인
    ![[sba_mysql_show_databases_result.png]]
2. `show tables;`로 테이블들 확인
3. `desc 테이블명;`로 테이블 정보 확인
    ![[sba_mysql_desc_tables_result.png]]
4. `show * from authors;`
    ![[sba_mysql_select_authors_result.png]]
5. `sqoop help`로 도움말 확인
6. `sqoop help import`로 import 명령어에 대한 도움말 확인
7. `sqoop list-databases --connect jdbc:mysql://localhost --username student --password student`로 데이터베이스 목록 조회
8. `sqoop list-tables --connect jdbc:mysql://localhost/labs --username student -P`로 테이블 목록 조회 (`-P`는 비밀번호 넣는 prompt를 뜨게함).
9. `sqoop import-all-tables --connect jdbc:mysql://localhost/labs --username student --password student`는 모든 테이블들을 import 해줌.



## Flume
[Apache Flume](https://flume.apache.org/)

Source, Channel, Sink로 데이터를 전달하는 에이전트, 여러 에이전트를 관리하는 데이터 수집 시스템

Conveyer 벨트 방식으로 처리하는 시스템

Tightly-Coupled Data Transfer

## Nifi
[Apache Nifi](https://nifi.apache.org/)

Flume과 비슷하되, Flume에서 제공하는 기능을 좀 더 간단한 인터페이스(Codeless)를 제공한다.

## Kafka
[Apache Kafka](https://kafka.apache.org/)

Producer / Consumer 방식으로 .. 하는 데이터 수집 시스템

Kafka만 잘하면 데이터 수집의 80%는 처리할 수 있다고 할 수 있다?

Broker / Topic 개념으로 데이터를 저장하고, 데이터가 사용될 때 까지 유지.

## 참고자료
- [빅데이터 - 하둡, 하이브로 시작하기](https://wikidocs.net/book/2203)
- [쿠팡 데이터 플랫폼의 진화](https://medium.com/coupang-engineering/%EC%BF%A0%ED%8C%A1-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%94%8C%EB%9E%AB%ED%8F%BC%EC%9D%98-%EC%A7%84%ED%99%94-26c827c1ec09)