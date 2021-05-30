## 기본 명명 규칙 
> 모든 프로그래밍 언어가 그렇듯 스위프트 언어 자체에 명시된 명명 규칙은 없습니다. 명명 규칙은 프레임워크나 코딩 환경 또는 협업 그룹마다 달라질 수 있습니다. 물론 언어에 따라서 권장하는 명명법이나 코딩 규칙이 있기도 합니다.

<br>

>애플은 스위프트 관련 문서 및 예제를 모두 스위프트의 [<API 디자인 가이드라인>](https://swift.org/documentation/api-design-guidelines) 및 애플의 [<코코아를 위한 코딩 가이드라인>](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html)에 따라 작성했습니다. 이 책에서도 이 가이드라인에 따라 변수, 상수, 열거형, 함수, 클래스, 구조체, 메서드, 프로토콜 등을 명명하려 합니다. 자세한 명명 규칙은 스위프트의 API디자인 가이드 라인 및 애플의 공식 문서를 참고하세요. 코딩은 습관이라 나중에 교정하기 어려우니 처음부터 제대로 된 코딩 규칙 및 명명 규칙을 익히도록 노력하는 것이 좋습니다.

<br>

다음은 가이드라인 중에서 꼭 알아야 할 기본 명명 규칙입니다.

- 변수, 상수, 함수, 메서드 타입 등의 이름은 유니코드에서 지원하는 어떤 문자(한글, 한자, 영문, 숫자, 이모티콘 등등)라도 사용할 수 있습니다. 다만 다음과 같은 예외 경우는 사용할 수 없습니다.
  - 스위프트에서 미리 정한 예약어 또는 키워드
  - 해당 코드 범위 내에서 미리 사용되는 기존 이름과 동일한 이름
  - 연산자로 사용될 수 있는 기호(+,-,*,/)
  - 숫자로 시작하는 이름
  - 공백이 포함된 이름
- 함수, 메서드, 인스턴스 이름은 첫 글자를 소문자로 사용하는 소문자 카멜케이스(Lower Camel Case)를 사용합니다.
- 클래스, 구조체, 익스턴스, 프로토콜, 열거형 이름은 타입의 이름이기 때문에 첫 글자를 대분자로 사용하는 대문자 카멜케이스(Upper Camel Case)를 사용합니다.
- 대소문자를 구별합니다. 예를 들어 Var와 var를 다르게 인식합니다.

<br>

[TIP] **예약어와 키워드**
>예약어는 프로그래밍 언어에서 미리 사용하기로 약속한 단어로, 식별자로 사용할 수 없는 단어를 뜻합니다. 키워드는 프로그래밍 언어 문법의 일부로, 특별한 의미가 있는 단어를 뜻합니다. 스위프트의 키워드는 대부분 예약어입니다. 일부 예약어의 경우에는 강세표(backquote. ')를 사용하여 이름으로 사용할 수 있습니다. 

<br>

[TIP] **스위프트에서 세미콜론**
>스위프트에서 명령 구문 뒤에 세미콜론(;)을 붙이는 것은 선택ㄱ 사항입니다. 기존 프로그래밍 언어의 습관대로 구문 뒤에 세미콜론을 붙여도 상관 없습니다만, 새로운 문법에 적응하려면 세미콜론을 붙이지 않는것을 권합니다.

<br>
<br>

>**NOTE**_ 변수, 상수, 함수, 클래스 , 구조체, 열거형, 익스텐션 등의 모든 이름은 스위프트에서 미리 정한 키워드(예약어) 및 데이터 타입 이름 등을 사용할 수 없습니다. 예를 들어 let var: String = "String" 은 잘못된 구문입니다. <br> let var: String = "String"코드에 대해 출력되는 오류 메시지
<img width="459" alt="스크린샷 2021-05-25 오후 5 38 00" src="https://user-images.githubusercontent.com/68891494/119467269-51c10580-bd80-11eb-86a1-9629af97d084.png">
<br>
는 var는 스위프트의 키워드이므로 상수 이름으로 사용할 수 없습니다. 스위프트의 키워드 및 주요 식별자 등은 부록에서 조금 더 자세하게 다룹니다.