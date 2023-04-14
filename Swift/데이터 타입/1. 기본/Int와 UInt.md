# Int와 UInt
> 정수 타입
- 8bit, 16bit, 32bit, 64bit 등으로 저장할 수 있는 데이터의 크기에 따라 타입이 분리되어 있다
- 시스템 아키텍처에 따라 32bit 아키텍처에서는 Int32가 Int 타입으로, UInt32가 UInt 타입으로 지정된다

<br>

## Int
> +, - 부호를 포함한 정수
<br>

## UInt
> 부호를 포함하지 않는 0을 포함한 양의 정수
<br>

### 코드 예제
```swift
var integer: Int = -100
let unsignedInteger: UInt = 50

let largeInteger: Int64 = Int64.max
let smallUnsignedInteger: UInt8 = UInt8.max

let tooLarge: Int = Int.max + 1 // [error] overflow
let cannotBeNegetive: UInt = -5 // [error] UInt는 음수가 될 수 없음

integer = unsignedInteger // [error] Swift에서 Int와 UInt는 다른 타입
integer = Int(unsignedInteger) // [error] Int타입의 값으로 할당해줘야 함 Int의 범위를 넘어가면 overflow 발생
```
<br>

### 진수에 따른 정수 표현
| 진수 |표현|
|:-:|:-:|
| 10진수 | 평소에 쓰는 숫자 |
| 2진수 | 접두어 0b 사용 |
| 8진수 | 접두어 0o 사용 |
| 16진수 | 접두어 0x 사용 |
<br>

```swift
// 10진수
let decimalInteger: Int = 28

// 2진수
let binaryInteger: Int = 0b11100

// 8진수
let octalInteger: Int = 0o34

// 16진수
let hexadecimalInteger: Int = 0x1C
```
<br>
