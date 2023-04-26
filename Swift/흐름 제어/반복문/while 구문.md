# while 구문

### 일반적인 사용
<br>

```swift
var friends: [String] = ["A", "B", "C"]

while !friends.isEmpty {
    print("Good bye \(friends.removeFirst())")
}
// Good bye A
// Good bye B
// Good bye C
```
<br><br>
