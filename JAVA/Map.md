###  HashMap 과 HashTable - 순서 X, 중복(키 X, 값 O)
- Map 인터페이스를 구현, 데이터를 키와 값의 쌍으로 저장
- HashMap(동기화 X)은 HashTable(동기화 O)의 신버전
- HashMap
  - Map 인터페이스를 구현한 대표적인 컬렉션 클래스
  - 순서를 유지하려면, LinkedHashMap클래스를 사용하면 된다.
- TreeMap
  - 범위 검색과 정렬에 유리한 컬렉션 클래스
  - HashMap보다 데이터 추가, 삭제에 시간이 더 걸림

### HashMap의 키와 값
- 해싱기법으로 데이터를 저장. 데이터가 많아도 검색이 빠르다.
- Map 인터페이스를 구현. 데이터를 키와 값의 쌍으로 저장

### HashMap 주요 메서드
- 생성자
  - HashMap()
  - HashMap(int initialCapacity)
  - HashMap(int initialCapacity, float loadFactor)
  - HashMap(Map m)
- 저장
  - Object put(Object key, Object value)
  - void putAll(Map m)
- 삭제
  - Object remove(Object key)
- 변경
  - Object replace(Object key, Object value)
  - boolean replace(Object key, Object oldValue, Object newValue)
- 기타
  - Set entrySet()
  - Set keySet()
  - Collection values()
  - Object get(Object key)
  - Object getOrDefault(Object key, Object defaultValue)
  - boolean containsKey(Object key)
  - boolean containsValue(Object value)
  - int size()
  - boolean isEmpty()
  - void clear()
  - Object clone()