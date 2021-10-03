# available
> available을 사용하여 특정 Swift 언어 버전 또는 특정 플랫폼 및 OS버전과 관련된 선언의 수명주기(Lifecycle)를 나타냅니다.

사용가능한 속성(attribute)은 항상 두개 이상의 쉼표로 구분된 attribute argument목록과 함께 나타납니다.
아러한 argument는 다음 플랫폼 또는 언어 이름중 하나로 시작합니다.
- iOS 
- iOS ApplicationExtension
- macOS
- macOSApplicationExtension
- watchOS
- watchOSApplicationExtension
- tvOS
- tvOSApplicationExtension
- swift

*(별표)를 사용하여 위에 나열된 모든 플랫폼 이름에 대한 선언의 가용성(availability)을 나타낼 수도 있습니다.
Swift 버전 가용성을 지정하는 사용가능한 attribute는 *를 사용할 수 없습니다.
나머지 argument는 순서에 관계없이 나타날 수 있으며, 중요한 milestones를 포함하여, 선언의 수명주기에 대한 추가 정보를 지정할 수 있습니다.

- ``unavailable``는 지정된 플랫폼에서 선언을 사용할 수 없음을 나타냅니다. 이 argument는 Swift버전 가용성을 지정할 때 사용할 수 없습니다.
- ``introduced``는 선언이 도입된 지정된 플랫폼 또는 언어의 첫번째 버전을 나타냅니다.
 <br>introduced = ``version number``
 <br>버전 번호는 1~3개의 양의 정수로 구성되며, 마침표로 구분합니다.
 <br>

- ``deprecated``는 선언이 사용되지 않는 지정된 플랫폼 또는 언어의 첫번째 버전을 나타냅니다.
<br>deprecated : ``version number``
<br>
<br>optional 버전번호는 1~3개의 양의 정수로 구성되며, 마침표로 구분됩니다. 버전 번호를 생략하면, 해당 선언이 더이상 사용되지 않으므로 정보는 제공되지 않습니다.
버전번호를 생략하면, :(콜론)도 생략하세요.

- ``obsoleted``는 선언이 폐기된 지정된 플랫폼 또는 언어의 첫번째 버전을 나타냅니다. 선언이 obsoleted로 지정되면, 지정된 플랫폼 또는 언어에서 제거 되고, 더이상 사용할 수 없습니다.
<br>obsoleted: ``version number``
<br>
<br> 버전 정보는 1~3개의 양의 정수로 구성되며, 마침표로 구분됩니다.

- ``message``는 사용되지 않거나 더 이상 사용되지 않는 선언을 사용하는 것에 대한 경고 또는 오류를 표시할때 컴파일러가 표시하는 텍스트 메세지를 제공하는데 사용됩니다.
<br>message : ``message``
<br>
<br>메세지는 문자열 리터럴로 구성됩니다.

- ``renamed``는 이름이 바뀐 선언의 새 이름을 나타내는 텍스트 메세지를 제공하는데 사용됩니다. 새로운 이름은, 이름이 바뀐 선언의 사용에 관혜 오류를 낼때 컴파일러에 의해 표시됩니다.
<br>renamed: ``new name``
새이름 문자열 리터럴로 구성됩니다.

---

## #available
예시
```swift
if #available(iOS 11.0, *){
    //do something.
}else{
    //do something.
}
```

> #available은 여러 플랫폼에서 서로 다른 논리 처리를 결정하기 위해서 if 또는 guard문과 같이 사용됩니다. 
즉, Bool을 반환하는 런타임 검사에요.

``*`` 은 필수 입니다

주의할 점은 , 해당 버전을 포함하여 "그 이상의 버전"인지를 확인하는 거예요.
```swift
if #available(iOS 11.0, *){
    //iOS 11,12
}else{
    //iOS 11,12 가 아닌 다른 버전들
}
```
이 되는겁니다.

그럼 타입은? 메소드를 버전또는 플랫폼 별로 제한 할 수 없을까요?
그럴때 바로 @available을 사용합니다.

## @available
@available은 함수(메소드), 클래스 또는 프로토콜 앞에 놓입니다. 타입 또는 프로토콜이 적용되는 플랫폼 및 OS를 나타내요.이건 deployment target과 관련이 깊습니다. #available과 다르게, 컴파일 타임에 경고 또는 오류를 생성합니다.
```swift
@available(iOS 12, *)
func setupDoneButton(){ }
```
이렇게 되면 iOS12를 포함한 그 이상의 버전에서만 setupDoneButton을 호출 할 수 있습니다.

그러나 deployment target이 10이라면

```swift
if #available(iOS 12, *){
    self.setupDoneButton()

}else{
    //Fallback on earlier versions
}
```
이렇게 밖에 호출할 수 밖에 없다.

이렇게 하나의 플랫폼에서만 체크 할수도 있고, 여러개도 가능하다.

```swift
@available(iOS 10.0, macOS 10.12, *)
func setupDoneButton(){}
```
이렇게 하면 된다.

---
위에서 말한 unavailable, introduced...등등을 써보겠습니다.
<br>모두 @available안에 들어가는 것들입니다.

### unavailable
```swift
@available(*, unavailable)
func setupDoneButton(){ }
```
위에서 *은 "*(별표)를 사용하여 위에 나열 된 모든 플랫폼 이름에 대한 선언의 가용성(availability)을 나타낼 수도 있습니다.
<br>그러면 setupDoneButton()은 모든 플랫폼에서 unavailable하다는 뜻입니다.
>사용 하려면 오류가 생깁니다.

메세지도 같이 줄 수 있습니다.
```swift 
@available(*,unavailable,message: "2021년 10월 4일")
func setupDoneButton() { }
```
이렇게 하면
>오류에 메시지도 같이 나온다.

*가 아니라 플랫폼을 지정해주면
```swift
@available(macOS, unavailable)
func setupDoneButton(){ }
```
이렇게 하면 macOS에서는 사용 할 수 없는 메소드 인겁니다.

--- 

### introduced.
```swift
@avaiilable(*,introduced: 12.0)
func setupDoneButton(){ }
```

-> setupDoneButton 은 12.0에서 도입됐다 라고 하는거니까 12.0 이상만 쓸 수 있다.

### deprecated
deprecated은 보니까 현재,, deployment target이랑 관련이 있는 것 같아요.
현재 deployment target "이하" 면 경고가 뜨는것 같습니다.

```swifft
@available(*, deprecated: 10.0, message : "ㅋㅋ")
```
메세지도 추가 가능하다.

초과하면 뜨지 않는다.

메시지도 추가 가능하지만,renamed도 추가 가능합니다.
```swift
@available(*, deprecated: 10.0, renamed: "집가자")
```

### obsoleted
obsoleted은 폐기랑 관련이 있었다. 이것도 deployment target이랑 관련이 있는것 같아요. 역시나 deprecated 처럼 현재 deployment target "이하"면 에러가 뜹니다. deprecated는 경고였지만...obsoleted는 에러가 뜬다.

```swift
@available(swift, obsoleted: 4.2)
```
현재 Swift버전 "이하"면 에러가 뜹니다.
지금 프로젝트 Swift 버전이 4.2상태라면 에러가 나겠죠?

### 마지막
```swift 
@available(swift,deprecated : 4.0 , obsoleted: 5.0, message: "This will be removed in v5.0; please migrate to a different API.")
```
deprecated와 obsoleted 같이 쓰기, deorecated눈 4.0부터 되었고(아직까지는 컴파일 됨), 근데 5.0부터는 아예 폐기되어서 에러가 날거니까 다른걸로 바꿔라라고 경고를 줄 수 있다.