### Int 와 UInt 
> 정수 타입입니다.

- Int 는 +, - 부호를 포함한 정수
- UInt 는 - 부호를 포함하지 않는 0을 포함한 양의 정수

Int 와 UInt 타입의 최댓값과 최솟값은 각각 max 와 min 프로퍼티로 알아볼 수 있습니다. Int와 UInt는 각각 8비트, 16비트, 32비트, 64비트의 형태가 있습니다. 즉, Int8, Int16, Int32, Int64, UInt8, UInt16, UInt32, UInt64 등으로 저장할 수 있는 데이터 타입의 크기에 따라 타입이 분리되어 있습니다. 시스템 아키텍처에 따라 Int 와 UInt의 타입이 달라집니다. 32비트 아키텍처에서는 Int32가 Int 타입으로, UInt32 가 UInt타입을 지정됩니다. 그리고 64비트 아키텍처에서 Int64가 Int 타입으로, UInt64가 UInt 타입으로 지정됩니다.

```swift
var integer : Int = -100       // Int형 선언
let unsignedInteger: UInt = 50 // UInt형 선언 (음수 값을 할당 할 수 없다.)
```
##### 진수표현법

- 10진수 : 우리가 평소에 쓰던 숫자와 동일하게 작성하면 됩니다.
- 2진수  : 접두어 0b를 사용하여 표현합니다.
- 8진수  : 접두어 0o를 사용하여 표현합니다.
- 16진수 : 접두어 0x를 사용하여 표현합니다.

사용법
```swift
let decimalInteger : Int = 28
let binaryInteger : Int = 0b11100
let octalInteger : Int = 0o34
let hexadecimalInteger : Int = 0x1c
```