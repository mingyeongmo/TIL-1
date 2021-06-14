## 콘솔 로그
프로그램에서 로그란 애플리ㅔ이견의 상태 또는 애플리케이션 내부 로직의 흐름을 관찰할 수 있도록 출석한 정보를 의미합니다. 콘솔 로그(Console Lod)는 디버깅 중 디버깅 콘솔에 보여줄 로그를 뜻합니다. 스위프트에서는 print() 또는 dump 함수를 사용하여 콘솔 로그를 출력할 수 있습니다.

### print()함수
스위프트에서 콘솔 로그를 남기는 용도로 print() 함수를 사용합니다. print() 함수의 기본 원령은 public func print(items: Any...,separator: String = default,terminator: String = default)로 정의 되어 있습니다. 기본적으로 print("Hello Swift!")와 같이 사용하면 디버깅 콘솔에서 'Hello Swift!'라는 로그를 확인할 수 있습니다. print() 함수는 로그를 출력한 뒤 줄바꿈을 해주기 위해 줄바꿈 문자(\n)를 자동으로 삽입 해줍니다. 자세한 사용 방법은 변수와 상수에서 다루도록 하겠습니다.

>**NOTE**_print()와 dump()함수
스위프트 표준 라이브러리에는 print() 함수 외에도 dump() 라는 함수가 있습니다. print()함수는 디버깅 콘솔에 간략한 정보를 출력해주는 반면,dump() 함수는 조금 더 자세한 정보를 출력해줍니다. print()함수는 출력하려는 인스턴스의 description 프로퍼티에 해당하는 내용을 출력해주고, dump() 함수는 출력하려는 인스턴스의 자세한 내부 콘텐츠까지 출력해줍니다. 필요에 따라 print()함수 대신에 dump() 함수를 적절히 사용하는 것도 좋습니다. print() 와 dump() 함수는 '부록 B.스위프트의 주요 함수'에서 더 살펴볼 수 있습니다.
```swift
    struct BasicInformation{
        let name: String
        var age: Int
    }

    var yagomInfo: BasicInformation = BasicInformation(name: "yagom", age: 99)

    class Person{
        var height: Float = 0.0
        var weight: Float = 0.0
    }

    let yagom: Person = Person()
    yagom.height = 182.5
    yagom.weight = 78.5

    print(yagomInfo) //BasicInformation(name: "yagom",age: 99)
    dump(yagomInfo)

    /*
    * BasicInformation
    - name: "yagom"
    - age: 99
    */

    print(yagom)    //Person

    dump(yagom)
    /*
    * Person #0
    - height: 182.5
    - weight: 78.5
    */
```

### 문자열 보간법
>문자열 보간법(String Interpolation)은 변수 또는 상수 등의 값을 문자열 내에 나타내고 싶을 때 사용합니다. 문자열 내에 \\(변수나 상수)의 형태로 표기하면 이를 문자열로 치환해서 넣습니다. 문자열 보간법을 이용해 프로그래머가 원하는 문자열로 치환하려면 변수나 상수 타입을 **CustomStringConvertible** 프로토콜을 준수하는 description 프로퍼티로 구현합니다.

```swift
let name: String = "yagom"
print("My name is \(name)");
```

실행 코드로 디버깅 콘솔에서 'My name is yagom'이라는 결과를 볼 수 있습니다.

[Tip] 문자열 보간법을 통해 조금 더 다양한 문자열 출력하기
- 문자열 보간법을 사용하면 기본적으로 인스턴스 description 프로퍼티를 사용하여 문자열로 치환합니다. description 프로퍼티는 CustomStringConvertible 프로토콜을 준수할 때 구현해 주면 됩니다. 하나의 타입에만 국한 하지 않거나 조금 더 다양한 경우의 문자열 보간법을 구현하고 싶다면, StringInterpolationProtocol을 활용하면 됩니다.

### 주석
>주석은 프로그램 소스 코드에 정보를 남기는 목적으로 사용합니다. 주로 코드를 다시 봤을 때 필요한 중요 메모나 다른 프로그래머에게 설명하기 위한 메모 등을 주석으로 남깁니다.

Xcode에는 말풍선의 형태로 레퍼런스 문서의 요약된 내용을 보여주는 퀵헬프라는 기능이 있습니다.코드를 작성하는 중에 레퍼런스 문서로 이동하지 않고도 (퀵헬프를 지원하는) 데이터 타입이나 메서드 등의 간단한 정보를 확인할 수 있는 아주 유용한 기능입니다.

퀵헬프를 보려면 큌헬프를 보기 원하는 항목(변수,상수,함수,메서드,타입 등등) 위에 마우스 커서를 위치한 다음 키보드의 옵션(option)키를 누른상태로 클릭 하면 됩니다. 또는 퀵헬츠를 보기 원하는 항목에 커서를 위치한 다음 Quick Help Inspector(단축키 command + option + 2)를 통해 퀵헬프를 확인할 수도 있습니다.

마크업 문법에 맞춰 메서드나 변수, 클랫스 등에 주석을 작성하면 퀵헬프로 다른 프로그래머가 해당 내용을 확인할 수 있습니다. 형식을 맞추는 일이 번거로울 수는 있으나 문서화에 큰 도움이 됩니다.