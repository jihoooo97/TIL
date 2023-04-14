# Enum
> 연관된 항목들을 묶어서 표현할 수 있는 타입
- Array나 Dictionary 같은 타입과 다르게 개발자가 정의한 항목 값 외에는 추가/수정이 불가능
- Swift의 열거형은 항목별로 값을 가질 수도, 가지지 않을 수도 있다
- Swift의 열거형은 각 열거형이 고유의 타입으로 인정된다
- 열거형 각 항목이 `원시 값(Raw Value)` 이라는 형태로 실제 값을 가질 수 있다
- `연관 값(Associated Values)` 을 사용하여 다른 언어에서 공용체라 불리는 값의 묶음도 구현할 수 있다  
<br>

## 사용
  - 제한된 선택지를 주고 싶을 때
  - 정해진 값 외에는 입력받고 싶지 않을 때
  - 예상된 입력 값이 한정되어 있을 때  
<br>

## 기본 열거형
- Developer라는 이름을 갖는 열거형에는 android, ios, web, backend라는 항목이 있다  
- 각 항목은 그 자체가 고유의 값이며, 한 줄에 모두 표현해 줄 수도 있다  

```swift
enum Developer {
    case android
    case ios
    case web
    case backend
}

enum Developer {
    case android, ios, web, backend
}
```
<br>

- 열거형 변수를 생성하고 값을 할당할 수 있다

```swift
var position: Developer = Developer.android
var position: Developer = .android

position = .ios
```
<br><br>

## 원시값
- 열거형의 각 항목은 자체로도 하나의 값이지만, 항목의 `원시 값(Raw Value)` 도 가질 수 있다  
  -> 특정 타입으로 지정된 값을 가질 수 있다
- 원시 값을 사용하고 싶다면 `rawValue` 라는 프로퍼티를 통해 가져올 수 있다

```swift
enum Developer: String {
    case android = "android 개발자"
    case ios = "iOS 개발자"
    case web = "web 개발자"
    case backend = "backend 개발자"
}

let position: Developer = Developer.ios
print("저의 개발 포지션은 \(position.rawValue)입니다")
// 저의 개발 포지션은 iOS 개발자입니다


enum WeekDays: Character {
    case mon = "월"
    case tue = "화"
    case wed = "수"
    case thu = "목"
    case fri = "금"
    case sat = "토"
    case sun = "일"
}

let today: WeekDay = .fri
print("오늘은 \(today.rawValue)요일입니다")
// 오늘은 금요일입니다
```
<br><br>

- 일부 항목만 원시 값을 줄 수도 있다
- String 타입이라면 각 항목 이름을 그대로 원시값으로 갖게된다
- Int 타입이라면 첫 항목을 기준으로 0부터 1씩 늘어난 값을 갖는다
   
```swift
enum Developer: String {
    case android = "android 개발자"
    case ios = "iOS 개발자"
    case web
    case backend
}

let position: Developer = .backend
print("저의 개발 포지션은 \(position.rawValue)입니다") // 저의 개발 포지션은 backend입니다
print(Developer.ios.rawValue) // iOS 개발자


enum Numbers: Int {
    case zero
    case one
    case two
    case ten = 10
}

print("\(Numbers.zero.rawValue), \(Numbers.one.rawValue), \(Numbers.two.rawValue), \(Numbers.ten.rawValue)")
// 0, 1, 2, 10
```
<br><br>

- 열거형이 원시 값을 갖는 열거형일 때, 열거형의 원시 값 정보를 안다면 원시 값을 통해  
  열거형 변수 또는 상수를 생성할 수 있다
- 올바르지 않은 원시 값을 통해 상성하려 한다면 nil을 반환한다

```swift
let ios = Developer(rawValue: "iOS 개발자")    // ios
let html = Developer(rawValue: "HTML 개발자")  // nil
```
<br><br>


## 연관 값
- Swift의 열거형 각 항목이 연관 값을 가지게 되면, 공용체 형태를 띌 수 있다
- 열거형 내의 항목(case)이 자신과 연관된 값을 가질 수 있다
- 연관 값은 각 항목 옆에 소괄호로 묶어 표현할 수 있다
- 모든 항목이 연관 값을 가질 필요는 없다

```swift
enum PastaTaste {
    case cream, tomato
}

enum PizzaDough {
    case cheeseCrust, thin, original
}

enum PizzaTopping {
    case pepperoni, cheese, bacon
}

enum MainDish {
    case pasta(taste: PastaTaste)
    case pizza(dough: PizzaDough, topping: PizzaTopping)
    case chicken(withSauce: Bool)
    case rice
}

var dinner: MainDish = .pasta(taste: PastaTaste.cream)
dinner = .pizza(dough: .cheeseCrust, topping: .bacon)
dinner = .chicken(withSauce: true)
dinner = .rice
```
<br><br>


## 항목 순회
- `CaseIterable` 프로토콜을 채택해준 뒤 `allCases` 라는 프로퍼티를 통해  
  모든 케이스의 컬랙션을 생성할 수 있다
  
