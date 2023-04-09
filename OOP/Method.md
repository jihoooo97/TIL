# Method
- 객체가 클래스에서 정의된 행위를 실질적으로 하는 함수
- 메서드를 통해 객체에 명령을 전달할 수 있다
- 객체 간에 명령 전달 또는 데이터 전달은 메서드를 통해 이루어지며 명령을 전달하거나 데이터르 전달하는 행위를 '메서드를 호출한다'라고 표현
<br><br><br>

```swift
class SomeClass {
    var someProperty: Any = 1
  
    func someMethod() {
        print(self.someProperty)
    }
}

class Main {
    var someClass: SomeClass
  
    init() {
        self.someClass = SomeClass()
        self.someClass.someMethod()  // 1
    }
}
```
