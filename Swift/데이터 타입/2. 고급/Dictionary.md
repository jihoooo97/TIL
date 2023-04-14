# Dictionary
> 요소들이 순서 없이 키와 값의 쌍으로 구성되는 컬렉션 타입
- 딕셔너리에 저장되는 값은 항상 키와 쌍을 이루게 되는데, 키가 하나이거나 여러 개일 수 있다
- 하나의 딕셔너리 안의 키는 같은 이름을 중복해서 사용할 수 없다 -> 키는 값을 대변하는 유일한 식별자가 된다
- 대괄호로 `키`와 `값`의 타입 이름의 쌍을 묶어 딕셔너리 타입임을 표현한다
<br>

```swift
// 키는 String, 값은 Int 타입인 빈 딕셔너리를 생성한다
var numberForName: Dictionary<String, Int> = Dictionary<String, Int>()
var numberForName: [String: Int] = [String: Int]()
```
<br><br>

- typealias를 통해 조금 더 단순하게 표현할 수 있다
```swift
typealias StringIntDictionary = [String: Int]
var numberForName: StringIntDictionary = StringIntDictionary()
```
<br><br>

- 딕셔너리 키와 값을 명시해줬다면 [:]만으로도 빈 딕셔너리를 생성할 수 있다
```swift
var numberForName: [String: Int] = [:]
```
<br><br>

- 초깃값을 주어 생성할 수 있다
```swift
var numberForName: [String: Int] = ["jiho": 27, "miyeon": 27, "haesun": 35]

print(numberForName.isEmpty) // false
print(numberForName.count)   // 3
```
<br><br>

- 딕셔너리는 각 값에 키로 접근할 수 있다
- 딕셔너리 내부에서 키는 유일하지만 값은 유일하지 않다
- 배열과 다르게 딕셔너리 내부에 없는 키로 접근해도 오류가 발생하지 않고 nil을 반환한다
```swift
print(numberForName["miyeon"]) // 27
print(numberForName["suzy"])   // nil

numberForName["jiho"] = 28
// ["jiho": 28, "miyeon": 27, "haesun": 35]

print(numberForName["jiho"]) // 28

numberForName["max"] = 999 // [키: max, 값: 999]인 요소를 무작위 순서로 추가한다
// ["jiho": 27, "miyeon": 27, "max": 999, "haesun": 35]
```
<br><br>

- 특정 키에 해당하는 값을 제거하려면 removeValue(forKey:) 메서드를 사용한다
- 특정 키에 해당하는 값이 없으면 기본값을 돌려주도록 할 수 있다
```swift
print(numberForName.removeValue(forKey: "jiho")) // 28
print(numberForName.removeValue(forKey: "jiho")) // nil
print(numberForName["jiho", default: 0]) // 0
```
<br>