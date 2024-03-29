

분산저장(HDFS), 분산처리(MapReduce)

RDBMS : 스키마, 관계

NoSQL : 확장성, 유연성, 고성능



SQL은 데이터가 자주 변경되는 어플리케이션(계좌내역), NoSQL은 정확한 데이터 구조를 알 수 없거나 유연하게 데이터를 저장할 경우



분산저장 : 네임노드/데이터노드

병렬처리 : 잡트래커/태스크트래커



하둡2 등장배경

하둡 클러스터에서 적절한 리소스 관리의 부재 -> YARN

고정된 맵/리듀스 슬롯 사용, 다른 시스템과 자원 공유 불가로 비효율적



네임노드의 SPOF 문제 -> 네임노드HA

잡트래커의 단일고장점, 문제가 발생하면 맵리듀스 실행이 불가능

잡트래커는 메모리 상에 실행정보를 유지하므로 메모리 제약 있음

잡트래커의 병목현상을 제거하기 위함이었음, 자원관리 기능과 작업관리 역할을 나눔

**YARN** 에서는 리소스 매니저, 애플리케이션 마스터 사용



단일 네임스페이스의 문제 ->HDFS Federation





ETL : Extract, Transform, Load



DDL : CREATE, ALTER, DROP, TRUNCATE

DML : SELECT, INSERT, UPDATE, DELETE (CRUD)

DCL : grant, revoke

TCL : commit, rollback

트랜잭션 : 하나의 그룹으로 처리되어야 하는 명령문들, 모두 정상적으로 처리되어야 db에 반영하고, 그렇지 않으면 전체 취소한다.



조건을 줄 때 where

그룹으로 묶은 후 조건을 줄 때는 having

DISTINCT와 GROUP BY는 거의 같은 동작이지만, GROUP BY는 정렬도 해줌



hiveQL에서 테이블 별칭 AS 안쓰고 그냥씀

order by : 전체정렬

sort by : 여러 개의 리듀서 실행, 각 리듀서 정렬

각 리듀서가 같은 키만 받는 것을 보장 x, 출력 결과에 동일한 키가 생성될 수 있음

distribute by : 같은 키를 가진 레코드가 같은 리듀서로 보내지는 것을 보장, 일반적으로 sort by와 같이 사용

cluster by : distribute by + cluster by



UNION UNION ALL의 차이 : UNION ALL은 중복제거x, 속도가 더 빠르다



SQL on Hadoop의 fault tolerance : 중간 결과를 수시로 저장하여 문제가 발생했을 경우 이를 참조, 하드디스크 사용하므로 속도 저하

dynamic scheduling : 각 노드에서 한번에 실행할 수 있는 태스크를 할당받고, 그것이 완료되면 다시 태스크를 받음

in-memory : 빠르지만, out of memory 발생 여지 높음  



**spark**

대규모 데이터 처리를 위한 분석 엔진, 인메모리 기반이라 속도 빠름

RDD : Resilient Distributed Data/Dataframe/Dataset

RDD의 연산은 transformation/action으로 나뉜다. transformation은 rdd를 변형하여 새로운 rdd 반환, 액션은 rdd의 각 요소를 이용해 어떤 결과값(스칼라)을 얻어내는 연산. transformation은 실제로 action이 실행되어야 평가된다(lazy evaluatation)