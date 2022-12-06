# a http/1 server example targeting wasi with xitca-web web framework

## Requirement

- [Rust](https://www.rust-lang.org/)

- [wasmtime](https://docs.wasmtime.dev/)

## Setup
- prepare Rust language.
  - install language. <https://www.rust-lang.org/tools/install>
  - switch to nightly compiler.
    ```commandline
    rustup default nighlty
    ```
  - add wasi target.
    ```commandline
    rustup target add wasm32-wasi
    ```
- install wasmtime cli. <https://docs.wasmtime.dev/cli-install.html>
- clone project.
  ```commandline
  git clone https://github.com/fakeshadow/xitca-web-wasm
  cd xitca-web-wasm
  ```
- compile project.
  - unix
    ```bash
    RUSTFLAGS="--cfg tokio_unstable" cargo build --release --target wasm32-wasi
    ```
  - windows
    ```commandline
    set RUSTFLAGS=--cfg tokio_unstable
    cargo build --release --target wasm32-wasi
    ```
- (optional) optimize compiled wasm file. <https://github.com/WebAssembly/binaryen>    
- run compiled wasm file.
  ```commandline
  wasmtime run ./target/wasm32-wasi/release/xitca-web-wasm.wasm --tcplisten 127.0.0.1:8080 --env FD_COUNT=3
  ```
- open browser and visit <http://127.0.0.1:8080>  