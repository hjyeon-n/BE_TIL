# JAVA 메소드 정리

| 바로가기 😎                  |
| --------------------------- |
| [Arrays](#Arrays)           |
| [Collection](#Collection)   |
| [Collections](#Collections) |

<br>

___



### #Arrays

- sort : 오름차순으로 정렬

```java
int[] arr = {5, 26, 1, 74, 59, 38};
Arrays.sort(arr);

for (int i = 0; i < arr.length; i++) {
     System.out.print(arr[i] + " ");
}
// 출력
1 5 26 38 59 74
```

- asList : 배열을 ArrayList로 변환

```java
Integer[] arr = {5, 26, 1, 74, 59, 38};
ArrayList<Integer> list = new ArrayList<Integer>(Arrays.asList(arr));

for (int i : list) {
     System.out.print(i + " ");
}
// 출력
5 26 1 74 59 38
```





### #Collection

컬렉션 계층 구조의 루트 인터페이스로, 하위 인터페이스에는 List, Map, Set 등 다양한 컬렉션들이 존재한다. Collection에 포함된 메소드는 하위 인터페이스에서도 사용이 가능하다.

```java
size() // 컬렉션의 크기 반환
equals(Object o) // 컬렉션 비교
isEmpty() // 컬렉션이 비어있는지 확인
contains(Object o) // 해당 값이 컬렉션에 있는지 확인
clear() // 컬렉션에 있는 모든 요소 제거
remove(Object o) // 컬렉션 내에서 해당 객체 삭제
removeIf(Predicate<? super E> filter) // 해당 조건에 만족하는 객체 삭제
addAll(Collection<? extends E> c) // 지정된 컬렉션의 모든 요소를 컬렉션에 추가
containsAll(Collection<?> c) // 컬렉션에 지정된 컬렉션의 모든 요소가 포함되어 있는지 여부를 반환
removeAll(Collection<?> c) // 지정된 컬렉션에 공통으로 포함된 컬렉션의 모든 요소를 제거
retainAll(Collection<?> c) // 지정된 컬렉션에 공통으로 포함된 컬렉션의 요소만 유지
```





### #Collections

- sort : 오름차순으로 정렬

```java
Integer[] arr = {5, 26, 1, 74, 59, 38};
ArrayList<Integer> list = new ArrayList<Integer>(Arrays.asList(arr));

Collections.sort(list);
        
for (int i : list) {
    System.out.print(i + " ");
}
// 출력
1 5 26 38 59 74
```

- max / min : 컬렉션 내의 최댓값 / 최솟값 반환

```java
System.out.println(Collections.max(list));
System.out.println(Collections.min(list));
// 출력
74
1
```