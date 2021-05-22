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

