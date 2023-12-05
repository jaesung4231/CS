# 데이터베이스

구조화된 정보 또는 데이터의 조직화된 모음

### 키(Key)

키(Key)는 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 Attribute(속성)이다.

  <p align="center"><img src='.\images\keys.png' align="center" width=350><p>

- **후보키(Candidate Key)**<br>
  2가지 조건을 만족해야 한다.<br>

  - **유일성:** Key로 하나의 Tuple을 유일하게 식별할 수 있음
  - **최소성:** 꼭 필요한 속성으로만 구성

- **기본키(Primary Key)**<br>
  특징: Null값을 가질 수 없음, 동일한 값이 중복될 수 없음

- **대체키(Alternate Key)**<br>
  후보키 중 기본키를 제외한 나머지 키 (보조키라고도 불림)

- **슈퍼키(Super Key)**<br>
  유일성은 만족하지만, 최소성을 만족시키지 못하는 키

- **외래키(Foreign Key)**<br>
  다른 릴레이션의 기본키를 그대로 참조하는 속성의 집합

### 인덱스(Index)

추가적인 쓰기 작업과 저장 공간을 활용하여 데이터베이스 테이블의 검색 속도를 향상시키기 위한 자료구조

  <p align="center"><img src='.\images\index.png' align="center" width=600><p>

- **장점**<br>

  - 테이블을 조회하는 속도와 그에 따른 성능을 향상시킬 수 있다.
  - 전반적인 시스템의 부하를 줄일 수 있다.

- **단점**<br>
  - 인덱스를 관리하기 위해 DB의 약 10%에 해당하는 저장공간이 필요하다.

### 인덱스 자료구조

대표적으로 B+-Tree, Hash로 이루어져 있다.

- **B-Tree**<br>

  - B는 Binary가 아닌 Balanced로, 균형이 잡힌 트리라는 의미의 자료구조이다.<br>
  - 이진 트리와는 다르게 하나의 노드에 두 개 이상의 자식을 가질 수 있다.<br>
  - 노드가 한쪽으로만 쏠리지 않도록 노드 삭제/삽입 시 재정렬하여 균형을 유지한다.

    <p align="center"><img src='.\images\b-tree.png' align="center" width=600><p>

  - **단점**<br>
    B-Tree는 어떤 한 데이터의 검색에서는 빠를 수 있으나, 모든 데이터를 순회하기 위해서는 leaf node까지 갔다가 다시 부모 node로 BackTracking하여 트리의 모든 node를 방문해야 하므로 비효율적이다.

- **B+Tree**<br>

  B-Tree 단점을 보완하고자 하는 것이 B+Tree이다.

  - 데이터는 leaf node에만 저장한다. leaf가 아닌 root node와 중간 node들은 자식 node로 향하는 포인터만 갖는다.

  - 모든 leaf node들은 연결리스트를 통해 연결되어 있다.
  - 중간 node들의 key를 통해 leaf node를 찾아가르모, node들이 갖는 key는 중복될 수 있다.

  <p align="center"><img src='.\images\b+tree.png' align="center" width=500><p>

- **Hash Table**<br>
  해시 테이블이란 해시 함수를 사용하여 변환한 값을 index로 삼아 키(key)와 데이터(value)를 저장하는 자료구조를 말한다.

  - 매우 빠른 검색 속도를 가지고 있다. 하지만 값을 변형해서 인덱싱하므로 값의 일부만으로 검색 할 때는 hash를 사용할 수 없다.

  - B tree보다 Hash가 효율적일 것 같지만, SELECT 질의의 조건에는 부등호(<>)연산도 포함이 된다. Hash에서 등호(=) 연산이 아닌 부등호 연산의 경우에 문제가 발생한다.

### 정규화

관계형 데이터 베이스에서 중복을 최소화하기 위해 데이터를 구조화하는 작업이다.

- **제1 정규형**<br>
  한 칸에는 하나의 데이터만 보관

- **제2 정규형**<br>
