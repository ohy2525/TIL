### StringBuffer 클래스
- String 처럼 문자열 배열(char[])을 내부적으로 가지고 있다.
- 그러나 String과 달리 내용을 변경할 수 있다.(mutable)
- 문자열을 가지고 조작을 많이 할 경우 StringBuffer 사용

### StringBuffer의 변경
- StringBuffer는 String 과 달리 내용 변경이 가능.
- append()는 지정된 내용을 StringBuffer에 추가 후, StringBuffer의 참조를 반환

### StringBuffer의 비교
- StringBuffer는 equals()가 오버라이딩 되어있지 않다. (**주소비교**)
```java
StringBuffer sb = new StringBuffer("abc");
StringBuffer sb2 = new StringBuffer("abc");

System.out.println(sb==sb2);          //false
System.out.println(sb.equals(sb2));   //false
```
- StringBuffer를 String으로 변환 후에 equals()로 비교해야 한다.
```java
String s = sb.toString();
String s2 = sb2.toString();

System.out.println(s.equals(s2));     //true
```


### StringBuffer의 생성자와 메서드
- StringBuffer() - 16문자를 담을 수 있는 버퍼를 가진 StringBuffer 인스턴스를 생성한다.
```java
StringBuffer sb = new StringBuffer();
```
- StringBuffer(int lenght) - 지정된 개수의 문자를 담을 수 있는 버퍼를 가진 StringBuffer 인스턴스를 생성한다.
```java
StringBuffer sb = new StringBuffer(10);
```
- StringBuffer(String str) - 지정된 문자열 값(str)을 갖는 StringBuffer 인스턴스를 생성한다.
```java
StringBuffer sb = new StringBuffer("HI");
```
- StringBuffer append() - 매개변수로 입력된 값을 문자열로 변환하여 StringBuffer 인스턴스가 저장하고 있는 문자열의 뒤에 덧붙인다.
```java
StringBuffer sb = new StringBuffer("abc");
StringBuffer sb2 = sb.append(true);

//sb2 = "abctrue"
```
- int capacity() - StringBuffer 인스턴스의 버퍼크기를 알려준다. length()는 버퍼에 담긴 문자열의 길이를 알려준다.
```java
StringBuffer sb = new StringBuffer(100);
sb.append("abcd");
        
//sb.capacity() = 100
//sb.length() = 4
```
- char charAt(int index) - 지정된 위치에 있는 문자를 반환.
- StringBuffer delete(int start, int end) - 시작위치부터 끝 위치 사이에 있는 문자를 제거한다. 단, 끝 위치의 문자는 제외.
- StringBuffer deleteCharAt(int index) - 지정된 위치의 문자를 제거.
- StringBuffer insert(int pos, 매개변수) - 두 번째 매개변수로 받은 값을 문자열로 변환하여 지정된 위치(pos)에 추가한다. pos는 0부터 시작
- StringBuffer replace(int start, int end, String str) - 지정된 범위의 문자들을 주어진 문자열로 바꾼다. end위치의 문자는 범위에 포함되지 않는다.
- StringBuffer reverse() - StringBuffer 인스턴스에 저장되어 있는 문자들의 순서를 거꾸로 나열한다.
- void setCharAt(int index, char ch) - 지정된 위치의 문자를 주어진 문자로 바꾼다.
- void setLength(int newLength) - 지정된 길이로 문자열의 길이를 변경한다. 길이를 늘리는 경우에 나머지 빈 공간을 널문자 '\u0000' 로 채운다.
```java
StringBuffer sb = new StringBuffer("0123456");
sb.setLength(5);

//sb = "01234
```
- String toString() - StringBuffer 인스턴스의 문자열을 String으로 반환
- String substring(int start, int end) - 지정된 범위 내의 문자열을 String 으로 뽑아서 반환한다. 시작위치만 지정하면 시작위치부터 문자열 끝까지 뽑아서 반환한다.

### StringBuilder
- StringBuffer는 동기화되어 있다. 멀티 쓰레드에 안전(thread-safe)
- 멀티 쓰레드 프로그램이 아닌 경우, 동기화는 불필요한 성능저하
- 이럴땐 StringBuffer 대신 StringBuilder를 사용하면 성능 향상