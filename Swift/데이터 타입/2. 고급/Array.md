# Array
> 배열은 같은 타입의 데이터를 일렬로 나열한 후 순서대로 저장하는 형태의 컬렉션 타입이다
- 각기 다른 위치에 같은 값이 들어갈 수도 있다
- `버퍼(Buffer)`이며, 필요에 따라 자동으로 버퍼의 크기를 조절해준다  
  -> 요소의 삽입 및 삭제가 자유롭다
<br>

```swift
// 대괄호를 사용하여 배열을 표현할 수 있다
var names: Array<String> = ["jiho", "chulsoo", "younghee", "jiho"]

// 위의 코드와 동일한 표현
var names: [String] = ["jiho", "chulsoo", "younghee", "jiho"]

var emptyArray: [Any] = [Any]()
var emptyArray: [Any] = Array<Any>()

// 배열의 타입을 명시해줬다면 []로 빈 배열을 생성할 수 있다
var emptyArray: [Any] = []
print(emptyArray.isEmpty) // true
print(names.count)        // 4
```
<br>

- 각 요소에 index를 통해 접근할 수 있다
- index는 0부터 시작하며, 잘못된 index로 접근하려하면 익셉션 오류(Exception Error)가 발생한다
```swift
names[2] = "babo" // ["jiho", "chulsoo", "babo", "jiho"]
print(names[2])   // babo
print(names[4])   // [error] index 범위를 벗어남
```
<br>

- 맨 처음과 맨 마지막 요소는 first와 last 프로퍼티를 통해 가져올 수 있다
- firstIndex(of:) 메서드를 사용하면 해당 요소의 인덱스를 알아낼 수 있다  
  -> 중복된 요소가 있다면 제일 첫 번째 index를 반환
```swift
print(names.first)                  // jiho
print(names.last)                   // jiho
print(names.firstIndex(of: "jiho")) // 0
print(names.firstIndex(of: "son"))  // nil
```
<br>

- 맨 뒤에 요소를 추가하고 싶다면 append(_:) 메서드를 사용한다
- 중간에 요소를 삽입하고 싶다면 inser(_: at:) 메서드를 사용한다
- 요소를 삭제하고 싶다면 remove(_:) 메서드를 사용한다
```swift
names.append("jisoo") 
// ["jiho", "chulsoo", "babo", "jiho", "jisoo"]

names.append(contentsOf: ["suzy", "miyeon"])
// ["jiho", "chulsoo", "babo", "jiho", "jisoo", "suzy", "miyeon"]

names.insert("haesun", at: 2)
// ["jiho", "chulsoo", "haesun", "babo", "jiho", "jisoo", "suzy", "miyeon"]

let firstItem: String = names.removeFirst() // jiho
// ["chulsoo", "haesun", "babo", "jiho", "jisoo", "suzy", "miyeon"]

let lastItem: String = names.removeLast() // miyeon
// ["chulsoo", "haesun", "babo", "jiho", "jisoo", "suzy"]

let zeroItem: String = names.remove(at: 0) // chulsoo
// ["haesun", "babo", "jiho", "jisoo", "suzy"]
```
<br>

- 범위 연산자를 통해 배열의 일부 요소만 가져오거나 요소를 바꿀 수 있다
```swift
names[1...3] = ["I", "Love", "You"]
// ["haesun", "I", "Love", "You", "suzy"]

print(names[1...3]) // ["I", "Love", "You"]
print(names[1...])  // ["I", "Love", "You", "suzy"]
print(names[...3])  // ["haesun", "I", "Love", "You"]
```
<br>