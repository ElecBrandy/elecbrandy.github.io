+++
title = '[OOP] 캡슐화'
date = 2024-09-02
featured_image = "https://miro.medium.com/v2/resize:fit:910/format:webp/1*SDetxWyCUpDq6ju7xhdNYA.jpeg"
tags = ['c++', 'cs101']
+++

<details>
<summary><strong>📂 : OPP 모아보기</strong></summary>
<div markdown="1">


- <a href="https://elecbrandy.github.io/tags/opp/capsule"> **[0]** : 캡슐화 </a>  

- <a href="https://elecbrandy.github.io/tags/opp/"> **[1]** : Stack </a>  

- <a href="https://elecbrandy.github.io/tags/opp/"> **[2]** : Queue </a>  

</div>
</details>

<br>

> ??? : Class는 붕어빵 틀, instance는 붕어빵...?

<br>

# 객체지향 이전의 세계
____
객체지향이란 무엇일까? 인터넷에 검색해보면 "객체를 지향하는 프로그래밍"이라는 복잡한 설명과 함께, "클래스는 붕어빵 틀이고 인스턴스는 그 틀로 찍어낸 붕어빵이다..." 같은 비유를 흔히 보게 된다. 그런데 이런 설명만으로는 객체지향의 본질을 파악하기 어렵다. 그렇다면 객체지향을 공부하기 전에, 이 개념이 왜 등장하게 되었는지 먼저 살펴보자.

42과정을 진행하면서 처음으로 접하게 되는 언어는 C이다. C는 대표적인 절차지향 언어로, 프로그램을 일련의 명령과 함수로 구성해 나가는 방식이다. 처음엔 간단한 프로그램을 짜는 데 어려움이 없었고, 몇몇 과제는 금방 끝났다. 하지만 과제가 점점 복잡해지고, 코드의 규모가 커질수록 문제들이 발생하기 시작했다.

프로젝트가 커지면서 중복된 로직과 비슷한 구조들이 여기저기 산발적으로 흩어지기 시작했다. 함수와 변수를 최대한 잘 배치하려 노력했지만, 아무리 신경 써도 코드가 점점 비논리적으로 느껴졌다. 그나마 구조체를 사용해 관련된 변수를 묶어 놓으니 정리는 좀 되었지만, 함수와 로직도 관련된 변수와 함께 묶고 싶을 때는 마땅한 방법이 보이지 않았다.

이렇게 점점 더 많은 에러와 비효율성이 나타나면서, 무언의 한계를 절실히 느끼게 되었다.

<br>
<br>

# 객체지향의 등장
____
그러던 중, 마침내 CPP 과제에 도착하면서 객체지향 프로그래밍과 만나게 되었다. 절차지향과 작별하고 객체지향의 문을 두드리면서, 그동안 C에서 느꼈던 불편함을 해소할 수 있을 거란 희망이 생겼다. 객체지향은 연관된 변수와 함수들을 하나의 객체로 묶어 논리적으로 관리할 수 있는 규칙을 제공한다.

객체지향의 핵심은 바로 이 부분이다. 객체를 통해 관련된 데이터와 동작을 한 곳에 묶어 관리함으로써, 코드의 가독성과 유지보수성을 크게 향상시킬 수 있다. 내가 C에서 느꼈던 문제들은 결국 이 규칙을 통해 해결할 수 있는 문제들이었다. 단순히 변수만 묶는 것이 아니라, 함수까지 함께 묶어서 연관된 모든 요소들을 하나의 객체로 관리하는 것이 포인트이다.

<br>
<br>

# 객체지향이란 무엇일까?
____
그럼 이제 객체지향이 무엇인지 더 구체적으로 알아보자. 앞서 말했듯이, 객체지향이란 비슷한 그룹이나 반복되는 로직들을 잘 정리해 유지보수도 쉽게 하고, 전체 구조도 깔끔하게 만들 수 있는 방법처럼 느껴졌다. 그렇다면 좀 더 정확하게 살펴보자.  

