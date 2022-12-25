## Set - 순서 x, 중복 x
HashSet
- Set인터페이스를 구현한 대표적인 컬렉션 클래스
- 순서를 유지하려면, LinkedHashSet 클래스를 사용하면 된다.

treeSet
- 범위 검색과 정렬에 유리한 컬렉션 클래스
- HashSet보다 데이터 추가, 삭제에 시간이 더 걸림.

### HashSet 주요 메서드
- 생성자
  - HashSet()
  - HashSet(Collection c)
  - HashSet(int initialCapacity)
  - HashSet(int initialCapacity, float loadFactor) : loadFactor 만큼 찼을 때 *2
- 추가
  - boolean add(Object o)
  - boolean addAll(Collection c)
- 삭제
  - boolean remove(Object o)
  - boolean removeAll(Collection c)
  - boolean retainAll(Collection c) : 조건부 삭제, 컬렉션만 남기고 삭제, 차집합
  - void clear()
- 기타
  - boolean contains(Object o)
  - boolean containsAll(Collection c)
  - Iterator iterator()
  - boolean isEmpty()
  - int size() : 저장된 객체 수
  - Object[] toArray() : 객체를 객체 배열로 반환
  - Object[] toArray(Object[] a)

### HashSet 예제
- HashSet은 객체를 저장하기전에 기존에 같은 객체가 있는지 확인
- 같은 객체가 없으면 저장하고, 있으면 저장하지 않는다.
- boolean add(Object o) 는 저장할 객체의 equals()와 hashCode()를 호출
- equals()와 hashCode()가 오버라이딩 되어 있어야 함
```java
class Person {
    String name;
    int age;
    
    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public String toString() {
        return name + ":" + age;
    }
}

public boolean equals(Object obj) {
    if(!(obj instanceof Person)) return false;
    
    Person tmp = (Person)obj;
    
    return name.equals(tmp.name) && age = tmp.age;
}
public int hashCode() {
    return Objects.hash(name, age);
    //return (name+age).hashCode();
}
```

### TreeSet - 범위 탐색, 정렬
- 이진 탐색 트리(binary search tree) 로 구현. 범위 탐색과 정렬에 유리
- 이진 트리는 모든 노드가 최대 2개의 하위 노드를 갖음

###  이진 탐색 트리
- 부모보다 작은 값은 왼쪽, 큰 값은 오른쪽에 저장
- 데이터가 많아질 수록 추가, 삭제에 시간이 더 걸림(비교 횟수 증가)

### TreeSet 주요 생성자와 메서드
| 생성자 또는 메서드               |설 명|
|--------------------------|----|
| TreeSet()                |기본 생성자|
| TreeSet(Collection c)    |주어진 컬렉션을 저장하는 TreeSet을 생성|
| TreeSet(Comparator comp) |주어진 정렬기준으로 정렬하는 TreeSet을 생성|
| Object first()           |정렬된 순서에서 첫 번째 객체를 반환한다.|
| Object last()            |정렬된 순서에서 마지막 객체를 반환한다.|
| Object ceiling(Object o) |지정된 객체와 같은 객체를 반환. 없으면 큰 값을 가진 객체 중 제일 가까운 값의 객체를 반환, 없으면 null|
| Object floor(Object o)   |지정된 객체와 같은 객체를 반환. 없으면 작은 값을 가진 객체 중 제일 가까운 값의 객체를 반환. 없으면 null|
| Object higher(Object o) |지정된 객체보다 큰 값을 가진 객체 중 제일 가까운 값의 객체를 반환. 없으면 null|
| Object lower(Object o) | 지정된 객체보다 작은 값을 가진 객체 중 제일 가까운 값의 객체를 반환. 없으면 null|
| SortedSet subSet(Object fromElement, Object toElement) | 범위 검색의 결과를 반환한다.(끝 범위인 toElement는 범위에 포함하지 않는다.)|
| SortedSet headSet(Object toElement)| 지정된 객체보다 작은 값의 객체들을 반환한다.|
| SortedSet tailSet(Object fromElement)| 지정된 객체보다 큰 값의 객체들을 반환한다.|
