# Xcode 프로젝트에 Pods 추가

### 설치 

**Podfile** 을 만들고 종속성을 추가
```
target 'MyApp' do
  pod 'AFNetworking', '~> 3.0'
  pod 'FBSDKCoreKit', '~> 4.9'
end
```
- **$ pod install** 프로젝트 디렉토리에서 실행하십시오.
- **App.xcworkspace**를 열고 빌드하십시오.

## CocoaPods로 새 Xcode 프로젝트 만들기
 CocoaPods로 새 프로젝트를 생성하려면 다음의 간단한 단계를 따르십시오.

- 평소처럼 Xcode에서 새 프로젝트를 만듭니다.
- 터미널 창을 열고 **$ cd** 프로젝트 디렉터리로 이동합니다.
- Podfile을 만듭니다. **$ pod init** 명령어를 사용하면 됩니다.
- Podfile을 엽니다. **$ open podfile** 명령어를 입력해주세요. 첫번째 줄은 지원되는 플랫폼과 버전을 지정해야합니다.

```
platform :ios, '9.0'
```

<br>

- CocoaPods를 사용하려면 연결할 Xcode 대상을 정의해야합니다. 예를 들어 iOS 앱을 작성하는 경우 앱의 이름이됩니다. 서면에 의한 대상 섹션 만들기 **target '$TARGET_NAME' do**와 **end**후 몇 줄을.
- **pod '$PODNAME'** 대상 블록 내부에 한 줄을 지정하여 CocoaPod를 추가하십사오.

```
target 'MyApp' do
  pod 'ObjectiveSugar'
end
```

<br>

- Podfile을 저장하십시오.
- **$ pod install** 실행
- 생성된 **MyApp.xcworkspace**를 엽니다. 이 파일은 응용프로그램을 만들 때 매일 사용하는 파일이어야 합니다.

### 기존 작업 공간과 통합
CocoaPods를 기존 작업 공간과 통합하려면 Podfile에 추가 한 줄이 필요합니다. 다음 **.xcworkspace** 과 같이 대상 블록 외부에 파일 이름을 지정하기 만하면됩니다 .
```
workspace 'MyWorkspace'
```

<br>

## 언제 pod install vs pod update?

많은 사람들은 언제 **pod install** 해랴하는지, 언제 **pod update** 를 사용해야하는지 헷갈린다. 특히 pod instal를 대신 사용해야하는 pod update를 사용하는 경우가 많습니다.

[안내서](https://guides.cocoapods.org/using/pod-install-vs-update.html) 를 참고하세요

<br>

## Pods 디렉토리를 소스 제어로 확인해야합니까?

프로젝트마다 워크플로우가 다르기 때문에 Pods 폴더의 체크 인 여부는 사용자에게 달려 있습니다. Pods 디렉터리는 소스 제어 하에 두고 .git 무시에 추가하지 않는 것이 좋습니다. 하지만 궁극적으로 이 결정은 여러분에게 달려 있습니다.

### Pods 디렉토리 확인의 이점
- 저장소를 복제 한 후에는 머신에 CocoaPods를 설치하지 않고도 프로젝트를 즉시 빌드하고 실행할 수 있습니다.  **pod install** 를 실행할 필요가 없으며 인터넷 연결이 필요하지 않습니다.
- 포드 아티팩트 (코드 / 라이브러리)는 포드 소스 (예 : GitHub)가 중단 되더라도 항상 사용할 수 있습니다.
- Pod 아티팩트는 리포지토리를 복제 한 후 원래 설치의 아티팩트와 동일하도록 보장됩니다.

### Pods 디렉토리 무시의 이점
- 소스 제어 저장소는 더 작고 공간을 덜 차지합니다.
- 모든 포드의 소스 (예 : GitHub)를 사용할 수있는 한 CocoaPods는 일반적으로 동일한 설치를 다시 생성 할 수 있습니다. (기술적으로 **pod install** Podfile에서 커밋 SHA를 사용하지 않을 때 실행 이 동일한 아티팩트를 가져오고 다시 생성 한다는 보장은 없습니다 . 이는 특히 Podfile에서 zip 파일을 사용할 때 적용됩니다.)


- 다른 Pod 버전으로 분기를 병합하는 것과 같은 소스 제어 작업을 수행 할 때 처리해야 할 충돌이 없습니다.

## **Podfile.lock 이란**

이 파일 pod install 과정의 첫번째 실행을 마친 후, 각 Pod은 설치되었다의 버전 추적하며 생성됩니다. 

```
pod 'RestKit'
```

<br>

**pod install**을 실행하면 RestKit의 현재 버전의 **Podfile.lock**이 설치되어 설치된 정확한 버전 을 나타내는가 생성됩니다

> (예: **RestKit 0.10.3.** 받는 사람 덕분에 **Podfile.lock**, 실행중인 **pod install** 다른 시스템에 시간 이후의 시점에서이 가상 프로젝트에 여전히 새 버전을 사용할 경우에도 RestKit 0.10.3를 설치합니다. CocoaPods는 Podfile.lock종속성이 Podfile에서 업데이트되거나 pod update호출 되지 않는 한 Pod 버전을 준수 합니다 (새 항목 Podfile.lock이 생성됨). 이런 식으로 CocoaPods는 예기치 않은 종속성 변경으로 인한 오류를 방지합니다.)

