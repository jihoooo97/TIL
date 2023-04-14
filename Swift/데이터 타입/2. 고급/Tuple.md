# Tuple
> 타입의 이름이 따로 지정되어 있지 않은, 개발자가 마음대로 만드는 타입이다
- C언어 원시 구조체의 형태와 가깝다
- Python의 튜플과 유사하다
- 타입 이름이 따로 없으므로 일정 타입의 나열만으로 튜플 타입을 생성할 수 있다
- 튜플에 포함될 데이터의 개수는 자유롭게 정할 수 있다
<br>

### String, Int, Double 타입을 갖는 튜플
```swift
var person: (String, Int, Double) = ("Jiho", 27, 178.5)

// index를 통해 값을 할당할 수 있다
person.1 = 28
person.2 = 182.5

// index를 통해 값을 빼 올 수 있다
print("이름: \(person.0), 나이: \(person.1), 키: \(person.2)")
```
<br>

### 가독성을 위해 튜플의 요소에 이름을 붙여줄 수 있다
```swift
var person: (name: String, age: Int, height: Double) = ("Jiho", 27, 178.5)

// index 또는 이름을 똥해 값을 할당할 수 있다
person.age = 28
person.2 = 182.5

// index 또는 이름을 통해 값을 빼 올 수 있다
print("이름: \(person.name), 나이: \(person.2), 키: \(person.height)")
```
<br>

### 튜플에 별칭을 지정하여 사용할 수 있다
```swift
typealias PersonTuple = (name: String, age: Int, height: Double)

var person: PersonTuple = ("Jiho", 27, 178.5)

person.age = 28
person.2 = 182.5

print("이름: \(person.name), 나이: \(person.2), 키: \(person.height)")
```
<br>
