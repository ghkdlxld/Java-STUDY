# 03_Class

#### 목차

- [Class 사용](#Class-사용)

- [변수](#변수)

  





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

