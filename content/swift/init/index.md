---
title: "생성자"
date: "january 24, 2023"
description : "생성자에 대하여 알아봅시다"
tags: ["swift"]
---
## Initiallizer 생성자
매서드 중 클래스 안 저장 속성을 초기화하는 함수 **생성자**  
클래스가 품고있는 속성들이 많아질 경우 사용시 일일히 초기화가 어려워 생성자를 사용  
속성을 옵셔널로 선언하면 값이 없을경우 nil로 표현이 가능하므로 init을 사용할 필요 X
### Self.
생성자가 파라미터로 받는 name과 price는 `self.name`를 초기화  
생성자 내부의 `self.name`는 Cake 클래스를 이용해 만든 해당 객체의 `var name`에 담긴다.  
blueCake 선언 시 init은 파라미터로 전달받은 `name: "블루케이크"`로 `self.name`을 초기화  
이때 `self.name`은 곧 `blueCake.name`이다. 
### Overloading
Overloading을 지원하므로, 클래스 안에 생성자를 맘대로맘대로 열매 먹은 것 마냥 생성할 수 있다. 장점은 개발자가 인스턴스를 만들 때 선택의 폭이 넓어진다는점? 
```swift
class Cake {
    var name: String
    //var name: String?
    var subname: String

    // 여러 저장 속성에 한가지 입력값을 넣을 수도 있고
    init(name: String) {
        self.name = name
        self.subname = name
    }
    // 한번에 다 받을 수도 있다.
    init(name: String, subname: String, price: Double) {
        self.name = name
        self.subname = subname
        self.price = price
    }
}
```
### init() 자동 구현
저장 속성의 기본값을 설정한 경우 스위프트에서 자동으로 `init`(생성자)를 구현  
`var buleCake = Cake()`는 사실 `var blueCake = Cake.init()`의 축약형
```swift
class Cake {
    var name: String = "블루케이크"
    var subname: String = "블루베리케이크" 
//  여기 숨어있지롱  
//  init() {
//        
//  }
}
var buleCake = Cake()
```
### Delegate up, across
**Delegate up**  
서브클래스의 지정생성자는 슈퍼클래스의 지정생성자를 반드시 호출해야함.  
**Delegate across**  
편의 생성자는 동일한 클래스에서 다른 편의생성자 또는 지정생성자를 호출해야함.
```swift
class A {
    var a: Int
    var b: Int
    
    init(a: Int, b: Int) {
        self.a = a
        self.b = b
    }
    convenience init() {
        self.init(a: 0, b: 0)
    }
}
class B: A {
    var c: Int
    
    init(a: Int, b: Int, c: Int) {
        self.c = c
        //self.a = a 또는 self.b = b 처럼
        //이때 여기서 A의 저장속성에 접근하는 것은 불가능하다.
        //왜냐? 아직 상위 클래스 A의 생성자를 호출하지 않아서
        //해당 메모리 셋팅이 되기 전이기 때문이다.
        super.init(a: a, b: b) // 상위 지정 생성자 호출
        //이 밑으로는 이제 A의 저장 속성에 접근이 가능하다.
        //self.a = 0 등
        //메서드도 운용 가능함
    }
}
```
##  클래스 생성자 Class Initiallizer
구조체는 메모리를 찾지 않고 그냥 스택에다가 차곡차곡 쌓아가지만,  
클래스의 경우 인스턴스를 만드는 경우 힙 영역에 비어있는 공간을 스캔해야하므로 구조체에 비해서 시간이 더 오래걸림 (동적할당)
### 지정 생성자
- _Designated Initiallizer_ 
- 지정 생성자는 모든 속성을 초기화 해야함!!  
- 일반적인 생성자를 지정 생성자라고 부르며, 그 범주 안에는 기본 생성자 `init()`도 포함
### 편의 생성자
- _Convenience Initiallizer_
- 편의 생성자는 모든 속성을 초기화 할 필요가 없고, 상속되지 않으며 서브클래스에서 재정의 불가! 
- 지정 생성자를 베이스로 가지며 (편의)생성자 내에서 지정 생성자를 호출하는 것이 특징!  
- 코드 중복을 줄여 유지보수가 쉬워지며 특히 클래스에서 상속 실수를 줄일 수 있음
- 생성자 중복을 없애고 편의 생성자를 통해 지정 생성자를 호출 = 국룰
```swift
class Cake {
    let name, subname: String
    //편의 생성자
    convenience init() {
        self.init(name: "블루케이크", subname: "블루베리케이크")
    }
    //편의 생성자
    convenience init(name: String) {
        self.init(name: name, subname: name)
    }
    //지정 생성자
    init(name: String, subname: String) {
        self.name = name
        self.subname = subname
    }
}
```
### 필수 생성자
- _Requried Initiallizer_
- 상위 클래스에 필수 생성자가 존재한다면, 하위 클래스에서 반드시 해당 생성자를 구현해야함!
- 단, 딱히 다른 지정생성자를 구현하지 않으면 자동으로 상속된다는거!
- 주로 애플이 미리 만들어놓은 프레임워크에 쓰인다는 점 유의합시당...
```swift
struct Cake {
    var price: Int
    required init(price: Int) {
        self.x = x
    }
}
```
> **UIView로 보는 필수 생성자**  
구현을 하지 않는다면  아래처럼 자동으로 상속. 해당 생성자는 UIView가 가지고 있는 init이겠죠? 
```swift
class AView: UIview {
//    required init?(coder: NSCoder) {
//        fatalError("init(coder:) has not been implemented")
//    }
}
```
그렇지만 아래처럼 하위 클래스인 AView에서 생성자 구현(재정의)이 발생한다면, 직접 써줘야하겠죠?
```swift
class AView: UIview {
    override init(frame: CGRect) {
        super.init(frame: frame)
    }
    //써줘야하겠죠?
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
}
```
### 실패가능 생성자
- _Requried Initiallizer_
- 인스턴스 생성에 실패해서 아에 삑나는 상황보다는, 실패할 수도 있는 가능성을 열어둔 생성자로 구조체/클래스/열거형 등에서 사용 가능함 (은 이름으로 override  불가능! )
- 실패가능 생성자를 정의하고 그에 따른 예외처리를 하는 것이 더 올바른 방법!
    - init 뒤에 ?를 붙여서 사용하며, 내부에 if문을 사용해서 실패할 경우 nil을 반환하기
