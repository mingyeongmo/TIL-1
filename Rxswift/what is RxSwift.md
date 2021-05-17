# RxSwift 란 
RX는 ReactiveX 이고, ReactiveX는 Reactive eXtensions 의 줄임말 입니다.

<br>

* ReactiveX의 소개 글

> ReactiveX is a library for composing asynchronous and event-based programs by using observable sequences.
It extends the observer pattern to support sequences of data and/or events and adds operators that allow you to compose sequences together declaratively while abstracting away concerns about things like low-level threading, synchronization, thread-safety, concurrent data structures, and non-blocking I/O....Why Use Observables?..

ReativeX는 관찰 가능한 시퀀스를 사용하여 비동기식 및 이벤트 기반 프로그램을 구성하기 위한 라이브러리 이다.

그리고 Observer 패턴을 사용한다. 여러가지 기능/ 문제를 해결해 주는 오퍼레이터를 지원한다고 한다.

RX는 Microsoft가 .NET에서 사용하려고 만든 Open Source Library이다.

지금은 다양한 언어로 확장되어 사용되고 있습니다.

> RxJs,RxJava ,RxSwift,RxKotlin, RxPY, RxScala, RxPHP, RxNetty, RxRuby, RxRust, RxNet ..

비동기로 이벤트 기반의 프로그래밍을 보다 효율적으로 사용하려고 만든 것이다.

 

많은 Swift 개발자들도 Swift에 새로운 패러다임을 붙이려는 여러가지 시도를 해보려고 할 것 같다.

RxSwift는 ReactiveX를 도입한 Swift 개발을 위한 Base가 되는 라이브러리 입니다.

RxSwift 레파지토리가 있는 Github 사이트 입니다.

[ReactiveX/RxSwift](https://github.com/ReactiveX/RxSwift)


<br>

내용을 보면 

### This is a Swift Version of RX.

라고 되어 있습니다.

RxSwift는 ReactiveX를 하기 위한 가장 기본이 되는 오퍼레이터들을 제공하고 있습니다.

<br>

# FRP란
FRP는 Fuctional Reactive Programming의 약어 입니다.

<br>

[Functional reactive programming - Wikipedia](https://en.wikipedia.org/wiki/Functional_reactive_programming)

<br>

FPR (Functionnal Reactive Programming)는 기능 프로그래밍의 구성 요소 (예 : map, reduce, filter..)를 사용하는 반응형 프로그래밍(비동기 데이터 흐름 프로그래밍)을 위한 프로그래밍 패러다임입니다.

Swift는 함수형 프로그래밍(FP) 패러다임을 강조하고 있고, 

Rx라는 시대의 흐름과 함쳐진 RxSwift는 함수형 프로그래밍 (FP)에 반응형 프로그래밍(Reactive Programming)이 더해진 FRP로 프로그래밍을 하게 해준다.
