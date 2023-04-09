# Object
- '클래스'의 인스턴스
- 객체는 자신 고유의 속성이 있으며 클래스에서 정의한 행위를 할 수 있다

```swift
class SomeClass {
    var someProperty: Any = 1
}

class Main {
    var someClass: SomeClass
  
    init() {
        self.someClass = SomeClass() // 클래스의 인스턴스
    }
}
```
<br>

## * Instance
- 실제로 메모리에 할당되어 동작하는 모양을 갖춘 것
- '객체 != 인스턴스', '객체 == 클래스의 인스턴스'
- 구조체, 열거형의 인스턴스도 있을 수 있기 때문에 객체는 인스턴스 중에도 '클래스'의 인스턴스를 가리킨다
