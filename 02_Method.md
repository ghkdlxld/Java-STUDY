# 02_Method







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





### 오버로딩, Overloading

> 이름이 같은 메소드를 여러 번 선언하는 것
>
> 전달값의 타입이 다르거나, 갯수가 다를 경우 가능

```java
public static String fool(String name) {
    return name + " 바보";
}

public static String fool(int number) {
    String result = "";
    for (int i = 0; i < number; i++) {
        result += "바보";
    }
    return result;
}

public static String fool(String name, String x) {
    return name + "은/는 " + x + "다";
}

public static void main(String[] args) {
    // 메소드명이 같지만 전달값이 다르므로(타입, 갯수...) 중복해서 사용 가능
    System.out.println(fool("가나다"));		// 가나다 바보
    System.out.println(fool(3));			  // 바보바보바보
    System.out.println(fool("가나다", "천재")); // 가나다은/는 천재다
}

```

