## Arrays 
배열을 다루기 편리한 메서드(static) 제공

- 배열의 출력
  - toString()

- 배열의 복사
  - copyOf()
  - copyOfRange()

- 배열 채우기
  - fill()
  - setAll()
- 배열의 정렬과 검색
  - sort()
  - binarySearch()
  - 정렬후 이진탐색
- 다차원 배열의 출력
  - deppToString()
- 다차원 배열의 비교
  - deepEquals()
- 배열을 List로 변환
  - asList(Object ...(배열) a )
- 람다와 스트림 관련
  - parallelXXX()
  - spliterator()
  - stream()

## Copartor와 Comparable
객체 정렬에 필요한 메서드(정렬기준 제공)를 정의한 인터페이스
- Comparable : 기본 정렬기준을 구현하는데 사용
- Comparator : 기본 정렬기준 외에 다른 기준으로 정렬하고자할 때 사용

```java
public interface Comparator {
    int compare(Object o1, Object o2);  // o1, o2 두 객체를 비교
    boolean equals(Object obj);    // equals를 오버라이딩
}

public interface Comparable {
    int compareTo(Object o);       // 주어진 객체(o)를 자신과 비교
}
```
- compare()와 compareTo()는 두 객체의 비교결과를 반환하도록 작성
- 같으면 0, 오른쪽이 크면 음수, 작으면 양수