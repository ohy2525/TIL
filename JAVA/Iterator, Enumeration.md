### Iterator, ListIterator, Enumeration
컬렉션에 저장된 데이터를 접근하는데 사용되는 인터페이스

Enumeration 은 Iterator의 구버전

- boolean hasNext() : 읽어 올 요소가 남아있는지 확인한다. 있으면 true, 없으면 false를 반환한다.
- Object next() : 다음 요소를 읽어 온다. next()를 호출하기 전에 hasNext()를 호출해서 읽어 올 요소가 있는지 확인하는 것이 안전하다.

### 사용
- 컬렉션에 저장된 요소들을 읽어오는 방법을 표준화한 것
- 컬렉션에 iteration()를 호출해서 Iterator를 구현한 객체를 얻어서 사용
```java
List list = new ArrayList();
Iterator it = list.iterator();

while (it.hasNext()) {
    System.out.println(it.next());
}
```

### Map과 Iterator
- Map에는 iterator()가 없다.
- Map은 컬렉션의 자손이 아니기 때문
- keySet(), entrySet(), values()를 호출
```java
Map map = new HashMap();

Iteration it = map.entrySet().iterator();
```