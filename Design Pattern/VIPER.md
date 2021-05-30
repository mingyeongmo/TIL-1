## VIPER 디자인 패턴
<img width = "500" src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FPC9Qp%2FbtqCl9ztZhJ%2FIS3wjKZESql0ZKy71ktyUk%2Fimg.jpg">

### 역할 및 동작원리
- View
  -  사용자가 보여지는 View를 생각하시면 됩니다., 유저인터렉션을 받는 역할
  - 이벤트가 발생시 Presenter에 해당 일을 전달
  - Presenter의 요청대로 디스플레이하고 사용자 입력을 Presenter로 보내는 작업

- Presenter
  - Entity로 부터 받은 업데이트 이벤트를 실행하지만 데이터를 직접적으로 보내지는 않는다.
  - View 모델의 변경사항을 Interactor에 알린다.
  - '언제'의 타이밍을 아는 존재
  - Interactor로 부터 데이터를 가져오고 View로 보내기 위해 데이터를 준비하여 '언제' View를 보여줄지 결정

- Interactor
  - Presenter로 부터 받은 모델 변경사항에 따라 Entity에 접속하여 Entity로 부터 수신한 데이터를 Presenter로 전달
  - Use Case에 따라서 Entity 모델 객체를 조작하는 로직을 담았습니다.
  
- Entity
  - 객체에 구성된 부분을 Interactor에 의해 제어
  - 순수 모델 객체
  
- Routing
  - Wireframe이라고 불리기도함, UIWindow와 UINavigationController에서 화면간의 탐색을 위한 라우팅을 담당
  - 화면 전환을 담당, Presenter는 '언제' 화면이 전환이라면 Router는 '어떻게' 하는 지 담당

### 장점
1. 각 도메인의 역할이 명확하게 구분됨
2. 모듈을 작게 역할을 분명히 하기에 대규모프로젝트에 적합하다.

### 단점
1. 설계가 여러 곳으로 난립하다.
2. 명확한 가이드나, 유지보수 되는 곳이 없음
3. 많은 파일들을 생성

