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