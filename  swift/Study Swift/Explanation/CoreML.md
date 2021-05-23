# CoreML
### what is CoreML
>CoreML은 Apple에서 제공해주는 ML(machine learning) 프레임워크이다.

<br>

## ML(머신러닝)의 장점

응용분야가 넓음
- 상품추천
- 자율주행
- 병 진단

너무 넚은 범위에서 뛰어난 성능을 보여주고 있다.

**뛰어난 성능 -> 사용자가치**

앱내에서 ML의 적용이 시급하다. 

Apple은 2017년도에 CoreML이라는 FrameWork를 선보였습니다.
- CoreML 출시로 iOS앱 내에 ML기능을 사용할수 있게 되었다.

### CoreML의 분야
- 이미지 분석
- 자연어 처리
- 오디오 분석

**순서**

Data 수집 -> ML 모델 생성 -> 모바일용 변환 -> Core ML model format -> Core ML

<br>
<br>


<구글이 제공해주는 ML 사이트>

[Teachable Machine](https://teachablemachine.withgoogle.com/)

<apple 이 제공해주는 ML>

[CreateML](https://developer.apple.com/documentation/createml)

<img width = "300" src = "https://docs-assets.developer.apple.com/published/e6ad1efd6a/d926fc62-3dea-4447-86fc-920d4d6c4781.png">

<img width = "300" src = "https://docs-assets.developer.apple.com/published/efbf968cc0/0edb3e43-a85c-41d0-9156-b0ee0b7b1d37.png">

### 받을수 있는 DATA
- Image
- Text
- Tabular Data

## ML 사용법

Xcode를 키고

<img width="458" alt="mlUsing" src="https://user-images.githubusercontent.com/68891494/119233548-ab4ce880-bb64-11eb-8ef8-835657113c60.png">

Xcode > Open Developer Tool > Create ML

파일 위치를 등록해준 다음

<img width="795" alt="ml finder" src="https://user-images.githubusercontent.com/68891494/119234180-74c49d00-bb67-11eb-97fe-76823e1562b9.png">

NewDocument 버튼을 눌러준다.

<img width="949" alt="file" src="https://user-images.githubusercontent.com/68891494/119234207-a2a9e180-bb67-11eb-8133-1779b97843d9.png">

그러면 만들 ML의 종류를 선택하는 창이 나오고

종류를 선택한 후 프로젝트 파일에 생성해주면 된다.

-------

ML은 Training Data와 Test Data를 구분해 놓는다.


<img width="1429" alt="스크린샷 2021-05-23 오전 1 48 20" src="https://user-images.githubusercontent.com/68891494/119234470-05e84380-bb69-11eb-96f0-782d46313a2a.png">

여기서 Data를 넣어준다.

<img width="1433" alt="스크린샷 2021-05-23 오전 1 49 53" src="https://user-images.githubusercontent.com/68891494/119235132-f0284d80-bb6b-11eb-8f26-683564180ef5.png">

Test할 이미지 까지 넣어주고

Train 버튼을 눌러주면 
<img width="1429" alt="스크린샷 2021-05-23 오전 2 30 07" src="https://user-images.githubusercontent.com/68891494/119235743-fff56100-bb6e-11eb-8594-169bbb96a758.png">

Testing이 된다.
## 정확성을 올리는 방법

<img width="860" alt="스크린샷 2021-05-23 오전 3 21 21" src="https://user-images.githubusercontent.com/68891494/119237076-fd4a3a00-bb75-11eb-9f6c-de5dc2920280.png">

Parameters 에는 Maximum Iterations의 갯수를 늘려서 정확성을 올릴 수 있다. 자료를 몇번 반복해서 학습할 것인지 입력하는 것이다.

[Augmentations](https://developer.apple.com/documentation/createml/improving_your_model_s_accuracy)

<img width="862" alt="스크린샷 2021-05-23 오전 3 37 26" src="https://user-images.githubusercontent.com/68891494/119237533-469b8900-bb78-11eb-9679-c5666fad2436.png">

Augmentation Data를 선택해서 정확성을 올릴 수 있다.

------
Precision & Recall

Precision : 머신러닝 모델이 진짜 Data와 일치하는 것이 몇개인지 퍼센트로 나타낸것 (정밀도), 예측에 맞는것은 몇개인지 라고 이야기 하는것

Recall : 전체 중에 실제로 맞은 Data는 몇개인지 알려주는것, 진짜 Data중에 몇개를 맞췄냐를 Recall 이라고 한다.(재현율)

-------
## Code
먼저 모델을 만들어 넣었는데 실제로 접근할수 있는 객체로 만들어 줘야 한다. 모델 자체가 image Classifier 같은 경우에는 vision이라는 CoreML에서 이미지를 도와주는 공구함의 도움을 받아서 모델을 감쌀수 있다.

```swift
import Vision
```
이미지를 가지고 개 인지 고양이인지 구분하는 모델이기 때문에
```swift
let model = try VNCoreMLModel(for: DogCatClassifier().model)
```
그렇게 모델을 객체로 만들고 모델을 통해서 사진 찍은거와 사진 불러온것을 Request해야한다.
```swift
let request = VNCoreMLRequest(model: model, completionHandler: {[weak self] request, error in
    self?.processClassifications(for: request, error : error)
})
```
이 객체를 통해서 실제로 ML모델의 예측결과를 받아볼 수 있다.
request가 보내지고 나서 그 Request에 대한 핸들러는 클로저로 받는다. 
```swift
func processClassifications(for request: VNRequest, error: Error?) {
        DispatchQueue.main.async {
            guard let results = request.results else {
                self.classificationLabel.text = "Unable to classify image.\n\(error!.localizedDescription)"
                return
            }
            // The `results` will always be `VNClassificationObservation`s, as specified by the Core ML model in this project.
            let classifications = results as! [VNClassificationObservation]
        
            if classifications.isEmpty {
                self.classificationLabel.text = "Nothing recognized."
            } else {
                // Display top classifications ranked by confidence in the UI.
                let topClassifications = classifications.prefix(2)
                let descriptions = topClassifications.map { classification in
                    // Formats the classification for display; e.g. "(0.37) cliff, drop, drop-off".
                   return String(format: "  (%.2f) %@", classification.confidence, classification.identifier)
                }
                self.classificationLabel.text = "Classification:\n" + descriptions.joined(separator: "\n")
            }
        }
    }
    
```

클로저를 받으면 그것을 처리하는 메서드이다. VNRequest인 비전의 Request를 받아서 밑에서 처리 해주고 처음에 CoreML 모델에 대해서 SetUp을 해주는 것이다.
첫번째로는 모델의 객체를 만들고 그 모델에 보낼 Request객체를 또 만들어 주는것이다. Request객체를 만들때는 모델도 필요하고 Request가 예측된 CompletionHandler를 같이 코드를 작성해줘야 한다. Request자체가 이미지 관련 Request이다. 이미지에서는 사진을 뒤집어 보면 거꾸로된 이미지를 가지고 하면 Orientation을 맞춰줘야 하기 때문에 Orientation을 처리하고 이미지가 모델한테 예측해달라고 할때 그 이미지가 원래 머신러닝에 사용하는 이미지 보다 클수도 있고 조금 비율이 다를 수도 있다. 그럴때 어떻게 할지 나타내는 프로퍼티
```swift
request.imageCropAndScaleOption = .centerCrop
```

이 imageCropAndScaleOption같은 경우에는 예를 들어 머신러닝 모델을 만들때 설정하는 것으로 이것은 크게 3가지 있다
- centerCrop
- scaleFit
- scaleFill

첫번째로 모델을 객체로 만들어주고 모델에 보낼 Request를 객체로 만들어준다.
실제로 우리가 processClassifiacation에서는 우리가 보낸 Request를 받아서 처리해준다. 
```swift
let topClassifications = classifications.prefix(2)
let descriptions = topClassifications.map { classification in
// Formats the classification for display; e.g. "(0.37) cliff, drop, drop-off".
    return String(format: "  (%.2f) %@", classification.confidence, classification.identifier)
}
 self.classificationLabel.text = "Classification:\n" + descriptions.joined(separator: "\n")
```
여기가 실제 결과물이 있는곳이다. 결과물이 있는 부분으로 클래스 중에서 값을 가져온다.
클래스의 identifier (이름) 분류의 대상으로 정한다. descriptions을 가지고 업데이트를 시켜준 것이다.