```swift
class A {
    var a: Int
    init?(a: Int) {
        if a.isEmpty {
            return nil
        }
        self.a = 0
    }
}

let a = A(a: "James") //옵셔널
let a = A(a: "") //nil
```
> **실패가능 생성자 조건정리**
- 실패가 불가능한 생성자는 다른 실패가능 생성자를 호출할 수 없다.
![002_실패가능생성자1.png](./image/002_실패가능생성자1.png)
- Delegate across
    - 실패가능  -(호출)-> 실패불가능
    - 실패불가능 -(호출)-> 실패가능
![002_실패가능생성자2.png](./image/002_실패가능생성자2.png "002_실패가능생성자2.png")
- 실패 가능 범위가 실패 불가 범위보다 포괄적인 개념이기 때문
- 위 벤다이어그램에 따라 범위가 큰 곳에서 작은 곳으로 가는 2번은 가능하지만, 작은 곳에서 큰 곳으로 가는 1번은 불가능하다.
### 소멸자
- 인스턴스가 메모리에서 해제되기 직전에 정리가 필요한 내용을 구현하는 메서드
- 클래스 당 최대 1개의 소멸자를 정의할 수 있으며, 소멸자는 따로 파라미터를 사용하지 않음
```swift
class A {
    var a: Int
    
    deinit {
        
    }
}
var AAA: A? = A()
A = nil //A인스턴스 제거... 그리고 deinit
```

## 생성자의 상속과 재정의
생성자 상속… 넘모 어렵고 헷갈리지만 위에서 배운 Delegate up,down도 생각하면서  
1. **상위 클래스의 생성자를 고려하자!**
**상위 클래스의 지정생성자를 상속할 경우**
   - 하위클래스에서 지정 생성자로도 구현할 수 있다! (재정의)
   - 하위클래스에서 편의 생성자로도 구현할 수 있다! (재정의)
   - 반드시 구현할 필요는 없다...!  
**상위 클래스의 편의 생성자를 상속할 경우**
   - 호출불가가 원칙이므로 재정의 필요없음! 만약 동일한 이름이 구현되어있다면 그냥 새로 정의한거겠죠?
2. **현재 클래스의 생성자를 구현하자!**  
**지정 생성자 안에서는...**  
   - 나의 모든 저장 속성을 초기화 해야함!
   - 슈퍼 클래스의 지정 생성자 호출.. 해야겠지? Delegate up, across 유의  
**편의 생성자 안에서는**  
    - 현재 클래스의 지정 생성자 호출 해야함!
> 도식으로 정리해봄
![001.png](./image/001.png)