사전적 개념에 따르면, **객체지향 프로그래밍(Object-Oriented Programming, OOP)**은 **데이터(속성)**와 그 데이터를 다루는 **동작(메서드)**를 하나의 객체로 묶어 프로그램을 구성하는 방식이다. 핵심은 객체라는 개념을 통해 현실 세계의 사물이나 개념을 추상화하여 코드로 표현하는 것이다. 아래는 객체지향 프로그래밍의 대표적은 특징 4가지이다.  

**1. 캡슐화(Encapsulation)**
데이터를 객체 내부에 감추고, 외부에는 필요한 부분만 노출하는 방식이다. 이로 인해 데이터가 보호되고, 코드의 복잡성도 줄어들게 된다. 쉽게 말하면, "내부에서 일어나는 일은 감추고, 필요한 인터페이스만 제공하라"는 원칙이다.  

**2. 상속(Inheritance)**
이미 존재하는 클래스를 확장해 새로운 클래스를 만드는 기능이다. 부모 클래스의 기능을 물려받아 코드의 중복을 줄이고, 프로그램의 확장성을 높일 수 있다. 마치 부모의 재산을 물려받는 것처럼 기존의 코드를 재사용할 수 있는 것이다.

**3. 다형성(Polymorphism)**
같은 이름의 메서드가 다양한 객체에서 다른 방식으로 동작할 수 있게 한다. 이를 통해 코드가 더 유연해지며, 상황에 맞게 다르게 행동할 수 있는 프로그램을 만들 수 있다. 예를 들어, '걷다'라는 동작이 인간과 로봇에서 다르게 구현될 수 있는 것처럼 말이다.

**4. 추상화(Abstraction)**
복잡한 시스템을 단순화해, 필요한 부분만 노출하고 나머지는 숨기는 방법이다. 현실 세계에서 중요한 정보만 골라내어 표현하는 것과 같다. 복잡한 기능을 간단한 인터페이스로 표현하는 것이 추상화의 핵심이다.

이렇게 보면 객체지향은 매우 강력한 도구처럼 보인다. 그러나 아직도 왜 이런 특징이 필요한지 모호할 수 있다. 왜 이런 개념들이 만들어졌을까? 객체지향의 특징들이 실제로 어떤 문제를 해결해 주는지 앞으로 더 알아보도록하자.

<br>
<br>

# 클래스
____

## 클래스의 정의
먼저 클래스를 알아보자. 객체지향에서 객체를 만들기 위해서는 클래스라는 개념이 필요하다. 클래스는 객체를 정의하는 청사진 또는 설계도라고 할 수 있다. 클래스는 데이터를 저장하는 변수(속성)와 데이터를 처리하는 함수(메서드)를 포함하고 있다. 이러한 클래스라는 설계도를 통해 우리는 실제로 사용할 객체(인스턴스)를 만들 수 있다.  

즉, 클래스는 객체를 정의하는 틀이고, 이를 기반으로 생성된 것이 바로 객체(인스턴스)이다.

<br>
<br>

## 클래스의 구성
클래스 내부를 들여다보면 처음 보는 용어들이 많아 혼란스러울 수 있다. 멤버 변수? 멤버 함수? 생성자? 이러한 용어들이 무엇인지 하나씩 알아보자. 또한, 객체지향에서 중요한 개념은 비슷한 것들끼리 묶는다는 것이다. 즉, 관련된 데이터와 기능을 하나의 클래스 안에 모아두는 것이 객체지향의 본질이다.  

이때, 비슷한 것들이 한 곳에 묶여 있다면 그것들은 외부와 분리되어 있다는 의미이기도 하다. 그리고 이 클래스 내부에 접근하려면 일종의 규칙이 필요하다. 마치 보안 문을 열 때 비밀번호나 암호를 입력해야 하는 것처럼 말이다. 이 규칙을 위해 객체지향에서는 접근 제어를 통해 클래스 내부와 외부 간의 구분을 한다.

