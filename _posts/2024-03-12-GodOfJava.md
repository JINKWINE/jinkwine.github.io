# 자바의 신 정리

### 프로그래밍

프로그래밍이란 어떤 입력을 했을 때 그 입력 값이 미리 설정 된 `"프로그램"`에 의해 정해진 값이 출력되는 것을 말한다. 학교 다닐 때 배웠던 함수(函數)와 같다. 그림 1과 같이 특정 식`(a + b)`이 있는 상자(函)에 입력 값(3과 9)를 집어 넣으면 그 함수(프로그램)에 의해 값(9)을 출력한다.

![그림 1](%E1%84%8C%E1%85%A1%E1%84%87%E1%85%A1%E1%84%8B%E1%85%B4%20%E1%84%89%E1%85%B5%E1%86%AB%20%E1%84%8C%E1%85%A5%E1%86%BC%E1%84%85%E1%85%B5%2019f6c18e92ee4f889f85b187666bfab9/Untitled.png)

그림 1

웹 페이지는 그러한 프로그램들을 웹에서 구현해 놓고 사용자가 요청(입력값)을 하면 미리 설정된 프로그램에 의해 요청 받은 데이터를 화면에 출력해주는 것이다.

### 자바 프로그램 메소드

위 함수 자바 프로그램은 다음과 같이 표현할 수 있다.

```java
public int addNumbers(int a, int b) {
    int result = a + b;
    return result;
}
```

- 메소드란 어떤 값이 주어졌을 때 특정한 값을 도출해주는 것을 말한다. 위 코드 조각에서 메소드는 `a + b` 이며 이 메소드의 이름은 `addNumbers()` 이다.
- 매개 변수 또는 parameter는 말 그대로 변하는 어떤 것이다. 위 코드에서는 정수 a와 b를 말하며 파라미터는 없어도 되며 몇 개가 있더라도 상관 없다.
- 자바의 메소드에는 `리턴 타입`이라는 것이 있어서 결과 값의 형태를 미리 결정하는 역할을 한다. `int`라는 것은 정수만을 출력하는 `기본 자료형` 중 하나이다.

![Untitled](%E1%84%8C%E1%85%A1%E1%84%87%E1%85%A1%E1%84%8B%E1%85%B4%20%E1%84%89%E1%85%B5%E1%86%AB%20%E1%84%8C%E1%85%A5%E1%86%BC%E1%84%85%E1%85%B5%2019f6c18e92ee4f889f85b187666bfab9/Untitled%201.png)

### 클래스

자바의 메소드는 클래스 안에 포함되어야 하며 클래스는 다음과 같이 표현한다.

```java
public class Calculator {
 //중간 생략
 }
```

위에서 Calculator가