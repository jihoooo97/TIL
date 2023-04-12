# String
> 문자열
<br>

```swift
let name: String = "Jiho"

// 이니셜라이저를 사용하여 빈 문자열을 생성할 수 있다
var introduce: String = String()

// append() 메서드를 사용하여 문자열을 이어붙일 수 있다
introduce.append("제 이름은")

// + 연산자를 통해서 문자열을 이어붙일 수 있다
introduce = introduce + " " + name + "입니다."

print("name의 글자 수: \(name.count)") // 4
print("introduce가 비어있나요?: \(introduce.isEmpty)") // false

// 유니코드의 스칼라값을 사용하면 값에 해당하는 표현이 출력된다
let unicodeScalarValue: String = "\u{2665}"
```
<br>

## 다양한 기능
```swift
let hello: String = "Hello"
let jiho: String = "Jiho"
var greeting: String = "hello"
```
<br>

### 1. 연산자를 통한 문자열 결합
```swift
greeting += " "
greeting += jiho
greeting += "!"
print(greeting) // hello Jiho!
```
<br>

### 2. 연산자를 통한 문자열 비교
```swift
print(hello == "Hello") // true
print(hello == "hello") // false
```
<br>

### 3. 메서드를 통한 접두어, 접미어 확인
```swift
print(hello.hasPrefix("He"))  // true
print(hello.hasPrefix("he"))  // false
print(hello.hasSuffix("He"))  // false
print(hello.hasSuffix("llo")) // true
```
<br>

### 4. 메서드를 통한 대소문자 변환
```swift
ar convertedString: String = ""

convertedString = hello.uppercased()
print(convertedString) // HELLO

convertedString = hello.lowercased()
print(convertedString) // hello
```
<br>

### 5. 프로퍼티를 통한 빈 문자열 확인
```swift
greeting = "헤헷 빈 문자열일까요?"
print(greeting.isEmpty) // false

greeting = ""
print(greeting.isEmpty) // true
```
<br>

### 6. 프로퍼티를 통한 빈 문자열 확인
```swift
print(greeting.count) // 0
```
<br>

### 7. 코드상에서 여러 줄의 문자열의 직접 쓰고 싶다면
"""  
내용  
"""  
식으로 작성하면 된다
```swift
greeting = """
안녕하세요
세줄로
요약해보겠습니다
"""
```
<br>
