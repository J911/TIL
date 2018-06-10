# 해시테이블

Key Value로 구성된 데이터를 저장하는 자료구조

## 구현
### 정의
- Node : key, value, nextNode로 구성된 객체
```
    Node { 
        key,
        value,
        nextNode(default: null)
    }
```
- HashTable : Node를 담는 배열과 hashKey로 구성된 객체
```
    HashTable {
        table, (default_value: null)
        hashKey (value: table_length)
    }
``` 
### 알고리즘
1. HashTable에 새로운 노드 추가
    - Node의 key % hashKey번째 인덱스가 null인 경우
        해당 인덱스에 Node 추가
    - Node의 key % hashKey번째 인덱스가 null이 아닌 경우
        1. 추가할 노드의 nextNode값을 해당 인덱스 노드로 변경
        2. 추가할 노드를 해당 인덱스로 변경
2. HashTable에서 노드 검색
    - Node의 key % hashKey번째 인덱스가 검색 값인경우
        - 해당 노드 반환
    - Node의 key % hashKey번째 인덱스가 검색 값이 아닌 경우
        1. 해당 노드의 nextNode값을 순차적으로 탐색
        2. 탐색 완료시 노드 반환
3. HashTable에서 노드 삭제
    - 해당 노드의 이전 노드가 존재할 경우
        - 이전 해시의 값의 nextNode노드를 해당 노드의 nextNode 값으로 설정
    - 해당 노드의 이전 노드가 존재하지 않을 경우 
        - 해당 노드를 null로 변경

## 구현 소스코드
[https://github.com/J911/algorism/tree/master/HashTable](https://github.com/J911/algorism/tree/master/HashTable)


## 레퍼런스
- 쉽게 배우는 알고리즘(한빛미디어)