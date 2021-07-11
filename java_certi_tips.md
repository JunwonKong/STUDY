# Certi tips

## null pointer 사용
- certi 시험장에서는 null pointer 를 사용못하게 되어 있다. ( stdio.h include 를 못하기 때문에)
- 따라서 아래와 같이 재정의 해서 사용하면 된다.
```c
#ifndef  NULL
#define NULL 0
#endif
```

## single linked list vs double linked list 
- single linked list 는 삭제를 고려하지 않은 사항임.
- 따라서 실제 삭제를 해야 할 필요성이 있다면, dummy tail 방식을 쓰거나 , double linked list 를 구현하는것이 좋다.
- 실제 구현상으로는 dummy tail 방식이 좀더 구현하기 쉽다. (NODE 에 avail 같은 필드를 두고 true false 를 두거나 v 값은 -1 로 두어서 해당 NODE 가 삭제된 노드임을 명시)
- single 이냐 double 이냐에서 성능상의 문제는 없고 메모리는 약간 증가하긴 하겠지만, 서티에서는 큰 영향은 없다.
- 다만 구현상의 복잡도가 증가 할 뿐이다.

## hash 를 만들때 데이터의 충돌이 많을것 같다면 더블 해시 테이블을 만드는것도 좋다.
- 사전과 같이 빠른 검색을 할때도 유용할것 같긴 함. (첫번째 문자 와 두번째 문자까지 해싱키로 두면 좀더 검색이 빠르지 않을까 싶긴 함
```
NODE *hashtable[10][10]
```

## linked list 를 만들때 맨 마지막 노드를 현재 지점으로 가리키고 있는것도 좋다. (순회할때는 prev 가  NULL 일때까지 돈다)

## graph를 구현할때, 배열을 사용하는 방법과 single linked list 를 사용하는 방법 두가지가 있다.
- 2차원 배열 사용
- y축은 from x 축은 to 로 생각하면 된다. 만약에 간선에 가중치가 있으면 1 대신 가중치 값을 넣어주면 된다.

    |  |0 |1 |2 |3 |
    |--|--|--|--|--|
    | 0|  |  |1 |  |
    | 1|  |1 |1 |1 |
    | 2|  |  |  |1 |
    | 3|  |  |  |  |

- single linked list 를 사용
- 0: 2
- 1: 1 -> 2 -> 3
- 2: 3
- 3: null 
- from 은 1차원 배열로 설정하고 각 노드에서 나가는 노드를 single linked list 로 구현하면 된다.
- 간선의 가중치가 있다면, NODE 의 v 변수를 하나두고 가중치로 사용하면 된다.

## double linked list 구현
- double linked list 를 구현할때, head 와 tail 을 먼저 잡아놓고, 노드가 추가 될때, head 와 tail 사이에 끼워 넣는 방식으로 하면 좀더 구현이 쉽다.
- 구현적으로 설명하자면, tail 앞에 넣는거라고 생각하면 쉽다.

## hash table 을 생성할때, 10억개 정도의 데이터를 hash table에 정리해야 할때 hashkey 는 110007 정도로 잡는다.
- 잡았을때 입력수 % hash key 를 써서 hash table 을 생성한다.
- hash key 가 감당할 수 없을정도로 큰 경우에는 openaddressing 을 할 수 없다. 따라서 적절한 크기의 hash table 에 chaining 을 써야 한다.

### hash 를 사용해야 할때.
- Solution class 안에 class NODE(info), genHashKey, get, add 메소드 3개만 생성한다.
(find key 이딴거 없음)
- 외부에서 객체를 사용하고자 할땐, get 의 반환값은 NODE 타입 add 의 파라미터는 NODE 로 객체를 아예 생성해서 던져 준다.
- ADD 의 반환값은 필요 없다.

### TOP N 을 뽑을때, naive 하게 하려면 아래와 같이 하면 된다.
```java
for(int i = 0; i < "뽑을 TOP 갯수" ; i++){
        for(int j = i; j < "전체 리스트 수"; j++){
                if (array[i]>array[j]) swap;
        }
}
```