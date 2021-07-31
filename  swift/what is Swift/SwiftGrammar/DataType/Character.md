### Character
> character는 말 그대로 '문자'를 의미합니다. 단어, 문장처럼 문자의 집합이 아닌 단 하나의 문자를 의미합니다. 스위프트는 유니코드 9 문자를 사용하므로 영어는 물론, 유니코드에서 지원하는 모든 언어 및 특수기호 등을 사용할수 있습니다. 문자는 표현하기 위해서는 값의 앞뒤에 큰따옴표를 사용하여 표현합니다.

```swift
let alphabetA : Character = "A"
print(alphabetA)

//Character 값에 유니코드 문잦를 사용할 수 있습니다.
let commandCharacter : Character = "🧡"
print(commandCharacter)

let 한글변수이름 : Character = "ㄱ"

//한글도 유니코드 문자에 속하므로 스위프트 코드의 변수 이름으로 사용할 수 있습니다.
print("한글의 첫 자음 : \(한글변수이름)")
```
