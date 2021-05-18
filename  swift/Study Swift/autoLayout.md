# AutoLayout
![img](https://user-images.githubusercontent.com/68891494/118460734-f23b7800-b737-11eb-80b1-687559e40249.png)

- 어떤 디바이스에서 그에 따라 자동적으로 배치될 수있게끔 하는 것
- 크게 pin으로 설정하는 방법과 ctrl+로 드래그앤드랍으로 설정 가능
- **간격을 고정으로 한 오토레이아웃 (뷰의 크기가 변동)**
- 뷰와 다른 뷰 사이의 간격과 뷰 와 뷰컨트롤러 테두리와의 간격을 고정 - > 뷰는 그 크기를 맞추기 위해 자체 크기 변동

<br>
<br>

### autolayout이 없다면?

<img width="150" alt="스크린샷 2021-05-17 오후 6 03 39" src="https://user-images.githubusercontent.com/68891494/118463054-49424c80-b73a-11eb-8fec-5e5f4b25b712.png">


<img width="300" alt="스크린샷 2021-05-17 오후 6 06 16" src="https://user-images.githubusercontent.com/68891494/118463373-a6d69900-b73a-11eb-98e7-4c279a25bd09.png">

iphone 11 , ipad pro (12.9인치) 비교

-------

### 2. 사용방법

### **1) constraints 값이 유지되도록 각 뷰를 설정**

```swift
staticView.translatesAutoresizingMaskIntoConstraints = false
greenView.translatesAutoresizingMaskIntoConstraints = false
staticView.translatesAutoresizingMaskIntoConstraints = false
```

### **2) constraints를 주기 전에, 먼저 subView에 추가해야함**
```swift
self.view.addSubView(staticView)
self.view.addSubView(greenView)
self.view.addSubView(blueView)
```
### **3) constraints 추가**
*밑에 나오는 Anchor라는 개념은 "좌표"를 위미 <br>
xAnchor: x좌표 <br>
yAnchor: y좌표

<br><br>

**1.값을 고정, 뷰를 중앙으로 이동**
```swift
greenView.widthAnchor.constraint(equalToConstant: 80).isActive = true
greenView.heightAnchor.constraint(equalToConstant: 50).isActive = true
greenView.centerXAnchor.constraint(equalTo: self.view.centerXAnchor).isActive = true
greenView.centerYAnchor.constraint(equalTo: self.view.centerYAnchor).isActive = true
```

<br>

**2.비율을 16:9로 설정**
```swift
greenView.widthAnchor.constraint(equalToConstant: 100).isActive = true
greenView.heightAnchor.constraint(equalTo: greenView.widthAnchor, multiplier: 16/9).isActive = true  
```

<br>

**3.safe area를 기준으로 뷰 설정**
```swift
greenView.topAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.topAnchor).isActive = true
greenView.leadingAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.leadingAnchor).isActive = true
greenView.trailingAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.trailingAnchor).isActive = true
greenView.bottomAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.bottomAnchor).isActive = true
```

<br>

**4.특정 뷰를 기준으로 뷰를 배치**

※ 주의할점은 "간격"을 입력하는 것이 아닌, "좌표기준"으로 입력하는 것 ( 마이너스 값이 있을 수 있음 )
회색 뷰를 기준으로 오른쪽에 초록색 배치

```swift
greenView.leadingAnchor.constraint(equalTo: staticView.trailingAnchor, constant: 3).isActive = true
greenView.trailingAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.trailingAnchor, constant: -3).isActive = true
greenView.bottomAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.bottomAnchor, constant: -350).isActive = true
greenView.topAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.topAnchor, constant: 350).isActive = true
 
```
<br>

### 3.간편화하여 coding
- ".isActivity = true"를 일일이 달아주는 번거로움을 제거
- NSLayoutConstraint.activate(constraints배열)

```swift
let cons = [
    lbl1.centerXAnchor.constraint(equalTo: self.view.centerXAnchor),
    lbl1.topAnchor.constraint(equalTo: self.view.topAnchor, constant: 100),
    lbl1.bottomAnchor.constraint(equalTo: self.view.bottomAnchor, constant: 300)
]
NSLayoutConstraint.activate(cons)
```

<br>

### 4.쉽게 사용하는 autolayout
- extension으로 UIView에 메소드를 추가하여 구현
  <br>
  (각 padding, size도 매개변수로 받아서 특정 내부 여백과 뷰의 크기를 설정할 수 있게끔 구현)
```swift 
    extension UIView {
    func anchor(top: NSLayoutYAxisAnchor?,
                right: NSLayoutXAxisAnchor?,
                bottom: NSLayoutYAxisAnchor?,
                left: NSLayoutXAxisAnchor?,
                padding: UIEdgeInsets = .zero,
                size: CGSize = .zero) {
        
        translatesAutoresizingMaskIntoConstraints = false
        
        if let top = top {
            topAnchor.constraint(equalTo: top, constant: padding.top).isActive = true
        }
        
        if let right = right {
            rightAnchor.constraint(equalTo: right, constant: -padding.right).isActive = true
        }
        
        if let bottom = bottom {
            bottomAnchor.constraint(equalTo: bottom, constant: -padding.bottom).isActive = true
        }
        
        if let left = left {
            leftAnchor.constraint(equalTo: left, constant: padding.left).isActive = true
        }
        
        if size.width != 0 {
            widthAnchor.constraint(equalToConstant: size.width).isActive = true
        }
        
        if size.height != 0 {
            heightAnchor.constraint(equalToConstant: size.height).isActive = true
        }
    }
}
```
<br>
- 사용
  
```swift
class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let greenView = UIView()
        greenView.backgroundColor = .green
        
        let redView = UIView()
        redView.backgroundColor = .red
        
        for item in [greenView, redView] {
            view.addSubview(item)
        }
        
        greenView.anchor(top: view.safeAreaLayoutGuide.topAnchor,
                      right: view.safeAreaLayoutGuide.rightAnchor,
                      bottom: nil,
                      left: nil,
                      padding: .init(top: 0, left: 0, bottom: 0, right: 30),
                      size: .init(width: 100, height: 200))
        
        redView.anchor(top: greenView.bottomAnchor,
                       right: greenView.rightAnchor,
                       bottom: nil,
                       left: nil,
                       padding: .init(top: 15, left: 0, bottom: 0, right: 0),
                       size: .init(width: 100, height: 100)
                       )
    }
}
```

**5. 프로그래밍으로 작성한 Constraints를 가시적으로 보는방법 (console창 메시지 이용)**
   * autolayout을 설정하다보면 오류 메시지가 뜨는데, 오류가 나는 부분을 찾기가 힘듦

<br>

[autolayout 설정한 것을 가시적으로 보여주는 사이트](https://www.wtfautolayout.com/)