---
title: "타입캐스팅"
date: "january 24, 2023"
description : "TypeCasting"
tags: ["swift"]
---
# 타입캐스팅 TypeCasting

## 인스턴스의 타입 검사
```swift
class Human {
    var hp = 100
}

class Wizard: human {
    // hp = 100
    var mana = 100
}

class Cleric: Wizard {
    // hp = 100
    // mana = 100
    var devine = 100
}
let Human1 = Human()
let Wizard2 = Wizard()
let Cleric3 = Cleric()
```
**Human** 클래스를 상속한 -  **Wizard** 클래스를 상속한 - **Cleric** 클래스가 있다고 생각해보자!
### is 연산자
- 타입을 검사하는 연산자! _Type check operator_
```swift
Human1 is Human
Human1 is Wizard
Human1 is Cleric

Wizard2 is Human
Wizard2 is Wizard
Wizard2 is Cleric

Cleric3 is Human
Cleric3 is Wizard
Cleric3 is Cleric
```

### as 연산자
- 타입 검사를 수행하는 연산자로, 참이면 True - 거짓이면 False를 반환!

