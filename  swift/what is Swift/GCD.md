# GCD  
- GCD : Grand Central Dispatch
C기반의 저수준 API라고 한다.

iOS앱 기발을 하게 되면 ㅍ;ㄹ스로 알아야 하는 것인데, DispatchQueue와 같다고 생각하면 될 듯하다.

## DispatchQueue

#### Serial, Concurrent
``DispatchQueue``에는 두가지가 있다.
- Serial Queue : 등록된 작업을 한번에 하나씩 차례대로 처리하는 직렬의 Queue.
- concurrent Queue: 등록된 작업을 한번에 하나씩 처리 하지 않고 여러 작업들을 동시에 작업하는 병렬의 Queue

SerialQueue 예시
```swift
let serialQueue = DispatchQueue(label: "jihoon04.serial")
print(serialQueue)
```
-> 기본이 Serial Queue이다.

Concurrent Queue 예시
```swift
    let concurrentQueue = DispatchQueue(label : "jihoon04.concurrent",
                                        attributes : .concurrent)
    print(concirremtQueue)
```
-> Concurrent Queue로 사용하려면 따로 attributes 선언을 해줘야 한다.


### Sync, Async
그리고 또 각 queue는 ``Sync`` 와 ``Async`` 두 가지로 나눌 수 있다.
``Sync``는 말그대로 동기. ``Async``는 말 그대로 비동기인데, ``Sync``는 큐에 추가된 작업이 종료될 때 까지 기다리는것이고, ``Async``는 큐에. 작업을 추가하지만 완료 여부는 보장하지 않는 것이다.
- Serial - Sync
- Concurrent - Sync
- Serial - Async
- Concurrent - Async

총 4가지 조합이 있다.

### Main, Global
앱 실행시 시스템에서 기본적으로 2개의 Queue를 만들어 주는데, 그것이 ``Main Queue``와 ``Global Queue``이다.

- ``Main Queue`` : 메인 스레드에서 사용 되는 ``Serial Queue``. 모든 UI처리는 메인 스레드에서 처리를 해야한다.

- ``Global Queue``: 편의상 사용할 수 있게 만들어 놓은 ``Concurrent Queue``. 처리 우선 순위를 위한 Qos(Quality) 파라미터를 제공한다. 작업 완료의 순서를 정할 수 없지만 우선적으로 일을 처리할 수 있다.


#### Qos 우선 순위

 1.``userInteractive`` 

 2.``userInitiated``

 3.``default``

 4.``utility``

 5.``background``

 6.``unspecified``

 순으로 처리가 된다.

### Conclusion
sync는 작업이 끝날 때까지 기다리기 때문에 UI 업데이트는 main thread의 async만 사용 가능하다.
raywenderlich 예제에서는 UI 업데이트를 위해 아래와 같이 코드를 작성하고 있다.

```swift
DispatchQueue.global(qos: .userInteractive).async{
    forLoop("1")
    DispatchQueue.main.async{
        print("2")
    }
}
```
