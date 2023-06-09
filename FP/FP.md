# FP

### 함수형 프로그래밍 패러다임 (Functional Programming)
- 프로그램이 상태의 변화 없이 데이터 처리를 수학적 함수 계산으로 취급하고자 하는 패러다임
- 함수 자체의 응용을 중요하게 여긴다
- 함수를 ***`일급 객체(First-class Citizen)`** 로 다룬다
- 최근 프로그래밍 패러다임의 대세


*`일급 객체`
> 함수가 일급 객체가 된다 == 다양한 종류의 함수를 [호출, 전달, 반환 등]의 동작만으로도 프로그램을 구현할 수 있다
- 조건
  - 전달인자(Argument)로 전달할 수 있어야한다
  - 동적 프로퍼티 할당이 가능해야한다
  - 변수나 데이터 구조 안에 담을 수 있어야한다
  - 반환 값으로 사용할 수 있어야한다
  - 할당할 때 사용된 이름과 관계없이 고유한 객체로 구별할 수 있어야한다
<br>

### 장점
- 대규모 병렬처리가 굉장히 쉽다
- 여러 가지 연산 처리 작업이 동시에 일어나는 프로그램을 만들기 쉽다
- 멀티 코어 혹은 여러 개 연산 프로세서를 사용하는 시스템에서 효율적인 프로그램을 만들기 쉽다
- 상태변화에 따른 부작용에서 자유로워지므로 순수하게 기능 구현에 초점을 맞춰 설계할 수 있다
<br>

### 기능
- `Monad`
- `Functor`
- `Map`
- `FlatMap`
- `Filter`
- `Reduce`
- etc..
<br>

### 수학적 함수 vs 명령형 함수
> 코드 이해와 실행 결과의 관점에서 큰 차이

**`수학적 함수`**
- 순수하게 함수에 전달된 인자 값만 결과에 영향을 주므로 상태 값을 갖지 않고 순수하게 함수만으로 동작한다  
  -> 어떤 상황에서 프로그램을 실행하더라도 일정하게 같은 결과를 도출
- 프로그램이 동작하는 흐름에서 상태(값)가 변하지 않으면 함수 호출이 각각 상호 간섭 없이 배타적으로 실행한다  
  -> 병렬처리할 때 부작용(Side-effect)이 거의 없다  
  -> 프로세스 혹은 스레드별로 특정 값을 참조하기 위해 락을 걸거나 대기할 필요가 없기 때문
- 필요한 만큼 함수를 나누어 처리할 수 있도록 스케일업 할 수 있다  
  -> 대규모 병렬처리에 큰 강점

**`명령형 함수`**
- 절차지향 프로그래밍 패러다임이 포함  
  -> 함수 실행 시 전달받은 전달인자 외에도 포인터, 레퍼런스 값 등 객체의 상태(프로퍼티) 값 또는 메모리 참조 값 등이 변경될 수 있다  
  -> 함수 내부의 처리에도 영향을 미칠 수 있다
    
|| 명령형 프로그래밍 | 함수형 프로그래밍 |
|:-:|:-:|:-:|
| 초점 | `작업 수행 알고리즘`<br>`상태의 변경 추적` | `원하는 정보`<br>`필요한 변환` |
| 상태 변경 | `중요` | `없음` |
| 실행 순서 | `중요` | `낮은 중요도` |
| 주요 흐름 제어 | `제어 구문(반복문, 조건문 등)`<br>`함수(메서드) 호출` | `순환(재귀)함수 호출 등의 함수 호출로 제어` |
| 주요 조작 단위 | `클래스나 구조체의 인스턴스` | `함수` |
<br>

### 코드 비교
- 명령형 프로그래밍
```swift
func doSomething() {
    print("do something")
}

func doAnotherThing() {
    print("do another thing")
}

func excuteAll() {
    doSomeThing()
    doAnotherThing()
}

excuteAll()

//================

func sum(first: Int, second: Int) -> Int {
    return first + second
}

sum(first: 10, second: 5)
```
- 함수형 프로그래밍
```swift
func doSomething() {
    print("do something")
}

func doAnotherThing() {
    print("do another thing")
}

func excute(tasks: [() -> Void]) {
    for task in tasks {
        task()
    }
}

excute(tasks: [doSomething, doAnotherThing])

//================

func sum(first: Int) -> ((Int) -> Int) { // 커링
    return { second in first + second }
}

sum(first: 10)(5)
```
<br>
