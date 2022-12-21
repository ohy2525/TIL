#### hashCode()
- 객체의 해시코드(hash code)를 반환하는 메서드
- Object 클래스의 hashCode()는 객체의 주소를 int로 변환해서 반환
- equals()를 오버라이딩하면, hashCode()도 오버라이딩해야 한다.
- **equals()의 결과가 true인 두 객체의 해시코드는 같아야 하기 때문**
```java
String str1 = new String("abc");
String str2 = new String("abc");
System.out.println(str1.equals(str2));   //true
System.out.println(str1.hashCode());   //96354
System.out.println(str2.hashCode());   //96354  (오버라이딩)
```

### toString(), toString()의 오버라이딩
- toString() : 객체를 문자열(String)으로 변환하기 위한 메서드
```java
public String toString() {     //Object 클래스의 toString()
    return getClass().getName()+"@"+Integer.toHexString(hashCode());
}
//-> 오버라이딩
public String toString() {
    return "kind : " + kind + ", number : " + number;   //문자열 결합
}
```

### equals(Object obj)
- 객체 자신(this)과 주어진 객체(obj)를 비교한다. 같으면 true 다르면 false.
- Object 클래스의 equals()는 객체의 주소르 비교(참조변수 값 비교)
```java
public boolean equals(Object obj) {
    return (this==obj); //주소 비교
}
```

### equals(Object obj)의 오버라이딩
- 인스턴스 변수(iv)의 값을 비교하도록 equals()를 오버라이딩해야 한다.
```java
class Person {
    long id;
    
    public boolean equals(Object obj) {
        if(obj instanceof Person)
            return id == ((Person)obj).id;  //obj 가 Object 타입이므로 id값을 참조하기 위해서는 Person타입으로 형변환이 필요하다.
    }
    
    Person(long id) {
        this.id = id;
    }
}
```