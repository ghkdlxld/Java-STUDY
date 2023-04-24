# 03_Class

#### 목차

- [Class 사용](#Class-사용)

- [변수](#변수)

- [Method](#Method)

  





---

### Class 사용

- 여러개의 변수를 한번에 관리할 수 있음

- 배열은 한 배열안에 여러 타입의 변수를 저장할 수 없음
- Class명은 **대문자**로 시작하도록 작성

```java
// Class Student.java 
public class Student {
    // 3개의 인스턴스 변수
    String studentName;
    String school;
    int studentnum;
}
```

```java
// Class 사용
Student std = new Student();
std.studentName = "다나카";
std.school = "오리무중";
std.studentnum = 7;
```

- Student 클래스로부터 std 객체를 생성했다
- std 객체는 Student 클래스의 인스턴스
- `Class명` `사용할 변수명` = new `Class명()`





### 변수

```java
// Class Student.java 
public class Student {
    // 3개의 인스턴스 변수
    String studentName;
    String school;
    int studentnum;
    
    // static이 붙은거는 class 변수
    // class 변수 = class를 가지는 모든 객체에 똑같이 적용됨
    static boolean graduation = false;
}
```

```java
public static void main(String[] args) {
    Student std1 = new Student();
    std1.studentName = "다나카";

    Student std2 = new Student();
    std2.studentName = "가나다";


    System.out.println(std1.studentName + " 졸업여부 : " + std1.graduation);
    System.out.println(std2.studentName + " 졸업여부 : " + std2.graduation);
    System.out.println("모든 학생 졸업여부 : " + Student.graduation);

    // class변수 한번 업데이트 하면 모든 객체에 반영됨
    Student.graduation = true;
    System.out.println(std1.studentName + " 졸업여부 : " + std1.graduation);
    System.out.println(std2.studentName + " 졸업여부 : " + std2.graduation);
    System.out.println("모든 학생 졸업여부 : " + Student.graduation);
}
```

- `instance 변수` = 서로 다른 객체에서 서로 다른 값을 가짐
- 모든 객체에 동일하게 반영하고 싶은 값이 있는경우는 `Class 변수` 사용 
- `객체명.변수` 말고 `Class명.변수`가 권장 방식





### Method

```java
// Class Student.java 
public class Student {
    String studentName;
    
    static boolean graduation = false;
    
    // 반환값이 없을 경우 void
    void autoCheck() {
        if (graduation) {
            System.out.println("졸업하였습니다.");
        }
        else {
            System.out.println("재학중입니다.");
        }
    }
    }
}
```

```java
Student s1 = new Student();
s1.studentName = "가나다";

s1.autoCheck(); // "재학중입니다."
Student.graduation = true;
s1.autoCheck(); // "졸업하였습니다."
```

- `반환타입` `메소드명()` {

  ​	...

  }





### Method Overloading

```java
void exam(eng, kor, time) {
    System.out.println("시험을 시작합니다.");
    if (eng) {
        System.out.println("영어시험을 시작합니다.");
    }
    if (kor) {
        System.out.println("국어시험을 시작합니다.");
    }
    System.out.println("시험은" + time + "시간 동안 진행됩니다.");
}


void exam() {
    // 하나하나 다시 정의할 수도 있지만 다시 함수를 호출하여 사용 가능
    exam(true, true, 5);
}
```

이름이 같은 메소드라도 전달값의 타입이 다르거나, 갯수가 다를 경우 가능(=오버로딩)

같은 클래스 내에서 메소드 오버로딩 가능

재 정의 시 원래의 메소드를 호출하여 사용 가능







### Class Method

```java
static void call() {
    System.out.println("우리집(1234-5678)에 전화해.");
}
```

method 앞에 static을 사용하여 정의

class method (x) => 객체마다 각각 다른 인스턴스변수를 가지기 때문에 객체마다 각각 다르게 동작할 수 있음

class method (0) => 어느 객체에서든 같은 동작 (모든 객체에 공통적으로 적용)



**객체를 만들지 않고 class의 class method에 직접 접근도 가능**

```java
Student s1 = new Student();
s1.call();	// "우리집(1234-5678)에 전화해."

Student.call(); // "우리집(1234-5678)에 전화해."
```



**static으로 선언한 static  변수는 static method에서 사용 가능**

인스턴스 변수는 사용 불가능 -> 인스턴스 변수의 사용이 필요 없는 경우에 class method 활용 가능

```java
// 위에서 정의한 static 변수 graduation
// static boolean graduation = false;


// 위에서 정의한 인스턴스 변수 studentName
// String studentName;


static void call() {
    System.out.println("우리집(1234-5678)에 전화해.");
    graduation = false; // 가능
    studentName = "가나다"; // 불가능
}
```









### This

기존의 studentName 인스턴스 변수에 입력된 매개변수를 더해서 출력하는 method를 만드려고 한다

```java
// 1.
void appendStudentName(String studentName) {
	studentName += studentName;
}

// 올바른 예시
void appendStudentName(String studentName) {
	this.studentName += studentName;
}
```

1번처럼 작성하게 되면 그냥 매개변수 += 매개변수 를 실행하고 끝나버린다.

인스턴스 변수와 매개변수의 이름이 같을 때, 인스턴스 변수에 변화를 주고 싶다면 this를 사용한다 

=> `this.변수` 로 작성하여 인스턴스변수와 매개변수를 구분해줄 수 있다.







### 생성자

```java
Student() {
	System.out.println("기본 생성자 호출")
}
```

```java
public static void main(String[] args) {
    Student s1 = new Student(); // 기본 생성자 호출
}
```

맨 처음 객체를 만들 때, 자동으로 호출되는 메서드

생성자를 사용하여 편하게 객체 생성시 인스턴스 변수값을 넣어줄 수 있다.

```java
public static void main(String[] args) {
    Student s1 = new Student();
    s1.studentName = "가나다";
    s1.school = "abc고등학교";
    s1.studentnum = 20230424;
}
```