- public: 클래스 외부에서 접근 가능한 것을 의미한다. 외부에서 자유롭게 사용할 수 있는 부분이다.
- private: 클래스 내부에서만 접근 가능한 것을 의미한다. 외부에서 직접 접근할 수 없는 부분으로, 클래스 내부에서만 사용된다.
- 멤버 변수: 클래스 안에 정의된 변수로, 객체의 속성값을 저장한다.
- 멤버 함수: 클래스 안에 정의된 함수로, 객체의 행동을 정의한다.
- 인터페이스: 외부에서 접근할 수 있는 public 멤버 함수나 변수를 의미한다. 클래스의 외부에서 호출할 수 있는 부분이다.
- 구현: 클래스 내부에서만 사용되는 private 멤버 함수나 변수를 의미한다. 클래스 내부에서 로직을 처리하는 부분이다.

<br>
<br>

## public과 private
그러면 왜 굳이 public과 private로 접근을 구분할까? 간단한 이유는 보안과 데이터 무결성을 위해서다. 특정 데이터는 외부에서 쉽게 조작되지 않도록 보호할 필요가 있기 때문이다. 이제 코드를 통해 살펴보겠지만, 이 개념을 쉽게 이해할 수 있는 예를 들어보자.  

사용자 정보를 저장하는 User 클래스가 있다고 하자. 이 클래스에는 사용자의 비밀번호를 저장하는 변수가 있을 것이다. 하지만 비밀번호는 매우 중요한 정보이므로, 아무나 변경할 수 있으면 안 된다. 그래서 비밀번호는 private 변수로 설정해 외부에서 직접 접근하지 못하게 한다.  

그런데 비밀번호를 변경해야 하는 상황이 생길 수 있다. 사용자가 비밀번호 변경을 요청했거나, 보안 정책에 따라 변경해야 할 수도 있다. 이런 상황을 위해, private 비밀번호 변수에 접근해 값을 변경하는 password_change라는 함수를 만들 수 있다. 이 함수는 비밀번호 변경 로직을 담고 있으며, 이 함수 또한 외부에서 직접 호출하지 못하게 private로 설정할 수 있다.  

이렇게 하면, 비밀번호 변수와 변경 로직은 외부로부터 보호되지만, 필요한 상황에서만 안전하게 변경할 수 있도록 관리할 수 있다. 즉, public과 private을 통해 안전하게 관리해야 할 데이터와 외부에 공개해도 되는 기능을 구분할 수 있다.  


<br>
<br>

# 캡슐화
___
처음에는 **"굳이 왜 이렇게 복잡하게?"**라는 생각이 들 수 있다. 클래스 내부와 외부의 접근을 구분하고, `private`과 `public`으로 나누는 일이 왜 중요한지 궁금할 것이다. 하지만 **캡슐화**의 개념을 이해하고 나면, 이것이 얼마나 중요한 역할을 하는지 깨닫게 된다.

캡슐화는 객체지향 프로그래밍에서 **객체 내부의 데이터를 보호**하고, **안전하게 다루기 위해 정보 은닉**을 보장하는 기법이다. 이를 통해 코드의 **보안성**, **유지보수성**, **확장성**을 크게 향상시킬 수 있다. 아래에서 하나의 코드 예시로 캡슐화의 다양한 이점을 설명해보겠다. 그 유명한 은행계좌 관련 예시임!

