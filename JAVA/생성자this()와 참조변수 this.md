## 생성자 this()
- 생성자에서 같은 클래스의 다른 생성자를 호출할 때, 클래스 이름 대신 this를 사용
- 다른 생성자 호출 시 첫 줄에서만 사용 가능 (다른 생성자로 인해 호출 이전의 초기화 작업이 무의미해지므로 첫 줄)
```java
class MyDate {
    private int year;
    private int month;

    public MyDate() {
        year = 2010;
        month = 8;
    }

    public MyDate(int new_year) {
        this();       //위 2010, 8 
        year = new_year;
    }
    public MyDate(int new_year, int new_month) {
        this(new_year);        //위 생성자 불러옴
        month = new_month;
    }

    public void print() {
        System.out.println(year + "/" + month);
    }
}

public class MyDateMain {
    public static void main(String[] args) {
        MyDate d = new MyDate();
        d.print();               //  2010/8
        MyDate d1 = new MyDate(2020);
        d1.print();              // 2020/8
        MyDate d2 = new MyDate(2022,10);
        d2.print();              // 2022/10
    }
}거
```
#
## 참조 변수 this
- 인스턴스 변수(iv)와 지역변수(lv)의 이름이 같을 때 구별하려고 사용
- this 가 붙으면 iv, 안 붙여주면 매개변수와 가까운 lv
- 인스턴스 자신을 가리키는 참조 변수(객체 주소가 저장되어 있음)
- 인스턴스 메서드에서 사용 가능 / static 메서드에서는 사용 불가
```java
//이름 다를 때
Car(String c, String g, int d) {  //color는 iv, c는 lv   구분이 되기 때문에 그냥 사용
    color = c;
    gearType = g;
    door = d;
}

같을때
Car(String color, String gearType, int door) {
    //this.color는  iv, color는 lv
    this.color = color;
    this.gearType = gearType;
    this.door = door;
}

```