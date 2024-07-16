## 변수와 가변성

변수는 기본적으로 **불변** _(러스트가 제공하는 안정성과 쉬운 동시성을 활용하는 방식으로 코드를 작성할 수 있도록 하는 넛지(선택 유도))_

변수를 가변으로 만드는것 가능

**불가능 (불변성 오류발생)**

```rust
fn main() {
    let x = 5;
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
}
```

**가능**

```rust
fn main() {
    let mut x = 5;
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
}
```

### 상수

불변 변수와 비슷하나,변수와는 약간 차이점 존재

- `mut` 키워드와 함꼐 선언 불가능
- 항상 불변 ("**기본적으로** 불변" 이 아닌)
- `const` 키워드로 선언
- 값의 타입 명시 필수
- 코드의 전역 스코프를 포함한 어떤 스코프에서도 선언 가능
- 상수 표현식으로만 설정 가능, 런타임에서만 계산될 수 있는 결괏값으로는 안됨.

**예시**

```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

### Shadowing

새 변수를 이전 변수명과 같은 이름으로 선언.

```rust
fn main(){
    let x = 5;
    let x = 6;
    {
        let x = x * 2;
        println!("The value of x in the inner scope is: {x}");
    }

    println!("The value of x is: {x}");


}
```

변수의 타입을 바꾸고 싶을때도 사용 가능

```rust
//불가능
fn main(){
    let spaces = "     "
    spaces = spaces.len();
}

//가능
fn main(){
    let spaces = "    "
    let spaces = spaces.len()
}
```

---

## 데이터 타입

러스트는 정적타입의 언어.
스칼라타입 , 복합 타입 두가지로 나뉘어져있음

```rust
let guess : u32 = "42".parse().expect("Not a Number!");
```

### 스칼라 타입

하나의 값을 표현. 4가지의 타입이 이에 해당함

- 정수
- 부동 소수점 숫자
- boolean
- 문자

**정수형**

정수형 타입

![image](https://github.com/user-attachments/assets/437f915f-45af-4047-950a-3bfab55c8150)

    - 부호 없는 타입 : `u`
    - 부호 있는 타입 : `i`

정수형 리터럴

![image](https://github.com/user-attachments/assets/ae4e492a-0b3e-43c0-866e-f24530f6ed7b)

**부동 소수점**

두가지의 기본형을 가짐,기본 타입은 `f64`이며 모든 부동 소수점 타입은 부호가 있음

- `f32`: 32bit
- `f64`: 64bit

```rust
fn main() {
    let x = 2.0; // f64

    let y: f32 = 3.0; // f32
}
```

---

**boolean**

`true` , `false` 두 값을 가짐.
크기는 1byte

```rust
fn main() {
    let t = true;

    let f: bool = false; // 명시적인 타입 어노테이션
}
```

**문자**
`char`
문자열 리터럴은 큰따옴표`""`를 사용하지만 `char`는 작은 따옴표 사용 `''`
4바이트 크기, 유니코드 스칼라 값 표현

```rust
fn main() {
    let c = 'z';
    let z: char = 'ℤ'; // 명시적인 타입 어노테이션
    let heart_eyed_cat = '😻';
}
```

### 복합 타입

튜플(`tuple`)과 배열(`array`)

**튜플 타입**

- 다양한 타입의 여러 값을 묶어 하나의 복합 타입으로 만드는 방식
- 고정 된 길이 가짐 (크기 변경 불가능)

```rust
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

튜플로 부터 개별 값 얻어오는 예제

```rust
fn main() {
    let tup = (500, 6.4, 1);

    let (x, y, z) = tup;

    println!("The value of y is: {y}");
}

```

튜플로 부터 인덱스로 접근하는 예제

```rust
fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;

    let six_point_four = x.1;

    let one = x.2;
}

```

**배열 타입**

- 모든 요소가 같은 타입이여함
- 고정된 길이를 가짐 (다른 언어들과의 차이점)

```rust
fn main() {
    let a = [1, 2, 3, 4, 5];
}
```

요소 타입 명시 예제

```rust
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

모든 요소가 동일한 값으로 채워진 배열 초기화 예제

```rust
let a = [3; 5];
// let a = [3, 3, 3, 3, 3];
```
