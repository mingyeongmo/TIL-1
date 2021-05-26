# SnapKit
**SnapKit이란**
짧은 코드로 autolayout을 표현할 수 있도록 도와주는 프레임워크

### pod SnapKit

<img width="714" alt="스크린샷 2021-05-17 오후 5 11 09" src="https://user-images.githubusercontent.com/68891494/118454115-f913bc00-b732-11eb-8194-b4496ed97b29.png">

### or

### Swift Package

[Snapkit](https://github.com/SnapKit/SnapKit)


<img width="340" alt="스크린샷 2021-05-17 오후 5 16 48" src="https://user-images.githubusercontent.com/68891494/118454831-c5856180-b733-11eb-875f-9df88dd530e1.png">

> Xcode > File > SwiftPackages > Add Package Dependency

"https://github.com/SnapKit/SnapKit.git"
이 코드를 복사해서 

<img width="400" alt="스크린샷 2021-05-17 오후 5 21 00" src="https://user-images.githubusercontent.com/68891494/118457246-89063580-b734-11eb-8eb4-9c8bda1f0652.png">

이곳에 넣은 후 Next 버튼을 눌러준 후


<img width="400" alt="스크린샷 2021-05-17 오후 5 24 24" src="https://user-images.githubusercontent.com/68891494/118457613-e4d0be80-b734-11eb-9178-322ff81c02f2.png">

이렇게 Finish 버튼이 뜨면 설치가 성공적으로 된 것이다.

<br>
<br>
<br>

>**사용법**

1. equalTo()사용 방법
'view.topAnchor와 같이 방향을 정해주지 않고 view 그대로 삽입
"make.top.equalTo(self.view.topAnchor)": 이것의 의미는 make의 top을 self.view의 top과 동일하게 설정한다는 의미
- SnapKit 임포트
  
  <img width="175" alt="스크린샷 2021-05-17 오후 5 02 51" src="https://user-images.githubusercontent.com/68891494/118453261-f5cc0080-b731-11eb-9c4e-3022fe061024.png">
- UIView객체.snp.makeContraints(트레일링클로저)로 접근
  
<img width="438" alt="스크린샷 2021-05-17 오후 5 06 17" src="https://user-images.githubusercontent.com/68891494/118453512-45123100-b732-11eb-8c12-a4b979f95039.png">


<br>
<br>
<br>
------------------
### SnapKit 을 썼을때와 안썼을때 차이점

![스크린샷](https://user-images.githubusercontent.com/68891494/118458014-44c76500-b735-11eb-964d-67bd19e3e8a3.png)
- 안썼을때

![스크린샷](https://user-images.githubusercontent.com/68891494/118458243-80fac580-b735-11eb-8dd4-7e41878a1990.png)
- 썼을때

2) 한꺼번에 레이아웃 배치하기
 - m.top.bottom.equalTo(self.mapView)와 같이 연속적으로 쓴다면 m객체의 top과 bottom을 동시에 지정

3) m.top의 위치를 self.view의 bottom위치와 동일하게 조절해 줘야 한다면?
m.top.equalTo(self.view.snp.bottom)

### superview와의 auto layout 설정

.equalToSuperview() 속성 사용


```swift
stackView.snp.makeConstraints { (make) in
    make.left.top.right.equalToSuperview()
    make.height.equalTo(30)
}
```
이렇게 사용하면 된다.