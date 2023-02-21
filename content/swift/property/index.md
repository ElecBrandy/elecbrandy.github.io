---
title: "저장속성"
date: "january 24, 2023"
description : "Property"
tags: ["swift"]
---
# 저장속성 Property
## 1. 저장 속성
메모리 공간을 가지고 값을 저장할 수 있는 속성.
Class Cake의 저장속성은 `var name`, `var price` !
```swift
class Cake {
    var name: String
    lazy var price: Double = 0.1

    init (a:String) {
        name = a
    }
}
```
 
## 2. 지연 저장 속성(Lazy Stored Properties)
속성의 초기화를 지연시키는 것으로, 해당 속성은 제외한 상태로 진행하다가 후에 접근 시 초기화하는 것임. 나중에 변화가 생기는 것이므로 `var` 로 선언해야며 미리 초기화 해두어야하는 것이 포인트! 지연 저장 속성 운용 시 생성자 안에서는 따로 값 설정을 해주지 않아야 함. 메모리 관리와 다른 속성을 이용(의존)해야하는 경우 사용한다!
```swift
lazy var price: Double = 0.1
```
## 3. 계산 속성
계산속성은  실질적으로 함수이며 get 속성과 set 속성으로 나누어진다.
두가지 매서드를 한번에 구현할 수 있으며, 결국 속성의 탈을 쓴 매서드임!
addScore는 score에 의존한다.
```swift
class score {
    var score: Int = 0
    
    var addScore: Int {
        get {
            return score + 100
        }
        set(newValue) {
            self.score = score + newValue
        }
    }
}

var peter = scoreCal()
peter.score = 100
peter.addScore //200

peter.addScore = 500
peter.score //600

```
### get
get은 값을 얻는 것.
`peter.score` 실행 시 내부의 get으로 들어가 `score + 100` 값을 리턴한다.
set과 함께 쓰이지 않을 경우 get 블록으로 감싸지 않아도 괜찮다!
```swift
class score {
    var score: Int = 0
    
    var addScore: Int {
            return score + 100
    }
}
```

### set
set은 값을 세팅하는 것.
get이 정해진 과정을 수행한다면 set은 사용자가 외부에서 값을 세팅하는 과정을 수행하며
`peter.addScore=500`의 의미는  `peter.score = score + 500` 을 의미한다.
파라미터는 `newVaule`로 사용하기로 애플과의 약속이다 :) 또한 생략도 가능하다.
```swift
class score {
    var score: Int = 0
    
    var addScore: Int {
        get {
            return score + 100
        }
        set {
            self.score = score + newValue
        }
    }
}
```
## 4. 타입 속성
모든 인스턴스가 공통적으로 가져야하는 속성의 경우 사용한다.
클래스, 구조체 등에 모두 사용가능하며, 접근 시 인스턴스가 아닌 클래스 원본에 접근해야 알아낼 수 있다. 따로 Student()를 사용해 인스턴스 생성을 하지 않아도 접근할 수 있다!
init(생성자)을 통해 따로 초기화하는 과정이 없으므로 선언시 무조건 초기값을 지정해주어야한다.
### 저장 타입 속성
활용 방법에 있어서는 `static var count: Int = 0`으로 타입속성을 초기화하고, init 구문 안에 `Student.count += 1`을 통해서 Student로 만들어진 인스턴스의 총 갯수를 샐 수 있다.
```swift
class Student {
    static let standing: String = "학생"
    static var count: Int = 0 //인스턴스를 몇개 찍어냈는지 확인
    
    var name: String
    
    init(name:String, score: Int) {
        self.name = name
        self.score = score
        Student.count += 1 // 타입 속성의 활용
    }
}

let student = Student(name: "길동", score: 60)

student.name //길동
student.score //60

//타입속성 접근 시 (static에 접근 시)
Student.standing
//student.standing 은 에러 발생

```
### 계산 타입 속성
계산 타입 속성의 경우 static 사용시 상속에서 재정의가 불가능하지만, class 사용시 재정의가 가능하다.
```swift
class Student {
    static let standing: String = "학생"
    static let score: Int = 0
    
    //계산 타입 속성 예시
    static var plusScore: Int {
        return score + 100
    }
    
    //상속 재정의가 가능
    class var pulsScore2: Int {
        return score +100
    }
}
```

## 5. 속성 감시자
저장 속성과 속성의 변화를 감시하는 매서드이며, 저장 속성이 변경되면 호출된다.
계산 속성에도 사용 가능하나, 상속해서 재정의하는 경우에만 가능하다. 사실 계산 속성의 경우 set 블록에서 속성의 변화를 감지할 수 있으므로… 속성감시자는 저장 속성에 자주 쓰인다고만 알아두자.
```swift
class Student {
    var name: String = "이름"
    
    //저장속성과 해당 속성이 변하는 시점을 관찰하는 매서드
    var status: String = "재학생" {
        willSet(newValue) {
            print("\(name) 학생 : \(status)에서 \(newValue)로 변경 예정")
        }
        didSet(oldValue) {
            print("\(name) 학생 : \(oldValue)에서 \(status)로 변경 완료")
        }
    }
    init(name: String) {
        self.name = name
    }
}

let std01 = Student(name: "길동")

std01.status = "졸업생" 
// 길동 학생 : 재학생에서 졸업생으로 변경예정 
// 길동 학생 : 재학생에서 졸업생으로 변경예정
```
### willset
willset은 메모리 변경(저장 속성 변경) 직전에 호출된다.
따라서 파라미터로 받는 정보는 메모리 변경 전 기본 세팅 값 되시겠다.
기본적으로 newValue 파라미터를 사용하며 생략 또한 가능하다.
```swift
        willSet {
            print("\(name) 학생 : \(status)에서 \(newValue)로 변경 예정")
        }
```
### didSet
didSet은 메모리 변경(저장 속성 변경) 직후에 호출된다.
따라서 파라미터로 받는 정보 또한 메모리 변경 이후 값 되시겠다.
기본적으로 oldValue 파라미터를 사용하며 생략 또한 가능하다.
```swift
        didSet {
            print("\(name) 학생 : \(oldValue)에서 \(status)로 변경 완료")
        }
```