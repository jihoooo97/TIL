# for-in 구문
> 반복적인 데이터나 시퀀스를 다룰 때 많이 사용한다

<br>

### 기본적인 사용
<br>

```swift
for i in 0..2 {
    print(i)
}
// 0
// 1
// 2


for i in 0...5 {
    if i.isMutiple(of: 2) {
        print(i)
        continue()
    }
    print("\(i) == 홀수")
}
// 0
// 1 == 홀수
// 2
// 3 == 홀수
// 4 
// 5 == 홀수


let hello: String = "hello"

for char in hello {
    print(char)
}
// h
// e
// l
// l
// o


var result: Int = 1

for _ in 1...3 {
    result *= 10
}
print("\(result)")
// 1000
```
<br><br>


### 다양한 컬렉션 타입에서 사용
<br>

```swift
// == Dictionary
let friends: [String: Int] = ["A": 27, "B": 29, "C": 31]

for tuple in friends {
    print(tuple)
}
// ("A", 27)
// ("B", 29)
// ("C", 31)

for (key, value) in friends {
    print("\(key): \(value)")
}
// A: 27
// B: 29
// C: 31


// == Set
let friends: Set<String> = ["A", "B", "C"]

for friend in friends {
    print(friend)
}
// A
// B
// C
```