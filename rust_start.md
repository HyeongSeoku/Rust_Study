## Docs

[Hello, World! - The Rust Programming Language](https://doc.rust-kr.org/ch01-02-hello-world.html)

### Install

```bash
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

### Hello world

```rust
fn main(){
    println!("Hello, world")
}
```

- main은 특별한 함수 - 러스트 실행 프로그램에서 가장 먼저 실행됨

\*rustfmt : 러스트 코드 포매팅 (rust 기본 배포에 포함되어 설치되었음)

!가 붙으면 매크로 함수

### 컴파일과 실행은 별개의 과정

**컴파일**

```bash
rustc [파일 명.rs]
```

**실행**

```bash
[파일명]
```

---

### Cargo

> 러스트 빌드 시스템 및 패키지 매니저
> (node의 npm과 같은)

### Cargo -build

```bash
cargo build
```

결과물

<img width="441" alt="스크린샷 2024-07-15 오후 12 54 11" src="https://github.com/user-attachments/assets/6a58e43c-8502-4394-b0c0-fedc110c15a1">

**실행**

```bash
./target/debug/[프로젝트 디렉토리명]
```

### Cargo run

```bash
cargo run
```

해당 명령어 진행시 Cargo 는 파일 변경 사항이 없으면 기존 바이너리를 그대로 실행함

즉, 빌드 과정은 건너뛰고 실행만 진행.

파일 변경점이 있을 경우 빌드 이후 실행 진행

### Cargo check

```bash
cargo check
```

실행 파일은 생성하지 않고 작성한 소스가 문제없이 컴파일되는지만 빠르게 확인하는 명령어

### 요약

- `cargo new` : 새로운 프로젝트 생성
- `cargo build` : 프로젝트를 빌드
- `cargo run` : 프로젝트 빌드 & 실행
- `cargo check` : 바이너리 생성하지 않고 프로젝트 에러 체크

### cargo build --release

```bash
cargo build --release
```

**일반 빌드와 차이점**

- *target/debug* 가 아닌 *target/release* 에 실행 파일이 생성됨
- 컴파일 시 최적화를 진행하여 컴파일이 오래 걸리는 대신 러스트 코드가 더 빠르게 작동

**⭐️빌드 종류가 나뉜 이유**

개발 - 빌드 잦음, 따라서 빌드 속도는 빠르면 빠를수록 좋음

릴리즈 - 잦은 빌드 필요없음. 따라서 빌드 속도보다는 프로그램의 작동 속도가 중요

> 작성한 코드의 작동 속도 벤치마킹 시 릴리즈 빌드를 기준으로 진행
