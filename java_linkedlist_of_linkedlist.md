# java linkedlist of linkedlist

### 생성
```java
LinkedList<LinkedList<YourClass>> list = new LinkedList<LinkedList<YourClass>>();
```
또는
``` java
LinkedList<LinkedList<YourClass>> list = new LinkedList<>();
```

### 첫 리스트의 element 를 linked list 로 생성
```java
list.add(new LinkedList<YourClass>());
```

### linkedlist 의 첫 요소를 추가
```java
list.get(sublistIndex).add(new YourClass());
```

### iteration
```java
for(LinkedList<YourClass> sublist : list) {
    for(YourClass o : sublist) {
        // your code here
    }
}
```
