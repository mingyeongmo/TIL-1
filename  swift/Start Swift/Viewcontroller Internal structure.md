# Viewcontroller Internal structure
> iOS의 개발의 기초가 되는 Viewcontroller의 내부 구조이다.
- 앱의 뷰 컨트롤러로 이루어져 있다. 어떤 앱이던 한 개 이상의 뷰 컨트롤러를 가지 있다.
- 이유는 뷰 컨트롤러가 뷰를 가지고 있기 때문이다.
- 대부분의 앱은 수많은 뷰컨트롤러로 이뤄져있기도 하다.

### View의 계층 관리
- 각각의 viewcontroller는 다양한 뷰 계층을 관리한다.
- 이 계층을 나눌 때에 가장 근원이 되는 것이 rootView이다.
    - 때문에 모든 Viewcontroller는 한개 이상의 rootView를 가진다.
- 화면에 표시되는 모든 뷰는 rootView의 계층 안에 있어야 한다.

## 뷰와 관련된 Notifications을 다룬다

>When the visibility of its views changes, a view controller automatically calls its own methods so that subclasses can respond to the change. Use a method like viewWillAppear: to prepare your views to appear onscreen, and use the viewWillDisappear: to save changes or other state information. Use other methods to make appropriate changes.

<img width=500 src = "https://t1.daumcdn.net/cfile/tistory/224C3B42574DB29A04?download">

```swift
- UIViewController 객체는 UIView 객체들의 생성과 소멸, 이벤트 발생 및 행위 등을 관리하는 곳이다.

- 때문에 View는 나타나기 직전, 나타나기 후, 사라질 때, 사라지기 직전일 때 시스템에서 단계별로 UIViewController에게 호출 필요한 메소드 재정의 하여 호출한다.
```

## 뷰에서 일어나는 user interactions을 받는다
- 사용자의 모든 이벤트는 뷰컨트롤러가 받는다.
- 그 후에 각 뷰에 따라 관련 action 메소드나 델리게이트를 통해 처리한다.

<br>


# 데이터 중계자 역할
<img width = 500 src = "https://t1.daumcdn.net/cfile/tistory/22414040574DBA0F20">

<br>
<br>


- 뷰 컨트롤러는 자신이 관리하는 뷰와 앱 내부의 데이터를 중계하는 역할을 한다.

# Resource 관리
> 모든 뷰들을 위에 올리고 있는 뷰 컨트롤러는 모든 뷰의 책임과 관리를 맡고 있다.
- didReceiveMemoryWarning method

- 앱 사용 중에 메모리가 부족 할 때  불리는 메소드
- 오랫동안 사용하지 않은 객체와 다시 쉽게 만들 수  있는 객체를 제거한다. 이후에 다시 불리울 때에는 뷰를 다시 그림

※ 참고 - 메모리 워닝이 일어날 때 가장 먼저 지워지는 부분은 뷰이다. 때문에 리소스 관리를 통해 계속 뷰가 제거/생성이 반복되는 것이다. (이를 통해 사실, 뷰디드로드가 한 번만 불리는 것이 아닌 것을 알 수 있다.) 때문에 우리는 뷰의 인스턴스를 생성할 때, 꼭 객체가 nil인지 확인하고 해야한다.

