# Lazy Variable

```
"A lazy stored property is a property whose initial value is not calculated until the first time it is used"
```
직역을 해보자면 lazy 변수는 처음 사용되기 전까지는 연산이 되지 않는다.

더 쉽게 이해 하자면
> 처음 사용되기 전까지는 로드 되지 않았다가 영상을 보려고 클릭하면 해당 영상들이 서버로부터 로드 되는 것입니다.

---
### lazy 사용시 고려사항

1. lazy는 반드시 var와 함께 쓰여야 한다.

    - lazy는 반드시 var와 사용되어야 합니다. 
        - lazy로 선언된 변수는 초기에는 값이 존재하지 않고 이후에 값이 생기는 것이기 때문에 let으로 선언할 수 없다.
2. struct , class
    - lazy는 struct와 class에서만 사용 가능하다
3. lazy vs Computed Property
    - computed Propery는 lazy 키워드를 사용할 수 없습니다. lazy는 처음 사용될때 메모리에 값을 올리고 그 이후 부터 계속해서 메모리에 올라온 값을 사용한다. 그 후 부터는 계속해서 메모리에 올라온 값을 사용합니다. 사용할 때마다 값을 연산하여 사용하는 Computed Property에는 사용할 수 없습니다.
4. lazy & closure
    - lazy는 어떤 특별한 연산을 통해 값을 넣어주기 위해서는 코드 실행 블록인 closure가 필요합니다.

class나 struct의 다른 프로퍼티의 값을 lazy 변수에서 사용하기 위해서는 closure내에서 self를 통해서 접근이 가능하다. 클래스가 생성된 이후에 접근이 가능하기 때문에 클래스내의 다른 영역(메소드, 일반 프로퍼티)에서는 self를 통해 접근할 수 없지만 lazy키워드가 붙으면 생성 후에 접근 할것이라는 의미이기 때문에 closure내에서 self로 접근이 가능하다.
```swift
class Person{
    var name: String

    lazy var greeting: String = {
        return "Hello my name is \((self.name))"
    }()
    init(name: String){
        self.name = name
    }
}

var me = Person(name: "John")

print(me.greeting) // Hello my name is John

me.name = "James"

print(me.greeting) // Hello my name is John
```
lazy var greeting을 보시면 클로저 내부에서 self.name을 통해 name 프로퍼티에 접근하는 것을 보실 수 있습니다. 클래스 내부의 클로저에서 클래스 객체를 self로 참조한다면 메모리 누수가 발생하는 위험이 있다는 것을 아실 것입니다. 하지만 그 뒤의 ()를 통해 그 즉시 실행하고 결과를 돌려주고 끝나버리기 때문에 메모리 누수의 걱정은 없습니다.

또한 프로퍼티가 James으로 변경이 되어도 처음 사용할 때 메모리에는 John이 올라가 있기 때문에 John이 출력이 됩니다.
```swift
class Person {
    var name:String
    
    lazy var greeting: ()->String = { [weak self] in
        return "Hello my name is \(((self?.name))!)"
    }
    init(name:String){
        self.name = name
    }
}

var me = Person(name:"John")

print(me.greeting()) // Hello my name is John

me.name = "James"

print(me.greeting()) // Hello my name is James
```
만일 변수가 lazy var greeting : String이 아닌 lazy var greeting:()->String으로 클로저 실행의 결과를 담는 것이 아닌 클로저 자체를 담고 있는 변수라면 [weak self]를 통해 메모리 누수를 방지해주어야 합니다.

또한 값이 아닌 클로저 자체가 메모리에 올라가 있고 self 는 내부에서 계속해서 클래스를 참조하기 때문에 계속 John이 출력이 되는 것이 아닌 James가 출력이 되는 것입니다.