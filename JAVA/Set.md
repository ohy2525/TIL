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