```swift
enum Developer: CaseIterable {
    case android
    case ios
    case web
    case backend
}

let allCases: [Developer] = Developer.allCases
print(allCases) 
// Developer.android, Developer.ios, Develiper.web, Developer.backend
```
<br><br>

- `available` 속성을 통해 플랫폼별로 사용 조건을 추가하는 경우 등 복잡해지는 열거형이 있다

```swift
enum Developer: String, CaseIterable {
    case android = "android 개발자"
    case ios = "iOS 개발자"
    case web = "web 개발자"
    case backend = "backend 개발자"
    @available(iOS, obsoleted: 15.0)
    case ai = "AI 개발자"

    static var allCases: [Developer] {
        let all: [Developer] = [.android,
                                .ios,
                                .web,
                                .backend]
        #if os(iOS)
        return all
        #else
        return all + [.graduate]
        #endif
    }

    let allCases: [Developer] = Developer.allCases
    print(allCases)
}
```
<br><br>

- 열거형의 케이스가 연관 값을 갖는 경우 매우 복잡해진다

```swift
enum PastaTaste: CaseIterable {
    case cream, tomato
}

enum PizzaDough: CaseIterable {
    case cheeseCrust, thin, original
}

enum PizzaTopping: CaseIterable {
    case pepperoni, cheese, bacon
}

enum MainDish: CaseIterable {
    case pasta(taste: PastaTaste)
    case pizza(dough: PizzaDough, topping: PizzaTopping)
    case chicken(withSauce: Bool)
    case rice
    
    static var allCases: [MainDish] {
        return PastaTaste.allCases.map(MainDish.pasta)
        + PizzaDough.allCases.reduce([]) { (result, dough) -> [MainDish] in
            result + PizzaTopping.allCases.map { topping -> MainDish in
                MainDish.pizza(dough: dough, topping: topping)
            }
        }
        + [true, false].map(MainDish.chicken)
        + [MainDish.rice]
    }
}

print(MainDish.allCases.count) // 14
print(MainDish.allCases)       // 모든 경우의 연관 값을 갖는 케이스 컬렉션
```
<br><br>


## 순환 열거형
- 열거형 항목의 연관 값이 열거형 자신의 값이고자 할 때 사용한다
- 순환 열거형을 명시하고 싶다면 `indirect` 키워드를 사용한다
- 특정 항목에만 한정하고 싶다면 case 키워드 앞에 `indirect` 를 붙이고,   
  전체에 적용하고 싶다면 enum 키워드 앞에 붙인다
- `indirect` 키워드는 이진 탐색 트리 등의 순환 알고리즘을 구현할 때 유용하게 사용한다

```swift
enum ArithmeticExpression {
    case number(Int)
    indirect case addition(ArithmeticExpression, ArithmeticExpression)
    indirect case multiplication(ArithmeticExpression, ArithmeticExpression)
}

indirect enum ArithmeticExpression {
    case number(Int)
    indirect case addition(ArithmeticExpression, ArithmeticExpression)
    indirect case multiplication(ArithmeticExpression, ArithmeticExpression)
}


let five = ArithmeticExpression.number(5)
let four = ArithmeticExpression.number(4)
let sum = ArithmeticExpression.addition(five, four)
let final = ArithmeticExpression.multiplication(sum, ArithmeticExpression(number(2)))

func evaluate(_ expression: ArithmeticExpression) -> Int {
    switch expression {
        case let .number(value):
            return value
        case let .addition(left, right):
            return evaluate(left) + evaluate(right)
        case let .multiplication(left, right):
            return evaluate(left) * evaluate(right)
    }
}

let result: Int = evaluate(final)
print("(5 + 4) * 2 = \(result)")  // (5 + 4) * 2 = 18
```
<br><br>


## 비교 가능한 열거형
- `Comparable` 프로토콜을 준수하는 연관 값만 갖거나 연관 값이 없는 열거형은 `Comparable` 프로토콜을 채택하면 각 케이스를 비교할 수 있다
- 앞에 위치한 케이스가 더 작은 값이 된다

```swift
enum Condition: Comparable {
    case terrible
    case bad
    case good
    case great
}

let myCondition: Condition = .great
let yourCondition: Condition = .bad

if myCondition >= yourCondition {
    print("제 상태가 더 좋네요")
} else {
    pirnt("당신의 상태가 더 좋네요")
}
// print("제 상태가 더 좋네요")


enum Device: Comparable {
    case iPhone(version: String)
    case iPad(version: String)
    case macBook
    case iMac
}

var devices: [Device] = []
devices.append(.iMac)
devices.append(.iPhone(version: "16.3"))
devices.append(.iPhone(version: "13.1"))
devices.append(.iPad(version: "15.2"))
devices.append(.macBook)

let sortedDevices: [Device] = devices.sorted()
print(sortedDevices)
// [Device.iPhone(version: "13.1"), Device.iPhone(version: "16.3"), Device.iPad(version: "15.2"), Device.macBook, Device.iMac]
```
<br><br>