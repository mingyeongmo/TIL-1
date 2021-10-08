# Sequence & Collection
>Sequence: 요소들의 목록
<br>
> Collection : 모든 Collection은 Sequence를 상속받아 구현되었다.

### Sequence & Collection 특징
Sequence: 첫째, 무한하거나 유한합니다. 한번만 이터레이트 할수 있습니다.

<br>
 Collection :  모든 Collection은 **유한**하다.
몇개의 요소로 구성 되어 있는지 항상 알 수 있다는 뜻이다.


### IteratorProtocol
> IteratorProtocol에 대해서 좀더 자세히 알아보자! IteratorProtocol은 Sequence와 매우 유사합니다.
**Element**라는 associatedtype을 가지고 있으며, 이것은 요소를 추가하거나 이터레이터를 수행할 때 사용하는 타입을 나타냅니다.그리고 **next**라는 함수가 있는데
이것을 next요소로 변환합니다.

```swif
protocol Sequence {
    associatedtype Iterator : IteratorProtocol where Iterator.Element == Element
    func makeIterator() -> Iterator
}
```
IteratorProtocol은 Sequence의 근간이며, Sequence는 프로그래밍할 때 필요한 기초적인 기능들을 제공합니다. 이해를 돕기 위해, Sequence를 이용해 링크드 리스트를 구현해보겠습니다. 링크드 리스트를 선택한 이유는 Sequence에 아주 적합한 데이터 구조이기 때문입니다. 링크드 리스트는 다음번 요소를 찾고, 또 다음번 요소를 찾고, 결국 마지막 요소를 찾을 때까지 이러한 작업을 반복하는 데이터 구조입니다.

