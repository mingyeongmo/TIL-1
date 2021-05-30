# CocoaPods(코코아팟)이란

<img width = "150" src ="https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fnmv5i%2FbtqAt6ktkFK%2FBysiKz65BA2rKdwpTxK8r1%2Fimg.png">

### CocaPods
>CocoaPods는 Objective-C, Swift 및 외부 라이브러리 관리를 위한 표준 형식을 제공하는 RubyMotion으로 Objective-C 런타임에서 실행되는 기타 언어를 위한 애플리케이션 수준 종속성 관리자 입니다.<br>
Eloy Durán과 Fabio Pelosin이 개발했으며 다른 많은 사람들의 도움과 기여로 프로젝트를 계속 관리하고 있습니다

<br>

[공식사이트](https://cocoapods.org/)

------
## 설치방법
CocoaPods는 Ruby로 빌드되었으며 macOS에서 사용 가능한 기본 Ruby로 설치할 수 있습니다. 기본 루비를 사용하는 것이 좋습니다.

기본 Ruby 설치를 사용하려면 **sudo** gem을 설치할 때 사용해야 합니다. (하지만 이것은 gem 설치 중에 만 문제가됩니다.)

```
$ sudo gem install cocoapods
```
설치중에 문제가 생긴다면

### Sudo없는 설치
> 이 프로세스에 대해 RubyGems 관리자 권한을 부여 하지 않으 려면 RubyGems 환경에 **--user-install**플래그를 전달하거나 **gem install** RubyGems 환경을 구성 하여 사용자 디렉토리에 설치하도록 RubyGems에 지시 할 수 있습니다. 후자는 우리 의견으로는 최상의 솔루션입니다. 이렇게하려면 터미널을 열고 **.bash_profile** 선호하는 편집기를 사용하여 생성하거나 편집하십시오 . 그런 다음 파일에 다음 행을 입력하십시오.

```
export GEM_HOME=$HOME/.gem
export PATH=$GEM_HOME/bin:$PATH 
```

이 **--user-install** 옵션을 사용하기로 선택한 경우에도 **.bash_profile**를 설정 **PATH** 하거나 전체 경로 앞에 추가 된 명령을 사용 하도록 파일을 구성해야 합니다. .NET과 함께 gem이 설치된 위치를 찾을 수 있습니다. **gem which cocoapods**

```
$ gem install cocoapods --user-install
$ gem which cocoapods
/Users/eloy/.gem/ruby/2.0.0/gems/cocoapods-0.29.0/lib/cocoapods.rb
$ /Users/eloy/.gem/ruby/2.0.0/bin/pod install
```

### CocoaPods 업데이트
>CocoaPods를 업데이트하려면 gem을 다시 설치하면 됩니다.

```
$ [sudo] gem install cocoapods
```

또는 시험판 버전인 경우
```
$ [sudo] gem install cocoapods --pre
```