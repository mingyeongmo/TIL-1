## ViewController 의 생명주기 (Life-Cycle)

<img width="340" alt="스크린샷 2021-05-17 오후 5 16 48" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile26.uf.tistory.com%2Fimage%2F2613D13C58C64DE32C838B">

ViewController는 이러한 Lifecycle을 가집니다. 

<br>


## **viewDidLoad**
> viewDidLoad() 함수입니다. <br> apple 문서를 보면 "Called after the controller's view is loaded into memory"  <br>  : 뷰의 컨트롤러가 메모리에 로드되고 난 후에 호출됩니다. 일단 '뷰'라는 것을 만들고, 메모리에 올려야 접근이 가능하겠죠? 이 viewDidLoad의 기능에 대해 설명하자면, 이 viewDidLoad 메소드는 뷰의 로딩이 완료 되었을때  <br> <**시스템에 의해 자동으로 호출**> <br> 되기 떄문에 일반적으로 리소스를 초기화하거나 초기 화면을 구성하는 용도로 주로 사용합니다. 화면이 처음 만들어질 때 한번만 실행되므로, 처음 한 번만 실행해야 하는 초기화 코드가 있을 경우이 메소드 내부에 작성하면 됩니다.
 
## **viewWillApper**
> 이제 뷰가 로드 된 다음의 상황을 봅시다 <br> 이제 뷰가 눈에 보여야 겠죠? 이 viewWillAppear는 뷰가 이제 나타날 거라는 신호를 컨트롤러에게 알리는 역할을 합니다. <br> 즉 뷰가 나타나기 직전에 호출된다고 볼 수 있다.앱의 초기화 작업은 viewDidLoad에서 해도 되겠지만,
다른뷰에서 갔다가 다시 돌아오는 상황에 해주고 싶은 처리가 있겠죠? 이때는 viewWillAppear에서 해주면 됩니다.

## **viewDidAppear**
> viewDidAppear는 뷰가 나타났다는 것을 컨트롤러에게 알리는 역할을 한다. 또한 화면에 적용될 애니메이션을 그려준다. <br> 이 viewDidAppear는 뷰가 화면에 나타난 직후에 실행됩니다. 이것을 제외하면 viewDidAppear과 viewWillAppear는 거의 같다.

## **viewWillDisappear**
>자, viewWillDisAppear는 <br> 뷰가 사라지기 직전에 호출되는 함수입니다. <br> 뷰가 삭제 되려고 하고 있는 것을 뷰 컨트롤러에 통지합니다.

## **viewDidDisappear**
>마지막인 viewDidDisappear은 viewDidDisAppear가 호출되면, viewController가 뷰가 제거되었음을 알려준다. 