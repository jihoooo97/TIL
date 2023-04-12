# Float과 Double
- 부동소수점을 사용하는 실수이며, 부동소수 타입이다
- 정수 타입보다 훨씬 넓은 범위의 수를 표현할 수 있다
<br>

## Float
- 32bit의 부동소수 표현을 한다
- 64bit환경에서 최소 15자리의 십진수를 표현할 수 있다
<br>

## Double
- 64bit의 부동소수 표현을 한다
- 64bit환경에서 최소 6자리의 십진수를 표현할 수 있다
<br>

```swift
// Float이 수용할 수 있는 범위를 넘어선다
// 감당할 수 있는 범위 만큼 남기므로 정확도가 떨어진다
var floatValue: Float = 1234567890.1

let doubleValue: Double = 1234567890.1

floatValue = 123456.1
```
<br>
