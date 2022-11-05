## 참조 변수 super (this 와 비슷)
- 객체 자신을 가리키는 참조 변수. 인스턴스 메서드(생성자) 내에서만 존재
- 조상의 멤버를 자신의 멤버와 구별할 때 사용
```java
class Ex {
    public static void main(String args[]) {
        Child c = new Child();
        c.method();
    }
}

class Parent { int x = 10;  /*  super.x  */  }

class Child extends Parent {
    int x = 20;  //this.x                    만약 없다면 this.x = 10
    
    void method() {
        System.out.println("x=" + x);                       
        System.out.println("this.x=" + this.x);
        System.out.println("super.x=" + super.x);
    }
}
/*
결과
x=20
this.x=20
super.x=10
*/

```
## 조상의 생성자 super()
- 조상의 생성자를 호출할 때 사용(생성자와 초기화 블록은 상속 안 되기 때문)
- 조상의 멤버는 조상의 생성자를 호출해서 초기화
- 자손의 생성자는 자신이 선언한 변수만 초기화할 수 있다.
- 생성자의 첫 줄에 반드시 생성자를 호출해야 한다.그렇지 않으면 컴파일러가 생성자의 첫 줄에 super()를 삽입.
```java
class Point {
    int x, y;
    
    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

class Point3D extends Point {
    int z;
    
    Point3D(int x, int y, int z) {
        super(x, y);    //조상클래스의 생성자 Point(int x, int y)를 호출
        this.z = z;     //자신의 멤버를 초기화
    }
}
```
#
ex)
```java
class Parent {
	int x = 100;
	Parent() {
        this(200);
	}
	Parent(int x) {
		this.x = x;
	}
	int getX() {
		return x;
	}
}

class Child extends Parent {
	int x = 3000;
	Child() {
		this(1000);
	}
	Child(int x) {
		this.x = x;
	}
}


class Exercise {
	public static void main(String[] args) {
		Child c = new Child();
		System.out.println("x=" + c.getX());
	}
}
```
호출되는 생성자의 순서와 실행결과

순서)  Child() → Child(int x) → Parent() → Parent(int x) → Object()

실행결과) x = 200

#

해설:

컴파일러는 생성자의 첫 줄에 다른 생성자를 호출하지 않으면 조상의 기본 생성자를 호출하는 코드 'super( );' 를 넣는다.
그래서 Child(int x){ this.x = x; } 이 코드는 컴파일 후 Child(int x){ super( ); this.x =x; } 와 같은 코드로 바뀐다.
마찬가지로 Parent(int x) 역시 컴파일러가 Parent의 조상인 Object클래스의 기본 생성자를 호출하는 코드를 넣는다.
Child( ) → Child(int x) → Parent( ) → Parent(int x) → Object( )의 순서로 호출되니까, Child클래스의 인스턴스변수 x는 1000이 되고, Parent 클래스의 인스턴스변수 x는 200이 된다.  getX( )는 조상인 Parent의 클래스에 정의된 것이라서, getX( )에서 x는 Parent 클래스의 인스턴스변수 x를 의미한다. 그래서 x=200이 출력된다.