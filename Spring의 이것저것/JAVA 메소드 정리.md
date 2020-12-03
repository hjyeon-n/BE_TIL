# JAVA 메소드 정리

| 바로가기 😎                  |
| --------------------------- |
| [Arrays](#Arrays)           |
| [Collection](#Collection)   |
| [Collections](#Collections) |
| [List](#List)               |
| [Map](#Map)                 |

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
```

```
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
```

```java
// 출력
5 26 1 74 59 38
```

<br>

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

<br>

### #Collections

- sort : 오름차순으로 정렬

```java
Integer[] arr = {5, 26, 1, 74, 59, 38};
ArrayList<Integer> list = new ArrayList<Integer>(Arrays.asList(arr));

Collections.sort(list);
        
for (int i : list) {
    System.out.print(i + " ");
}
```

```java
// 출력
1 5 26 38 59 74
```



- max / min : 컬렉션 내의 최댓값 / 최솟값 반환

```java
System.out.println(Collections.max(list));
System.out.println(Collections.min(list));
```

```java
// 출력
74
1
```

<br>

### #List

- add : 리스트 끝에 원소 추가

```java
// List 인터페이스를 구현한 ArrayList를 사용
ArrayList<String> list = new ArrayList<String>();

list.add("one");
list.add("two");
list.add("three");
      
for (String str : list) {
			System.out.print(str + " ");
}
```

```java
// 출력
one two three
```



- get :  특정 인덱스 값 조회

```java
System.out.println(list.get(2));
```

```java
// 출력
three
```



- remove : 특정 값 삭제

  ✅ remove(int index) : 인덱스에 위치하는 값 삭제

  ✅ remove(Object o) : 특정 객체 삭제

```java
// 같은 일을 하는 코드 -> 아래의 코드 중 하나만 실행해야 함
list.remove("three");
list.remove(2);
```

```java
// 출력
one two
```



- contains : 특정 원소가 리스트 내에 있는지 판별

```java
System.out.println(list.contains("one"));
System.out.println(list.contains("three"));
```

```java
// 출력
true
false
```



- size : 리스트 크기 반환

```java
System.out.println(list.size());
```

```java
// 출력
2
```

<br>

### Map

- put : Map에 key와 value 값 삽입

```java
// Map 인터페이스를 구현한 HashMap 사용
HashMap<Integer, String> map = new HashMap<Integer, String>(); 

map.put(1, "one");
map.put(2, "two");
map.put(3, "three");
```



- get : key와 매핑된 value 반환. 만약, key 값이 없을 땐 null을 반환

```java
System.out.println(map.get(1));
System.out.println(map.get(5));
```

```java
// 출력
one
null
```



- containsKey :  특정 key가 map에 있는지 판별

```java
System.out.println(map.containsKey(1));
System.out.println(map.containsKey(5));
```

```java
// 출력
true
false
```



- containsValue : 특정 value가 map에 있는지 판별

```java
System.out.println(map.containsValue("one"));
System.out.println(map.containsValue("five"));
```

```java
// 출력
true
false
```



- remove : 특정 key에 해당하는 값을 삭제

```java
map.remove(1);

// map의 값 출력
for(int key : map.keySet()){
    String value = map.get(key);
    System.out.println(key + " : " + value);
}
```

```java
// 출력
2 : two
3 : three
```

<br>

### Map

- put : Map에 key와 value 값 삽입

```java
// Map 인터페이스를 구현한 HashMap 사용
HashMap<Integer, String> map = new HashMap<Integer, String>(); 

map.put(1, "one");
map.put(2, "two");
map.put(3, "three");
```



- get : key와 매핑된 value 반환. 만약, key 값이 없을 땐 null을 반환

```java
System.out.println(map.get(1));
System.out.println(map.get(5));
```

```java
// 출력
one
null
```



- containsKey :  특정 key가 map에 있는지 판별

```java
System.out.println(map.containsKey(1));
System.out.println(map.containsKey(5));
```

```java
// 출력
true
false
```



- containsValue : 특정 value가 map에 있는지 판별

```java
System.out.println(map.containsValue("one"));
System.out.println(map.containsValue("five"));
```

```java
// 출력
true
false
```



- remove : 특정 key에 해당하는 값을 삭제

```java
map.remove(1);

// map의 값 출력
for(int key : map.keySet()){
    String value = map.get(key);
    System.out.println(key + " : " + value);
}
```

```java
// 출력
2 : two
3 : three
```

<br>

### Set

- add : Set에 요소 추가

```java
// Set 인터페이스를 구현한 HashSet 사용
HashSet<String> set = new HashSet<String>();

set.add("one");
set.add("two");
set.add("three");
set.add("two");

Iterator<String> iter = set.iterator();
while(iter.hasNext()) {
			System.out.println(iter.next());
}
```

```java
// 출력
one
two
three
```



- containsAll : 한 Set에 있는 원소들이 다른 Set에 전부 포함되는지 확인. 즉, 부분집합인지 판별.

```java
// setA : 2, 5, 9, 12
// setB : 3, 6, 9, 12
System.out.println(setA.containsAll(setB));
```

```java
// 출력
false
```



- addAll : 한 Set에 있는 원소들과 다른 Set 원소들을 합침. 즉, 합집합을 의미함.

```java
// setA : 2, 5, 9, 12
// setB : 3, 6, 9, 12

setA.addAll(setB);
System.out.println(setA.toString());
```

```java
// 출력
[12, 2, 3, 5, 6, 9]
```



- removeAll : 다른 Set에 포함된 공통적인 원소를 제거. 즉, 차집합을 의미함.

```java
// setA : 2, 5, 9, 12
// setB : 3, 6, 9, 12

setA.removeAll(setB);
System.out.println(setA.toString());
```

```java
// 출력
[2, 5]
```



- retainAll : 다른 Set에 포함된 공통적인 원소들만 포함. 즉, 교집합을 의미함.

```java
// setA : 2, 5, 9, 12
// setB : 3, 6, 9, 12

setA.retainAll(setB);
System.out.println(setA.toString());
```

```java
// 출력
[12, 9]
```

<br>

## Stack

- push : 스택의 top에 값을 삽입

```java
Stack<String> stack = new Stack<String>();

stack.push("one");
stack.push("two");
stack.push("three");

System.out.println(stack.toString());
```

```java
// 출력
[one, two, three]
```



- pop : 스택의 top 값을 반환한 뒤에 삭제

```java
System.out.println(stack.pop());
System.out.println(stack.toString());
```

```java
// 출력
three
[one, two]
```



- peek : 스택의 top 값 조회

```java
// 현재 스택 값 : [one, two]
System.out.println(stack.peek());
System.out.println(stack.toString());
```

```java
// 출력
two
[one, two]
```

<br>

## Queue

- offer : 큐의 뒤에 데이터를 삽입. add도 같은 역할을 하지만, 큐의 크기가 꽉 찼을 경우에 add는 예외를 발생시키지만 offer는 false를 반환.

```java
Queue<String> queue = new LinkedList<String>();

queue.offer("one");
queue.offer("two");
queue.offer("three");

System.out.println(queue.toString());
```

```java
// 출력
[one, two, three]
```



- poll : 큐의 맨 앞에 위치한 값을 반환한 뒤에 삭제

```java
System.out.println(queue.poll());
System.out.println(queue.toString());
```

```java
// 출력
one
[two, three]
```



- peek : 큐의 맨 앞에 위치한 값을 반환

```java
System.out.println(queue.peek());
System.out.println(queue.toString());
```

```java
// 출력
two
[two, three]
```

