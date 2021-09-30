# Thread-safe란
> iOS는 멀티 스레딩(Multi-Threaded) 방식을 사용하고 있습니다
- 멀티 스레드의 경우 stack을 제외한 Heap, 데이터 영역 등을 공유하고 있기 때문에 thread에서 사용 중인 곳에 다른 thread에서 접근한다면 문제가 생길 수가 있습니다.
- 멀티프로세스(Multi-process)에서는 공유하는 자원공간이 없기 때문에 문제가 생기지 않습니다. 
> 즉. thread-safe란 멀티 스레드 프로그래밍에서 어떤 함수나, 변수, 혹은 객체가 어떤 스레드로부터 동시에 접근이 이루어져도 문제가 생기지 않는다는 것을 의미한다. 여러곳에서 동시에 접근하더라도 그 결과가 올바르다는 것을 의미합니다.
---
#### Thread-safe를 알기 위해서는 알아야 하는 용어
1. atomic: 프로그래밍에서 데이터의 변경이 동시에 일어난 것처럼 보이게 하는 것을 의미합니다. 데이터의 값을 변경하는 것은 항상 그 시간이 필요합니다. atomic 한 데이터의 변경이 이루어지는 시간에는 lock 을 겁니다. 그래서 데이터를 변경하는 시간동안에는 접근이 이루어지지 않게 합니다.

그래서 프로퍼티가 atomic하다는 것은 멀티 스레드 환경에서 데이터가 반드시 변경 전과 후의 상황에서만 접근하는 것을 보장합니다.

즉, 데이터의 변경이 이루어지고 있는 순간에는 접근이 불가하다.

**atomic property 는 항상 serial 하게 접근됩니다**
- swift의 경우 Swift의 경우는 Thread-safe를 고려한 언어가 아니기 때문에 모든 프로퍼티는 non-atomic이기 때문에 별도로 atomic을 지정하기 것이 불가능 하다.

그렇기 때문에 [GCD](https://github.com/JiHoonAHN/TIL/blob/main/%20swift/what%20is%20Swift/GCD.md)를 통해서 이를 다뤄줘야 합니다.


### Thread-safe를 위한 방법
1. mutual Exclusion : Thread lock 이나 semaphore를 걸어서 공유 자원에서는 하나의 Thread 만 접근이 가능하게 한다.
2. Thread Local Storage : 특정 thread에만 접근 가능한 저장소를 만든다.
3. ReEntrancy : thread에서 동작하는 코드가 동일 thread에서 재수행되거나, 다른 thread에서 해당 코드를 동시에 수행해도 동일한 결과 값을 얻을 수 있도록 코드를 작성합니다. 이는 thread 진입시에 local state를 저장하고 이를 atomic 하게 구현할 수 있습니다
4. Atomic Operation : 데이터 변경시 atomic하게 데이터에 접근하도록 만듭니다.
5. Immutable Object : **객체 생성 이후**에 값을 변경할 수 없도록 만듭니다.