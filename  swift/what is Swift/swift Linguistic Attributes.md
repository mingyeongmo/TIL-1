# Swift의 언어적 특성
>애플이 최초에 스위프트를 발표했을 때 스위프트 언어의 특징을 Safe, Modern, Powerful이라고 발표헀습니다. 그러나 오픈소스로 전환되면서 특징을 Safe, Fast, Expressive로 변경하여 발표했습니다. 먼저 애플이 발표한 스위프트의 언어적 특징을 항목별로 정리해보았습니다. 

<br>

**안전성(Safe)**
>스위프트는 안전한 프로그래밍을 지향합니다. 소프트웨어가 배포되기 전, 즉 프로그래밍하는 중에 프로그래머가 저지를 수 있는 실수를 엄격한 문법을 적용해 미연에 방지하고자 노력했습니다. 때론 너무 강제적이라고 느껴질 수 있지만 문법적 제재는 실수를 줄이는 데 도움이 됩니다. 버그를 수정하거나 실수를 찾아내는 시간을 절약할 수 있습니다. 옵셔널이라는 기능을 비롯하여 guard구문, 오류처리, 강력한 타입 통제 등을 통해 스위프트는 안전한  프로그래밍을 구현하고 있습니다.

<br>

**신속성(Fast)**
> 스위프트는 C 언어를 기반으로 한 C, C++, Objective-C와 같은 프로그래밍 언어를 대체 하려는 목적으로 만들어 졌습니다. 아직은 미흡한 부분도 있지만 스위프트가 C 언어 수준과 동등한 성능을 일정한 수준으로 유지하는 데 초점을 맞춰 개발되었습니다. 실행속도의 최적화뿐만 아니라 컴파일러를 지속적으로 개량해 더 빠른 컴파일 성능을 구현해 나가고 있기도 합니다.

<br>

**더 나은 표현성(Expressive)**
> 컴퓨터 과학 분야의 발전과 함께 성장한 수많은 프로그래밍 언어 각각의 문법은 다양한 장단점이 있습니다. 스위프트는 이런 장단점을 참고해 좀 더 사용하기 편하고 보기 좋은 문법을 구현하려 노력했습니다. 덕분에 개발자들이 원하던 현대적이고 세련된 문법을 구사할 수 있습니다. 그러나 지금의 스위프트가 끝이 아닙니다. 계속된 업데이트를 통해 더욱 보기 좋고 쓰기 좋은 언어로 발전해 나갈 것입니다.

애플이 발표한 세 가지 특징 외에도 스위프트는 많은 특징이 있습니다. 그중에 프로그래밍 패러다임에 대해 조금 더 설명하겠습니다. 스위프트는 여러 가지 프로그래밍 패러다임을 차용한 다중 패러다임 프로그래밍 언어입니다. 크게 보면 명령형 프로그래밍 패러다임, 객체 지향 프로그래밍 패러다임, 함수형 프로그래밍 패러다임. 프로토콜 지향 프로그래밍 패러다임을 차용했습니다. 정확하게는 명령형과 객체지향 프로그래밍 패러다임을 기반으로 한 함수형 프로그래밍 패러다임과 프로토콜 지향 프로그래밍 패러다임을 지향합니다.

<br>

결과적으로 스위프트에서 가장 강조하는 부분은 함수형 프로그래밍 패러다임과 프로토콜 지향 프로그래밍 패러다임입니다.
기존의 C 언어는 명령형 프로그래밍 패러다임을 차용했으며, C++, JAVA등의 언어는 명령형 프로그래밍 패러다임과 객체지향 프로그래밍 패러다임을 동시에 차용한 다중 프로그래밍 패러다임 언어입니다. 스위프트는 여기에 함수형 프로그래밍 패러다임과 프로토콜 지향 프로그래밍 
패러다임을 더한 언어라고 생각하면 됩니다.

<br>

지금부터 오늘날 대부분의 프로그래밍 언어에서 차용하는 객체지향 프로그래밍 패러다임에 대해 알아보고, 근래에 큰 인기를 끌고 있는 함수형 프로그래밍 패러다임과 프로토콜 지향 프로그래밍 패러다임에 대해 조금 더 알아보겠습니다.

<br><br><br>

**객체지향이란**

- [객체지향(OOP)](https://github.com/JiHoonAHN/TIL/blob/main/%20swift/what%20is%20Swift/object%20Oriented%20Programing.md)

<br>


**함수형**


- [함수형 프로그래밍 패러다임](https://github.com/JiHoonAHN/TIL/blob/main/%20swift/what%20is%20Swift/Functional%20Programming%20Paradigm.md)

<br>


**프로토콜**


 - [프로토콜 지향](https://github.com/JiHoonAHN/TIL/blob/main/%20swift/what%20is%20Swift/Protocol%20Oriented.md)