# Set
> 같은 타입의 데이터를 순서 없이 하나의 묶음으로 저장하는 형태의 컬렉션 타입
- Set 내의 값은 모두 유일한 값으로 중복된 값이 존재하지 않는다
- Set는 보통, `순서가 중요하지 않거나 각 요소가 유일한 값` 이어야 하는 경우에 사용한다
- Set의 요소로는 *`해시 가능한 값` 이 들어와야 한다

##### *`해시 가능한 값` - Hashable 프로토콜을 따르는 타입. Swift의 기본 데이터 타입은 모두 해시 가능한 값
<br>

- Set 키워드와 타입 이름의 조합으로 써준다
- 배열과 마찬가지로 대괄호로 세트들을 묶어 세트 타입임을 표현한다
- 배열과 달리 축약형이 없다(배열의 `Array<Int> -> [Int]` 같은)
<br>

```swift
var names: Set<String> = Set<String>()
var names: Set<String> = []

var numbers = [1, 2, 3]  // 타입 추론을 하면 배열로 인식한다
print(type(of: numbers)) // Array<Int>

var names: Set<String> = ["jiho", "miyeon", "haesun", "jiho"]

print(names.isEmpty) // false
print(namse.count)   // 3 - 중복된 값을 허용하지 않는다
```
<br><br>

- insert(_:) 메서드를 사용하여 요소를 추가할 수 있다
- remove(_:) 메서드를 사용하여 요소를 삭제할 수 있다. 요소가 없다면 nil 반환

```swift
names.insert("jisoo")
// ["jiho", "miyeon", "haesun", "jisoo"]

print(names.remove("haesun")) // haesun
// ["jiho", "miyeon", "jisoo"]

print(name.remove("suzy"))    // nil
// ["jiho", "miyeon", "jisoo"]
```  
<br><br>

- Set는 자신 내부의 값들이 모두 유일함을 보장하므로, 집합관계를 표현할 때 유용하게 쓸 수 있다
- 두 세트의 교집합, 합집합 등을 연산하기에 매우 용이하다
- sorted() 메서드를 통해 정렬된 배열을 반환해줄 수 있다
```swift
let englishClass: Set<String> = ["jiho", "miyeon", "haesun"]
let koreanClass: Set<String> = ["suzy", "jisoo", "jiho", "miyeon"]

// 교집합 ["jiho", "miyeon"]
let intersectSet: Set<String> = englishClass.intersection(koreanClass)

// 여집합의 합
let symmetricDifferenceSet: Set<String> = englishClass.symmetricDifference(koreanClass)

// 합집합
let unionSet: Set<String> = englishClass.union(koreanClass)

// 차집합
let subtractSet: Set<String> = englishClass.subtracting(koreanClass)

// sorted()
print(unionSet.sorted()) // ["haesun", "jiho", "jisoo", "miyeon", "suzy"]
```
<br><br>

- Set는 포함 관계를 연산할 수 있는 메서드로 구현되어 있다
```swift
let bird: Set<String> = ["비둘기", "닭", "기러기"]
let mammalia: Set<String> = ["사자", "호랑이", "곰"]
let animal: Set<String> = bird.union(mammalia) // bird와 mammalia의 합집합

print(bird.isDisjoint(with: mammalia)) // true - 서로 배타적?
print(bird.isSubset(of: animal))       // true - bird가 animal의 부분집합?
print(animal.isSuperset(of: mammalia)) // true - animal이 mammalia의 전체집합?
print(animal.isSuperset(of: bird))     // true - animal이 bird의 전체집합?
```
<br>