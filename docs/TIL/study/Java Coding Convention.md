---
layout: post
title:  "Java Coding Convention"
date:   2022-08-04 14:29:06 +0900
categories: TIL
---


<span style="color:green"> Java 코딩 가이드(Google) </span>
===============================================

<br>

<span style="color:red">Formatting</span>
-----------------------------------------

<br>

<h3>1. 인코딩</h3>

- UTF-8

<br>

<h3>2. 들여쓰기</h3>

- TAB 대신 space 4개사용. (사용자 설정에따라 간격이 다르게 보일수도있기때문)

<br>

<h3>3. 중괄호</h3>

- K&R 스타일 사용. 시작하는 중괄호를 제어문과 같은 라인에서 사용함
제어문이 한줄이라도 중괄호 생략x

    ```java
    if (test == note) {
        System.out.println("test");
    }
    ```

<br>

<h3>4. 띄어쓰기</h3>

- 메소드 이름 다음에는 띄어쓰기없이 괄호 사용

    ```java
    test(x,y);
    ```

<br>

- 배열 다음에는 띄어쓰기 없이 왼쪽괄호 사용

    ```java
    args[0];
    ```
<br>


- 이진 연산자 간에는 양쪽에 띄어쓰기를 사용

    ```java
    a = b + c;
    z = 2 * x + 3 * y;
    ```
<br>


- 쉼표와 세미콜론 뒤에는 띄어쓰기를 사용

<br>


- cast 사용시 띄어쓰기 없이 작성
    ```java
    (MyClass)v.get(3);
    ```

<br>

- if, while, for, switch, catch 문 뒤에는 띄어쓰기 사용

<br>


<h3> 5. 클래스 멤버 정렬순서</h3>

<br>

- 필드(전역변수), 생성자, 메소드 순서로 작성한다.

    ```java
    class Test
    {
        // fields (attributes)

        // constructors

        // methods
    }
    ```

<br>

<h3>6. 라인 최대 길이</h3>

<br>

- 100칸을 넘지 않는다.

<h3> C 스타일 배열 선언 금지 </h3>

<br>

```java
String[] args;
```

<span style="color:red"> 네이밍 </span>
---------------------------------------

<br>

<h3>1. 클래스와 인터페이스명</h3>

<br>

- 각 단어의 첫 글자는 대문자로 나머지를 소문자를 사용

- 두문자어(acronym)도 같은 규칙을 사용
```java
XMLHTTPRequest  // NO!
XmlHttpRequest  // YES!

getCustomerID   // NO!
getCustomerId   // YES!

class HTML      // NO!
class Html      // YES!

String URL      // NO!
String url      // YES!

long ID         // NO!
long id         // YES!
```

<h3>2. 패키지명</h3>

- 소문자 8글자 이내로 사용

- 복합단어 사용금지
```java
    subwayzone  // NO!
    zone.subway // YES!
```

- 그외의 모든 식별자 (필드 식별자, 변수, 메소드, 파라미터 등)

    첫 단어를 제외한 첫 글자는 대문자로 나머지는 소문자를 사용. 
    
    두문자어(acronym)는 대문자 사용하되 첫 단어인 경우는 모두 소문자를 사용.

    ```java
    customer
    salesOrder
    addToTotal()
    targetURL
    urlTarget
    ```

<h3>3. 코딩</h3>

<br>

- do while 사용금지

    do while 문은 조건이 코드 아래 부분에 있기 때문에 가독성이 좋지 않고, 경험이 적은 프로그래머에게도 익숙하지 않은 문법이다.

    ```java
    So rather than:
        boolean done = false;
        do
        {
            ...
        } while (!done)
    use:
        boolean done = false;
        while (!done)
        {
        ...
        }
    ```
    
- 메소드 중간에 return사용 금지

    return을 메소드 중간에 작성한다면 추후 코드를 수정할때 고려할 사항이 많아지고 버그를 유발시킬 가능성이 높아지므로, 메소드 마지막에 작성해야된다.

<br>

- continue 사용금지

    수정 시에 2개 이상의 end point를 고려해야 하기 때문에 코드 수정이 어려워 진다.

<br>

- break는 switch 이외의 다른 제어문에서 사용하지 않는다.

    수정 시에 2개 이상의 end point를 고려해야 하기 때문에 코드 수정이 어려워 진다.

<br>

- 증감 연산자는 분리된 라인에서 사용

    ```java
    foo(x++); // NO!

        foo(x);   // YES!
        x++;

        y += 100 * x++;  // NO!

        y += 100 * x;    // YES!
        x++;
    ```

<br>

- 초기화

    변수가 사용되는 곳의 가까운 위치에 변수를 선언.
    
    ```java
    int totalWide;
    int firstWide = 20;
    int secondWide = 12;
    firstWide = doFoo(firstWide, secondWide);
    doBar(firstWide, secondWide);
    totalWide = firstWide + secondWide;         //  wrong!

    int firstWide = 20;
    int secondWide = 12;
    firstWide = doFoo(firstWide, secondWide);
    doBar(firstWide, secondWide);
    int totalWide = firstWide + secondWide;     //  right!

    int secondWide = 12;
    int firstWide = doFoo(20, secondWide);
    doBar(firstWide, secondWide);
    int totalWide = firstWide + secondWide;     //  even better!
    ```

- 접근

    상수를 제외한 모든 필드는 private해야 한다.

<br>

- 와일드 카드 임포트 사용 금지
    ```java
    import java.io.*; // bad
    import java.io.File; // good
    import java.io.FileReader; // good
    ```

- 스위치문 사용시엔 반드시 default를 정의한다.