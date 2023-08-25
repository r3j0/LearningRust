## 1. Getting Started

Rust 파일의 확장자는 .rs 이다.  
```bash
> rustc main.rs
> ./main
Hello, world!
```
컴파일 후 실행을 위해 다음 커맨드를 사용한다. ( .\main.exe )

```rs
fn main() {

}
```
함수 main을 정의한다. main 함수는 Rust 프로그램에서 제일 먼저 실행된다. 
현재 main 함수는 매개변수와 반환값이 없다. 함수 몸체는 { } 로 표시된다.

Rust 프로젝트의 표준 스타일을 따라가고 싶다면 [rustfmt](https://github.com/rust-lang/rustfmt) 를 설치할 수 있다.

```rs
println!("Hello, world!");
```
스크린에 글을 출력한다.
1. Rust는 indentation에서 Tab이 아닌 4 Spaces 를 사용한다.
2. `println!` 은 Rust macro 라고 불린다. `!` 가 일반 함수와는 다르게 매크로로 불리는 키워드임을 알아두자.
3. `"Hello, world!"` 문자열을 `println!` 의 인자로 전달한다.
4. 문장의 끝에는 세미콜론을 사용한다. 


별도 단계를 거쳐 컴파일 후 실행이 익숙하지 않을 수도 있다. Rust는 [Ahead-of-time compilation](https://en.wikipedia.org/wiki/Ahead-of-time_compilation) (AOT 컴파일) 언어로, Rust 를 설치하지 않아도 누군가에게 실행 파일을 주면 실행할 수 있다. 


프로젝트가 커질 때 모든 옵션을 관리하고 코드를 쉽게 공유하고 싶을 것이다. 실제 Rust 프로그램을 작성하는 데 도움이 되는 Cargo 를 알아보자.

Cargo는 Rust의 빌드 시스템이자 패키지 관리자이다. 대부분 이 도구를 사용하여 Rust Project를 관리한다. Cargo는 코드 구축, 코드가 의존하는 라이브러리 다운로드 및 라이브러리 구축과 같은 많은 작업을 처리한다. 복잡한 Rust 프로그램을 작성할수록 부속물을 추가해야 할 것이다. Cargo를 사용하여 프로젝트를 시작하면 훨씬 쉽게 부속물을 추가할 수 있다.

```bash
> cargo new hello_cargo
> cd hello_cargo
```

`hello_cargo` 라는 이름의 새로운 directory와 프로젝트를 생성한다. `cargo.toml` 파일과 src 폴더 안에 있는 `main.rs` 파일을 볼 수 있다. Git repository가 존재하는 곳에서 `cargo new`를 실행하면 Git 파일이 생성되지 않는다. 이는 `cargo new --vcs=git` 명령으로 재정의할 수 있다.

`cargo.toml` 파일은 [TOML](https://toml.io/en/) 형식이며, Cargo 의 구성 형식이다.
1. [package] 는 패키지를 구성하는 문장을 포함하는 섹션 헤딩이다. 더 정보를 추가하고 싶다면 다른 섹션을 추가할 수 있다.
2. [dependencies] 는 프로젝트의 dependencies 를 나열하는 섹션의 시작이다. Rust 에서 코드의 패키지들은 `crates` 라고 한다. 

```bash
> cargo build
```
hello_cargo 폴더에서 build를 진행해보자. 이 커맨드는 target/debug/hello_cargo 에 실행 파일을 생성한다. 
```bash
> ./target/debug/hello_cargo
```
다음 커맨드로 실행 파일을 실행할 수 있다. 처음 `cargo build` 를 실행하면 Cargo 가 Cargo.lock 파일을 생성한다. 이 파일은 프로젝트의 정확한 부속 버전을 추적한다.
`cargo run` 커맨드를 실행에 사용할 수 있다.

Cargo는 파일이 변경되지 않으면 이진 파일을 실행하기만 한다. 소스 코드가 수정되면 Cargo 는 프로젝트를 rebuild 하고 실행한다.

'cargo check' 라는 명령은 코드가 컴파일되는지 확인하기 위해 빠르게 코드를 확인하지만 실행 파일을 생성하지는 않는다.

- `cargo new`
- `cargo build`
- `cargo run`
- `cargo check`
- ./target/debug/hello_cargo

어느 운영체제든 동일한 커맨드를 가진다.

프로젝트를 Release 할 준비가 되면 `cargo build --release` 커맨드로 최적화된 상태로 컴파일할 수 있다. Rust 코드가 더 빨리 실행되지만 컴파일 시간이 길어진다.
```bash
> ./target/release/hello_cargo
Hello, My Practice World! Versdion 2
```

실제 존재하는 Git Repository를 clone 한 뒤 cargo build 할 수 있다.
```bash
> git clone example.org/someproject
> cd someproject
> cargo build
```