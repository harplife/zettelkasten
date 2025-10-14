# OSM 기반 절차적 도시 생성
OSM (OpenStreetMap) 데이터를 Houdini 로 가져와서 건물, 도로 등을 절차적(Procedural)으로 생성한 후 언리얼 엔진으로 불러와 렌더링 하는 방식으로 프로젝트 진행.

## 건물 생성

### 이슈
#### Same Building + No Overlap + No Connect
하나의 건물인데 건물 파트가 여러 개로 나뉘며 + 겹치는 부분이 없고 + 연결된 부분도 없이 떨어져 있음.

![[Pasted image 20230706104458.png]]

##### 해결 방안
서로 다른 Primitive 를 기준으로 Point 들에 Fuse 를 적용;
한번에 처리 되지 않음으로,
1. 작은 수치로 Fuse 적용 후 Fuse 된 포인트에 "Snapped" 그룹이 생성되도록 설정
2. Snapped 그룹이 먹힌 Point 를 가진 Primitive 에 Snapped 그룹/속성 적용
3. Snapped 를 가진 Primitive 를 기준으로 조금 더 큰 수치의 Fuse 적용
4. 

### Same Building + Overlap + No Connection
하나의 건물인데 건물 파트가 여러 개로 나뉘며 + 큰 파트 안에 작은 파트가 있는 방식으로 겹치고 + 연결 지점이 없음.