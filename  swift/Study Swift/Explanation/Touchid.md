# Touch ID & Face ID

> Touch ID는 지문인식 센서가 달린 홈 버튼에 손가락을 가져다 대면 인식되는 에어리어 방시의 지문인식 보안 기술입니다.

> Face ID는 도트 프로젝터로 보이지 않는 3만 개의 점을 사용자의 얼굴에 투사해 사용자의 특징적인 얼굴 패턴을 매핑한 다음 수학적으로 변화시켜 Secure Enclave에 저장하고 이를 Neural Engine으로 분석합니다.

<img width = 200 src = "https://upload.wikimedia.org/wikipedia/commons/a/a0/%D7%94%D7%9C%D7%95%D7%92%D7%95_%D7%A9%D7%9C_%D7%9E%D7%A2%D7%A8%D7%9B%D7%AA_%D7%94%D6%BEFace_ID.jpg">
<img width = 100 src = "https://w.namu.la/s/7e3d9cc9a43cdfcc674ac7428bbdfcca65d9b6041292afd06ba7bf614d1747163a1caca8c6df0ee95e6c338dc403b9a2238ce5a11add7fc390b2a2bf6c527c26467bbce69e2498a569bb08482d569f498a2558be567bd43a64b47184e77055ff">

           FaceID            TouchID

Touch ID는 손에 이물질이 묻거나 땀이 있으면 인식률이 급격하게 떨어지지만 Face ID는 얼굴 형태만 변형되지 않으면 잠금이 해제되며 일반적인 카메라 얼굴인식이나 홍채인식 방식보다 잠금 해제 속도와 인식률 모두 훨씬 우수하다. 

<br>

### 오늘은 **Touch ID & Face ID** 구현을 해볼 것이다.

<br>

Xcode 를 켜봅시다


### 서브 프로젝트 를 추가해줍니다.
<img width="400" alt="스크린샷 2021-08-23 오후 8 27 12" src="https://user-images.githubusercontent.com/68891494/130440502-1071132c-2cef-48ea-a18d-83b90829d13b.png">

### ViewController 에 import 

```swift
import LocalAuthentication
```

이것을 테스트 하기 위해서 저는 버튼을 만들고 그 버튼을 눌렀을 때 인증이 작동하게 하겠습니다.


### 핵심 코드입니다.
```swift
      let context = LAContext()
        var error : NSError? = nil
        if context.canEvaluatePolicy(.deviceOwnerAuthenticationWithBiometrics, error: &error){
            let reason = "Please authorize with touch id!"
            context.evaluatePolicy(.deviceOwnerAuthenticationWithBiometrics, localizedReason: reason) { [weak self]success, error in
                DispatchQueue.main.async {
                    guard success, error == nil else{
                        //failed
                        return
                    }
                    // show other screen
                    let vc = UIViewController()
                    vc.title = "welcome"
                    vc.view.backgroundColor = .systemBlue
                    self?.present(UINavigationController(rootViewController: vc), animated: true, completion: nil)
                }
                
            }        else{
            // Can not use
            let alert = UIAlertController(title: "Failed to Authenticate", message: "Please try again.", preferredStyle: .alert)
            alert.addAction(UIAlertAction(title: "Dismiss", style: .cancel, handler: nil))
            present(alert, animated: true)
        }
```

>연결된 구현은 실제로 LAContext를 생성해 두고 evaluatePolicy 를 호출해서 Touch ID 요청을 보내는 겁니다.
