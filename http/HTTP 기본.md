# HTTP (Hyper Text Transfer Protocol)
## 특징
- 클라이언트 서버 구조
- 무상태 프로토콜(stateless), 비연결성
- HTTP 메시지
- 단순함, 확장 가능

## 클라이언트 서버 구조
- Request Response 구조
- 클라이언트는 서버에 요청을 보내고, 응답을 대기
- 서버가 요청에 대한 결과를 만들어서 응답

## 무상태 프로토콜 (stateless)
- 서버가 클라이언트의 상태를 보존하지 않음
- 장점: 서버 확장성 높음 (스케일 아웃)
- 단점: 클라이언트가 추가 데이터 전송

## Stateful, Stateless 차이
- Stateful: 중간에 다른 서버로 바뀌면 안된다. (중간에 다른 서버로 바뀔 때 상태 정보를 다른 서버에 미리 알려줘야 한다.)
- Stateless: 중간에 다른 서버로 바뀌어도 된다.
- 무상태는 응답 서버를 쉽게 바꿀 수 있다. -> 무한한 서버 증설 가능
- Stateful 같은 경우 중간에 서버에 장애가 발생할 경우 문제가 일어나지만, Stateless의 경우 아무 서버나 호출해도 된다.

## Stateless 실무 한계
- 모든 것을 무상태로 설계 할 수 있는 경우도 있고 없는 경우도 있다.
- 무상태 - 로그인이 필요없는 단순한 서비스 소개 화면
- 상태 유지 - 로그인
- 로그인한 사용자의 경우 로그인 했다는 상태를 서버에 유지
- 일반적으로 브라우저 쿠키와 서버 세션등을 사용해서 상태 유지
- 상태 유지는 최소한만 사용

## 비 연결성 (connectionless)
- HTTP 는 기본이 연결을 유지하지 않는 모델
- 일반적으로 초 단위 이하의 빠른 속도로 응답
- 1 시간 동안 수천명이 서비스를 사용해도 실제 서버에서 동시에 처리하는 요청은 수십개 이하로 매우 작음
  - ex) 웹 브라우저에서 계속 연속해서 검색 버튼을 누르지는 않는다.
- 서버 자원을 매우 효율적으로 사용할 수 있음

## HTTP 메시지 구조
- start-line 시작 라인
- header 헤더
- empty line 공백 라인 (CRLF)
- message body

## 시작 라인 (요청 메시지)
- ex) GET /search?q=hello&hl=ko HTTP/1.1
- start-line = request-line / Status-line
- HTTP 메서드 (GET)
  - 서버가 수행해야 할 동작 지정
- 요청 대상 (/search?q=hello&hl=ko)
- HTTP Version

## 시작 라인 (응답 메시지)
- ex) HTTP/1.1 200 OK
- HTTP 버전
- HTTP 상태 코드: 요청 성공, 실패를 나타냄
  - 200: 성공
  - 400: 클라이언트 요청 오류
  - 500: 서버 내부 오류
- 이유 문구: 사람이 이해할 수 있는 짧은 상태 코드 설명 글

## HTTP 헤더
![img.png](img.png)
- HTTP 전송에 필요한 모든 부가정보
- ex) 메시지 바디의 내용, 메시지 바디의 크기, 압축, 인증, 요청 클라이언트 정보 등
- 표준 헤더가 너무 많음
- 필요시 임의의 헤더 추가 가능

## HTTP 메시지 바디
![img_1.png](img_1.png)
- 실제 전송할 데이터
- HTML 문서, 이미지, 영상, JSON 등 byte 로 표현할 수 있는 모든 데이터 전송 가능