# Object
- 클래스의 인스턴스(instance - 실제로 메모리에 할당되어 동작하는 모양을 갖춘 것)
- 객체는 자신 고유의 속성이 있으며 클래스에서 정의한 행위를 할 수 있다

```swift
class SomeClass {
  var someProperty: Any = 1
}

class Main {
  var someClass: SomeClass // 객체
  
  init() {
    self.someClass = SomeClass() // 클래스의 인스턴스
  }
}
```
