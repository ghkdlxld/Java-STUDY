# 01_Basic

#### 목차

- [선언](#선언)
  - [숫자 변수 선언](#숫자 변수 선언)
- [변수 이름 규칙](#변수 이름 규칙)
- [형변환](#형변환 )
  - [아스키코드](#아스키코드)

- [배열](#배열)
  - [배열에 값 넣기](#배열에 값 넣기)
  - [2차원 배열 선언](#2차원 배열 선언)
  - [3차원 배열 선언](#3차원 배열 선언)
- [반복문](#반복문)





---

### 선언

선언과 동시에 초기화 할 수 있다

```java
// 문자열 변수 선언
String name;
name = "ㅁㅁㅁ";

// 변수 선언과 동시에 초기화
String name = "ㅂㅂㅂ";
```

char은 `''` 사용

String은 `""` 사용





####  숫자 변수 선언

```java
// 정수형 변수
int hour = 15;

// 실수형 변수
double d = 3.14123456789;
float f = 3.14123456789f;   // 실수를 적으면 자동으로 double 형으로 인식함 => 사용하기 위해선 실수값 뒤에 f 적어줌
System.out.println(d);
System.out.println(f); // float은 double만큼 크고, 정밀한 데이터를 넣을 수 없음 => 3.1412346 까지만 출력됨

int i = 1000000000000; int에 넣을 수 없는 범위의 숫자
long l = 1000000000000l;// 정수는 자동으로 int형으로 인식 => 뒤에 l 붙여주기
l = 1_000_000_000_000l; // 언더바 넣어도 같음
System.out.println(l);
```



### 변수 이름 규칙

- camelCase
- snake_case
- 숫자로 시작 불가능



변수와 다르게 상수는 중간에 값을 바꿀 수 없다

상수는 모두 대문자로 표기한다

```java
final String NAME = "ME";
NAME = "YOU"; // 값 변경 불가능!

// 상수의 네이밍에 여러 단어 포함일 경우 _ 로 구분
final Stirng DATE_OF_BIRTH = "1999-08-02;

```







### 형변환 

```java
int score = 93;
System.out.println(score); // 93

// 정수 -> 실수로 변환 (int -> float, double)
System.out.println((float) score); // 93.0
System.out.println((double) score); // 93.0

// float, double -> int
float score_float = 93.3f;
double score_double = 98.8;
System.out.println((int) score_float); // 93 -> 소숫점 이하는 버려짐, 반올림x
System.out.println((int) score_double); // 98 -> 소숫점 이하는 버려짐, 반올림x


// 정수로 선언 값 = 정수 + 실수 -> 불가능! 실수를 정수로 형변환하여 연산
score = 93 + (int) 98.8; // 93 + 98
System.out.println(score); // 191

// 실수로 선언 값 = 정수 + 실수 -> 가능! 정수가 double로 자동 형변환
score_double = 93 + 98.8; // == (double) 93 + 98.8
System.out.println(score_double); // 191.8

// 변수에 형변환된 데이터 집어넣기
double newDoubleScore = score; // double 에 int 넣기 => int가 double로 자동 형변환 -> 191.0
// int -> long -> float -> double ( 자동 형변환 : 굳이 선언해서 형번환 해줄 필요 x )


// int에 double 넣기 불가능 -> 선언해줘야함
// int newIntScore = score_double;
int newIntScore = (int) score_double;
// double -> float -> long -> int ( 수동 형변환 )
```



- String.valueOf()
  - 대상이 null 이면 문자열 "null" 반환
- "".toString()
  - 대상이 null 이면 NullPointerException 발생





#### 아스키코드

```java
char c = 'A';
System.out.println(c); 	 // A
System.out.println(c+1); // 66
c++;
System.out.println(c);   // B
```







### 배열

- 형태[] `배열이름` = new 형태[`배열크기`] ;
- 형태 `배열이름[]` = new 형태[`배열크기`];
- 형태[] `배열이름` = new 형태[] {`item1`, `item2`, ...}; 
- 형태[] `배열이름` = {`item1`, `item2`, ...}; 

```java
String[] coffees = new String[4];
String names[] = new String[4];
String[] coffees = new String[] {"아메리카노", "카페모카", "라떼"}; // 이때는 배열 사이즈 작성 x
String[] coffees = {"아메리카노", "카페모카", "라떼"};
```



#### 배열에 값 넣기

배열[`index`] = `넣을 값`;

size는 해당 index만큼 존재하지만, 아무값도 넣지않는다면 null을 반환 -> 에러가 나진 않음

```java
coffees[0] = "아메리카노";
```



#### 2차원 배열 선언

```JAVA
// 3 * 5 크기의 2차원 배열 (생성x, 선언만 하려면 [] 안에 사이즈넣기)
String[][] seats = new String[][] {
    {"A1", "A2", "A3", "A4", "A5"},
    {"B1", "B2", "B3", "B4", "B5"},
    {"C1", "C2", "C3", "C4", "C5"}
};
```



#### 3차원 배열 선언

```java
// 3차원 배열 만들기 (생성x, 선언만 하려면 [] 안에 사이즈넣기)
String[][][] marray = new String[][][] {
    {{}, {}, {}},
    {{}, {}, {}},
    {{}, {}, {}},
};
```









### 반복문

- for-i

- for-each

  for (`형태` `변수` : `배열이름`) {

  ​		...

  }

```java
// for-i
for (int i = 0; i < coffees.length; i++) {
	System.out.println(coffees[i]);
}


// for-each
for (String coffee : coffees) {
	System.out.println(coffee);
}
```








