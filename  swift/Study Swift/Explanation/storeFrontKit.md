# StoreFrontKit

>소개: Apple의 StoreKit 프레임 워크는 앱 내 구매를 위해 App Store와 인터페이스하기위한 간결하고 깨끗한 API를 제공합니다. 그러나 주목할만한 누락은 앱 구매시 사용자에게 제공하는 UI 구성 요소입니다. 그 이유는 모든 앱의 모양과 느낌이 다를 가능성이 높습니다.

<br>

## **Pod**
CocoaPods

<br>
podfile 에서 "pod 'StoreFrontKit'"을 적고 pod install이라는 명령어를 입력해서 설치한다.
<img width="809" alt="스크린샷 2021-05-18 오후 4 13 04" src="https://user-images.githubusercontent.com/68891494/118607877-0d6bbd80-b7f4-11eb-836c-8701a45314f3.png">

--------

## File 생성
StoreKit Configuration file을 생성해준다.

<img width="2048" alt="스크린샷 2021-05-18 오후 11 11 09" src="https://user-images.githubusercontent.com/68891494/118666848-73753680-b82e-11eb-84fb-cccd327861c4.png">

<br>

**생성후**

<img width="2048" alt="스크린샷 2021-05-18 오후 11 15 37" src="https://user-images.githubusercontent.com/68891494/118667542-11690100-b82f-11eb-8174-bd8e3c58f542.png">

<br>

>이런 모습이 보인다.

<br>
<br>
<br>

<img width="2048" alt="스크린샷 2021-05-18 오후 11 22 20" src="https://user-images.githubusercontent.com/68891494/118668556-f3e86700-b82f-11eb-8313-b9eb0902a729.png">


<br>
<br>

>그후 + 버튼을 누르고 Add Non-Consumable In-App Purchase 버튼을 누릅니다.

<img width="2048" alt="스크린샷 2021-05-18 오후 11 31 18" src="https://user-images.githubusercontent.com/68891494/118669976-2e063880-b831-11eb-8eca-6de3c4654c7b.png">

이렇게 상품의 이름 (Reference Name)과 제품 id(product id), 가격(price)를 제품에 맞게 바꾸어 줍니다.


<img width="2048" alt="스크린샷 2021-05-18 오후 11 36 11" src="https://user-images.githubusercontent.com/68891494/118670766-de743c80-b831-11eb-80a2-6768301a577f.png">

그리고 Locailizations 버튼을 누르고
<br>

<img width="2048" alt="스크린샷 2021-05-18 오후 11 40 01" src="https://user-images.githubusercontent.com/68891494/118671416-68bca080-b832-11eb-8aff-e89111e3cd9a.png">

<br>

>그리고 여기에 제품 정보 일명 표시 이름 및 설명을 작성해주고


![스크린샷 2021-05-20 오후 1 54 59(2)](https://user-images.githubusercontent.com/68891494/118921561-59913c00-b973-11eb-9d90-a1f90f916322.png)

이 메뉴로 와서 편집 구성표를 누르시고, StoreKit 구성 파일을 제공하기만 하면 됩니다.
즉, 시뮬레이터에서 이러한 제품을 사용할 수 있습니다.

AppDelegate 파일에 가서 
```swift
import StoreFrontKit
```
```swift
        SFKManager.shared.configure(with: StoreFrontKitConfiguration(products: [
            .nonConsumable(productID: "com.example.premium", viewModel: nil),
            .nonConsumable(productID: "com.example.vip", viewModel: nil)
        ]))
```
<br>

>SFKManager에 우리가 원하는 공유 인스턴스가 있습니다. 그리고 configure를 호출해줍니다. 그리고 그것은 배열이 될것 입니다. 실제로 열거형이므로 비 소모품을 고수하고 제품 ID를 제공 할 것입니다. 그리고 뷰 모델에 대해 nil을 사용할 수 있습니다. 상점 첫 화면에 표시되는 방법에 대한 데이터를 보유합니다. 제품을 가져오는 측면에서 준비가 되었을 때 애플은 거래를 시작할 수 있습니다.


### 전체 코드

```swift
import StoreFrontKit
import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        createButton()
    }
    func createButton(){
        let button = UIButton(frame: CGRect(x: 0, y: 0, width: 220, height: 50))
        view.addSubview(button)
        button.center = view.center
        button.backgroundColor = .systemGreen
        button.setTitle("Upgrade", for: .normal)
        button.setTitleColor(.white, for: .normal)
        button.addTarget(self, action: #selector(didTapButton), for: .touchUpInside)
    }
    @objc private func didTapButton(){
        let header = UIView(frame: CGRect(x: 0, y: 0, width: view.frame.size.width, height: view.frame.size.width))
        let imageView = UIImageView(image: UIImage(named: "header"))
        imageView.contentMode = .scaleAspectFill
        imageView.clipsToBounds = true
        header.clipsToBounds = true
        header.addSubview(imageView)
        let footer = UIView(frame: CGRect(x: 0, y: 0, width: view.frame.size.width, height: view.frame.size.width))
        let label = UILabel(frame: footer.bounds)
        footer.addSubview(label)
        label.text = "I am a cool footer"
        label.textAlignment = .center
        
        let vc = SFKMultiNonConsumableViewController(
            with:[
                .nonConsumable(
                   productID: "com.example.premium",
                   viewModel: StoreFrontProductViewModel(
                       icon: UIImage(systemName: "crown"),
                       iconTintColor: .systemPink
                   )
                ),
                .nonConsumable(
                   productID: "com.example.vip",
                   viewModel: StoreFrontProductViewModel(
                       icon: UIImage(systemName: "star"),
                       iconTintColor: .systemBlue
                   )
                )
            ],
            header: header,
            footer: footer
        ) { result in
            switch result{
            case.success(let productID): break
            case.failure(let error): break
            }
        }
        vc.title = "Upgrade"
        vc.navigationItem.largeTitleDisplayMode = .always
        navigationController?.pushViewController(vc, animated: true)
    }
}

```

### Code 설명

>CreateButton는 버튼을 생성하는 메서드이다. CreateButton에서 버튼의 크기, 위치, 색상, 버튼 제목, 버튼 제목 색상들을 설정하고, didTapButton의 기능을 실행할 것을 추가한다.

>didTapButton() 메서드에는 header에서 UIView로 설정하고 imageView로 이미지를 만들어서 보여준다. 미리 추가해둔 "header"라는 이미지를 이용한다. 그리고 똑같이 footer도 만들고 라벨도 추가해준다.

```swift
        let vc = SFKMultiNonConsumableViewController(
```
>이 부분이 핵심이다.
이 부분은 여러 제품들을 보관할 수 있다. 단일 구매 품목을 나타내는  .nonConsumable 을 배열에 추가해서 단일 상품들을 등록해준다. 그리고 클로저로 result가 성공했다면 productID를 failure가 떴을때는 error가 뜬다.


