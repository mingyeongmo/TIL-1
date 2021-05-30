# CocoaPods install 

podfile을 가져오기 위해서 Terminal에서 프로젝트 안에 **pod init**이라는 명령어를 쳐준다
```
$ pod init 
```
그러면 podfile이 만들어진다.

**Podfile** Xcode프로젝트 디렉토리에 이름이 지정된 텍스트 파일에 종속성을 나열한다.


```
platform :ios, '8.0'
use_frameworks!

target 'MyApp' do
  pod 'AFNetworking', '~> 2.6'
  pod 'ORStackView', '~> 3.0'
  pod 'SwiftyJSON', '~> 2.3'
end
```

이제 프로젝트에 종속성을 설치할 수 있습니다.
```
$ pod install
```

프로젝트를 빌드 할 때 항상 프로젝트 파일 대신 Xcode 작업 공간을 열어야 합니다.
```
$ open App.xcworkspace
```

이제 종속성을 가져올수 있습니다.
```
#import <Reachability/Reachability.h>
```