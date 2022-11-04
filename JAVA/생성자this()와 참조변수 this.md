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
}
```