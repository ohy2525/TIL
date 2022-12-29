## 열거형 (enum)
- 관련된 상수들을 같이 묶어 놓은 것. Java 는 타입에 안전한 열거형을 제공
```java
class Card {
    enum Kind { CLOVER, HEART, DIAMOND, SPADE}  //열거형 Kind를 정의
    enum Value { TWO, THREE, FOUR}  //열거형 Value를 정의
    
    final Kind kind;
    final Value value;
}

if(Card.Kind.CLOVER == Card.Value.TWO) {  // 컴파일 에러. 타입이 달라서 비교 불가
}
```
- 클래스처럼 보이게 하는 상수
- 서로 관련있는 상수들끼리 모아 상수들을 대표할 수 있는 이름으로 타입을 정의하는 것
- Enum 클래스 형을 기반으로 한 클래스형 선언

### 열거형의 정의와 사용
- 열거형을 정의하는 방법
  - enum 열거형이름{상수명1, 상수명2, ...}
- 열거형 상수의 비교에 == 와 compareTo() 사용 가능

### 열거형에 멤버 추가하기
- 불연속적인 열거형 상수의 경우, 원하는 값을 괄호()안에 적는다
- 괄호()를 사용하려면 , 인스턴스 변수와 생성자를 새로 추가해 줘야 한다.
```java
enum Direction {
    EAST(1), SOUTH(5), WETS(-1), NORTH(10);   //끝에 ; 추가해야 한다.
    private final int value;   //정수를 저장할 필드(인스턴스 변수)를 추가
    Direction(int value) {this.value = value;}   // 생성자를 추가
    
    public int getValue() { return value;}
}
```
- 열거형의 생성자는 묵시적으로 private 이므로, 외부에서 객체 생성 불가