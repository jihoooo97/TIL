# repeat-while 구문
> repeat 블록의 코드를 최초 1회 실행한 후, while 다음의 조건이 성립하면 블록 내부의 코드를 반복 실행합니다.

<br>

```swift
var friends: [String] = ["A", "B", "C"]

repeat {
    print("Good bye \(friends.removeFirst())")
} while !friends.isEmpty
// Good bye A
// Good bye B
// Good bye C
```
