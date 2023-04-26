# Switch 구문
- 소괄호 생략이 가능하다
- break 키워드 생략이 가능하다  
  -> case 내부의 코드를 모두 실행하면 break 없이도 switch 구문 종료  
  -> case를 연속 실행하던 트릭 사용 불가(`fallthrough` 키워드 사용)
- 조건에 다양한 값이 들어갈 수 있다
- 비교될 값이 명확히 한정적인 값(열거형 등)이 아닐 때는 `default`를 꼭 작성해줘야 한다
- 각 case에 `범위 연산자`, `where 절`을 사용하여 조건을 확장할 수 있다

```swift
let integerValue: Int = 5

switch integerValue {
case 0:
    print("zero")
case 1...10:
    print("1 ~ 10")
    fallthrough
case Int.min..<0, 101..<Int.max:
    print("< 0, > 100")
default:
    print("> 10, <= 100)
}
```
<br><br>
  
### switch 구문의 입력 값으로 숫자 표현이 아닌 문자, 문자열, 열거형, 튜플, 범위, 패턴이 적용된 타입 등 다양한 타입의 값도 사용 가능하다

```swift
let stringValue: String = "jiho"

switch stringValue {
case "jisoo":
    print("She is Jisoo")
case "miyeon":
    print("She is Miyeon")
case "haesun", "jenny":
    print("She is \(stringValue)")
default:
    print("It's my name")
}
```
<br>


### Tuple 값
```swift
typealias NameAge = (name: String, age: Int)

let tupleValue: NameAge = ("Jiho", 27)

switch tupleValue {
case ("jiho", 27):
    print("good")
case ("jiho", _):
    print("이름만 맞았음. 나이: \(tupleValue.age)")
case (_, 27):
    print("나이만 맞음. 이름: \(tupleValue.name)")
default:
    print("hello")
}

switch tupleValue {
case ("jiho", 27):
    print("good")
case ("jiho", let age):
    print("이름만 맞았음. 나이: \(age)")
case (let name, 27):
    print("나이만 맞음. 이름: \(name)")
default:
    print("hello")
}
```
<br>

### where
```swift
let 직급: String = "사원"
let 연차: Int = 1
let 인턴여부: Bool = false

switch 직급 {
case "사원" where 인턴여부 == true:
    print("인턴이에요 헤헷")
case "사원" where 연차 < 2 && 인턴여부 == false:
    print("신입이에요 헤헷")
case "사원" where 연차 > 5:
    print("좀 오래된 사원이에요 허허")
case "사원":
    print("사원이에요 헤헷")
case "대리":
    print("대리입니다 껄껄")
default:
    print("찾지마세요")
}
```
<br>

### enum
```swift
enum Developer {
    case android, ios, web, backend
}

let 포지션: Developer = .ios

switch 포지션 {
case .android:
    print("멋있는 android")
case .ios:
    print("킹갓 ios")
case .web:
    print("활발한 web")
case .backend:
    print("과묵한 backend")
@unknown default:  // 추후에 추가될 수 있는 case에 대비하여 경고
    print("누구세요..?")
}
```