``` C++
#include <iostream>

class BankAccount {
private:
    int balance;  // 계좌 잔액 (private 변수로 외부 접근 불가)

    // private 메서드: 계좌의 상태를 출력 (내부에서만 사용)
    void printBalance() const {
        std::cout << "현재 잔액: " << balance << "원" << std::endl;
    }

public:
    // 생성자: 초기 잔액 설정 (public으로 외부에서 호출 가능)
    BankAccount(int initialBalance) {
        if (initialBalance >= 0)
            balance = initialBalance;
        else
            balance = 0;
    }

    // 입금 함수 (public으로 외부에서 호출 가능)
    void deposit(int amount) {
        if (amount > 0)
            balance += amount;
        printBalance();  // 입금 후 상태 출력
    }

    // 출금 함수 (public으로 외부에서 호출 가능)
    void withdraw(int amount) {
        if (amount > 0 && amount <= balance)
            balance -= amount;
        printBalance();  // 출금 후 상태 출력
    }

    // 잔액 확인 함수 (public으로 외부에서 호출 가능)
    int getBalance() const {
        return balance;
    }
};

int main() {
    BankAccount account(1000);  // 계좌 생성, 초기 잔액 1000원
    account.deposit(500);       // 500원 입금
    account.withdraw(300);      // 300원 출금
    std::cout << "최종 잔액: " << account.getBalance() << "원" << std::endl;  // 잔액 확인
    return 0;
}
```

#### 1. **데이터 무결성 보장**
위 코드에서 **`balance`**는 `private`으로 선언되어 외부에서 직접 수정할 수 없다. 따라서 외부에서 `account.balance = 5000;`과 같이 마음대로 잔액을 변경할 수 없다. 잔액의 수정은 반드시 `deposit()`이나 `withdraw()`와 같은 **`public` 함수**를 통해 이루어지므로, 계좌의 상태가 항상 **의도한 방식**으로만 변경된다. 이를 통해 **데이터 무결성**을 보장할 수 있다.

#### 2. **코드 유지보수성 향상**
내부에서 사용되는 **`printBalance()`** 함수는 `private`으로 선언되어, 클래스 외부에서 호출할 수 없다. 만약 이 함수의 구현을 바꾸어야 한다면, 외부의 코드를 수정할 필요 없이 클래스 내부에서만 수정하면 된다. 즉, **캡슐화를 통해 내부 구현을 바꿔도 외부 코드에 영향을 주지 않고 유지보수가 가능하다**.

#### 3. **명확한 인터페이스 제공**
클래스 외부에서는 `deposit()`, `withdraw()`, `getBalance()`와 같은 **`public` 함수**만 신경 쓰면 된다. 불필요하게 내부 로직을 알 필요가 없으며, 외부에서는 간단한 인터페이스만 알면 된다. 이를 통해 **클래스의 사용법이 명확해지고, 혼란이 줄어든다**.

#### 4. **의도된 동작 보장**
만약 `balance`가 음수가 될 수 없도록 하고 싶다면, `withdraw()` 함수에서 조건을 추가하여 음수 출금이 불가능하도록 만들 수 있다. 이를 통해 객체가 **의도하지 않은 방식**으로 사용되지 않도록 강제할 수 있다. 예를 들어, `withdraw()` 함수는 음수 값이나 잔액보다 큰 금액을 출금할 수 없도록 한다. **캡슐화를 통해 잘못된 사용을 방지하고 프로그램의 안정성을 높일 수 있다**.

<br>
<br>

# 결론
___
객체지향의 이전부터, 캡슐화까지 건너왔다. **캡슐화**는 객체 내부의 데이터를 보호하고, 이를 안전하게 관리하기 위한 중요한 기법이다. 이를 통해 **프로그램의 안정성**을 높이고, **유지보수성**을 향상시킬 수 있다. 하나의 클래스가 마치 블랙박스처럼 동작하여, 내부 구현은 숨기고 필요한 인터페이스만 외부에 제공함으로써 **코드가 의도한 대로 동작하도록 보장**하는 것이 캡슐화의 핵심이다.  

비록 처음에는 다소 번거로울 수 있지만, **장기적으로 안정적이고 관리하기 쉬운 코드**를 작성하는 데 큰 도움이 된다.

<br>
<br>

# Reference
____
- https://wikidocs.net/16469
- https://modoocode.com/135

<br>
{{<alert>}}
<a href="https://elecbrandy.github.io/tags/opp"> 42cursus </a>
{{</alert>}}
<br>
