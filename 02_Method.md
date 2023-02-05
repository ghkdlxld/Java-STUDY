# 02_Method

### 







#### 메소드 정의 & 호출

```java
// 메소드 정의
public static void sayHello(String name) {
	System.out.println(name + "안녕하세요");
}


public static void main(String[] args) {
    // 메소드 호출
    sayHello("바보"); // 바보안녕하세요
}
```

- public static void `메소드명`(`매개변수`) {

  ​	...

  }





#### 반환값이 있는 메소드

```java
// 메소드 정의
public static String getPhoneNumber(String area){
    String phoneNumber = area + "-1234-5678";
    return phoneNumber;
}

// return값 받아서 사용
public static void main(String[] args) {
    String contactNumber = getPhoneNumber("02");
    System.out.println("전화번호 : " + contactNumber);
}
```

- public static `반환 형태` `메소드명`(`매개변수`) {

  ​			...

  Return ...

  }