### 상속의 Case
클래스 A를 베이스로 하는 상속 케이스를 정리해보자  
클래스 A는 생성자가 없어보이지만 사실 자동으로 제공되는 init 기본형을 가지고 있다는 사실 유념
```swift
class A {
    var a: Int = 0
    // init() {} 기본 생성자 자동 제공!
}
```
> **[Case1]** 하위 클래스에서 **지정생성자**로 구현(재정의)해보자!  
```swift
class B: A {
    var c: Int
    
    override init() {
        self.c = 0
        super.init() //Delegate up
    }
}
```
> **[Case2]** 하위 클래스에서 **편의생성자**로 구현(재정의)해보자!  
```swift
class B: A {
    var c: Int
    
    override convenience init() {
        self.init(c:0) //Delegate acorss
    }
    
    init(c: Int) {
        self.c = c
        super.init() //Delegate up
    }
}
```
> **[Case3]** B클래스를 상속한 C클래스가 있다면 어떨까?  
B클래스를 보니 지정생성자 두개가 존재한다. `init()`, `init(c :Int)`  
이것들을 어떻게 상속할지 고민해보자. 지정? 편의? 아니면 상속 포기?
```swift
class C: B {
    var z: Int
    // 1. init()을 구현하자(재정의)
    override init() {
        self.z = 0
        self.init() //Delegate acorss
    }
    // 2. init(y: int)을 구현하자(재정의)
    override init(y: Int) {
        self.z = 0 //지정생성자의 조건. 모든 속성을 초기화해야하므로 z도 초기화
        super.init(y : y)
    }
    // 3. 요건 현재 클래스의 생성자를 구현하는 과정...
    init(z: Int) {
        self.z = z 
        super.init() //Delegate up
    }
}
```
### 생성자 상속 규칙 정리
1. 상위 클래스의 지정/편의 생성자를 현재 클래스(하위)에서 어떻게 구현할 것인가?
   - 지정생성자
        - 하위 클래스에서 지정 생성자로 구현한다
        - 하위 클래스에서 편의 생성자로 구현한다
        - 구현 안 할 수도 있음!
    - 편의 생성자
        - 재정의 하지않아도 되고, 동일이름이라면 그냥 새로 정의한 것임
2. 상위 관련 생성자를 구현했다면, 이제 현재 클래스의 생성자를 만들어야한다.
    - 지정생성자로 만들기
        - 현재 나의 모든 저장속성을 초기화
        - 상위 클래스(슈퍼)의 지정 생성자를 호출하기
    - 편의 생성자
        - 현재 클래스(동일)의 지정 생성자를 호출해야함…
> !!주의!! 예외사항
1. 지정 생성자 자동상속 - 저장속성의 기본값이 세팅되어있고 어떤 재정의도 안했을 때
2. 편의 생성자 자동상속 - 상위지정생성자를 모두 상속하는 경우
    - 위 지정생성자 모두를 자동상속하거나, 상위 지정생성자 모두 재정의하는 경우

### 생성자 상속
하위 클래스는 기본적으로 상위 클래스 생성자를 상속하지 않고 재정의하는 것이 원칙  
재정의는 동일한 이름을 가진 생성자를 구현하는 것이고, 하위클래스의 커스텀 생성자 구현 전에 (상위클래스의) 재정의 생성자를 작성해야 실수하지 않음.
- 상위 지정 생성자가 존재할 경우
    - 하위클래스에서 지정 생성자로 구현할 수도 있고 (재정의)
    - 하위클래스에서 편의 생성자로 구현할 수도 있고 (재정의)
    - 구현을 하지 않을 수도 있다. (재정의가 필수적인 것은 아님)
- 상위 편의 생성자가 존재할 경우
    - 재정의를 하지 않아도 되고, (호출불가가 원칙이라 재정의 제공 X)
    - 만약 동일한 이름을 구현했다면 그냥 새로 정의한 것임!

##  구조체 생성자
구조체는 지정 생성자와 실패가능 생성자를 가질 수 있음.

### 구조체 지정 생성자
- 다른 생성자를 호출하는 생성자를 선언하는 방식도 가능  
- 클래스에서 편의 생성자에 해당하며 구조체는 클래스와 달리 편의 생성자라는 개념이 없으니 그냥 지정 생성자  
- 전체적인 생성자를 하나 만들고, 다른 생성자에서 해당 생성자를 가져오는 그런 방법.
```swift
struct Cake {
    let name, subname: String
    
    init() {
        self.init(name: "블루케이크", subname: "블루베리케이크")
    }
    
    init(name: String) {
        self.init(name: name, subname: name)
    }
    
    init(name: String, subname: String, price: Double) {
        self.name = name
        self.subname = subname
        self.price = price
    }
}
var buleCake = Cake()
```

### Memberwise Initializer
- 구조체의 경우 맴버와이즈 이니셜라이저를 제공해주며 생성자를 딱히 적지 않아도 xcode에서 알아서 구현해냄  
- 생성자를 유저가 새로 만들면 더 이상 안해주는데, 이런 이유? 클래스보다 구조체를 더 많이 쓰니까 허들을 낮춰준게 아닐까?
```swift
struct Cake {
    var name: String
    var price: Double
//    여기 숨어있지롱 Xcode가 구현해주지롱.. 물론 당신이 새로 init을 생성하면 the end
//   init(name: String, subname: String, price: Double) {
//      self.name = name
//        self.subname = subname
//        self.price = price
//   }
}
//var blueCake = Cake(name: String, price: Double)
```