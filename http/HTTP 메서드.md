# HTTP 메서드
좋은 URI 설계 = **리소스 식별**

- 리소스 의미 : 회원을 등록하고 수정하고 조회하는 것이 리소스가 아니라 회원이라는 개념 자체가 리소스다. -> 회원 리소스를 URI 에 매핑
- 가장 중요한 것은 리소스를 식별하는 것
- 행위는 메서드를 통해 구분

## HTTP 메서드 종류
- GET: 리소스 조회
- POST: 요청 데이터 처리, 주로 등록에 사용
- PUT: 리소스를 대체, 해당 리소스가 없으면 생성
- PATCH: 리소스 부분 변경
- DELETE: 리소스 삭제
- 기타 메서드
  - HEAD: GET과 동일하지만 메시지 부분을 제외하고, 상태 줄과 헤더만 반환
  - OPTIONS: 대상 리소스에 대한 통신 가능 옵션(메서드)을 설명 (주로 CORS 에서 사용)
  - CONNECT: 대상 자원으로 식별되는 서버에 대한 터널을 설정
  - TRACE: 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트를 수행

## GET
- 리소스 조회
- 서버에 전달하고 싶은 데이터는 query(쿼리 파라미터, 쿼리 스트링)를 통해서 전달
- 메시지 바디를 사용해서 데이터를 전달할 수 있지만, 지원하지 않는 곳이 많아서 권장하지 않음

## POST
- 요청 데이터 처리
- 메시지 바디를 통해 서버로 요청 데이터 전달
- 서버는 요청 데이터를 처리
  - 메시지 바디를 통해 들어온 데이터를 처리하는 모든 기능을 수행한다.
- 주로 전달된 데이터로 신규 리소스 등록, 프로세스 처리에 사용
- 다른 메서드로 처리하기 애매한 경우
  - ex) JSON 으로 조회 데이터를 넘겨야 하는데, GET 메서드를 사용하기 어려운 경우
  - 애매하면 POST

## PUT
- 리소스를 대채
  - 리소스가 있으면 대체
  - 리소스가 없으면 생성
  - 쉽게 이야기해서 덮어버림
- **클라이언트가 리소스를 식별**
  - 클라이언트가 리소스 위치를 알고 URI 지정
  - POST 와 차이점
- {"age":50} : {"username":"kim", "age":20} -> {"age":50}

## PATCH
- 리소스 부분 변경
- {"age":50} : {"username":"kim", "age":20} -> {"username":"kim", "age":50}

## DELETE
- 리소스 제거

## HTTP 메서드의 속성
- 안전 (Safe Methods)
- 멱등 (Idempotent Methods)
- 캐시가능 (Cacheable Methods)
![img.png](img.png)

## 안전 
- 호출해도 리소스를 변경하지 않는다.

## 멱등
- 한 번 호출하든 두 번 호출하든 결과가 똑같다.
- 멱등 메서드
  - GET: 한 번 조회하든, 두 번 조회하든 같은 결과가 조회된다.
  - PUT: 결과를 대체한다. 따라서 같은 요청을 여러번 해도 최종 결과는 같다.
  - DELETE: 결과를 삭제한다. 같은 요청을 여러번 해도 삭제된 결과는 똑같다.
  - **POST**: 멱등이 아니다. 두 번 호출하면 같은 결제가 중복해서 발생할 수 있다.
- 활용
  - 자동 복구 메커니즘
  - 판단 근거: 서버가 TIMEOUT 등으로 정상 응답을 못주었을 때, 클라이언트가 같은 요청을 다시 해도 되는가?
- 멱등은 외부 요인으로 중간에 리소스가 변경되는 것 까지는 고려하지는 않는다.

## 캐시가능
- 응답 결과 리소스를 캐시해서 사용해도 되는가
- GET, HEAD, POST, PATCH 캐시 가능
- 실제로는 GET, HEAD 정도만 캐시로 사용
  - POST, PATCH 는 본문 내용까지 캐시 키로 고려해야 하는데, 구현이 쉽지 않음
  
