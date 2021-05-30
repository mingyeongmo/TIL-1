## VIP 다자인 패턴
 <img width = "200" src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbIQuEB%2FbtqCgRN8mYz%2FjE8y2PXHhCklJztI0ITxo1%2Fimg.png">

 VIP패턴은 VIPER 패턴과 디렉토리와 생성되는 클래스는 동일하지만 플로우를 다른 관점에서 보는 아키텍처

위의 그림 처럼 VIPER는 양방향으로 로직이 순환해서 순환참조에 의한 메모리 누수가 날 수 있고, 또한 하나의 액션의 기대 결과값을 위해 각 클래스의 프로토콜에 메소드를 만들어야하는 수고스러움이 있다.

그래서 이런 수고스러움을 덜고자 VIP는 닫는방향으로 로직이 순환해서 액션에 대한 결과값을 보여주는 형태이다.

### 역할 및 동작원리

- View
  - 스토리보드, XiB와 같은 사용자와 상호작용이 발생하는 인터페이스
- Controller
  - View를 코드에 바인딩하는 레이어, => UIViewController
- Interactor
  - Controller의 요청을 보내야하는 비지니스 로직 계층
- Presenter
  - Interactor로 부터 받은 형태를 View에 맞게 전달할 수 있게 Controller에게 전달
- Router
  - Controller에서 발생한 이벤트를 다른 user case에 전달하는 역할

1. View 가 사용자의 인터페이스를 만듭니다.
2. Controller에서 이벤트가 발생하여 모델을 요청후 Interactor를 호출
3. Interactor에서는 기본 코어 라이브러리를 호출하여 데이터를 액세스합니다.
4. Interactor에서 비지니스로직을 처리하고 결과를 다시 Presenter로 보냄
5. Presenter에서 Interactor에서 받은 결과에 대한 UI처리를 Controller에 전달 View에서 보여줌

VIPER와 다르게 액션에 대한 비즈니스 로직을 Presenter를 통하지 않고 Interactor를 요청하여 변화를 주어 단방향으로 플로우가 진행된다.

### 장점
   1. 컴포넌트가 단단히 연결되어 있지 않아 유연하고, 확장가능하며, 유지관리가 가능하다.
   2. 프로토콜로 서로 참조합니다.
   3. 모든 layer가 인터페이스로 되어 있기에 테스트에 용이합니다.

### 단점
   1. layer끼리 전달할 때 request/ response 모델을 랩핑해야하는 불편함이 존재
   2. 모델을 랩핑하지 않으면 컴포넌트가 결합될 수 있다.
   3. 비동기 액션에 대한 처리가 별도로 필요합니다.
