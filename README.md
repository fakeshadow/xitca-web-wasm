# a http/1 server example targeting wasi with xitca-web web framework

## Requirement

-. nightly Rust.

-. [wasmtime](https://docs.wasmtime.dev/).

## How to

-. install wasmtime cli. See doc for how to: <https://docs.wasmtime.dev/cli-install.html>

-. compile the project with `RUSTFLAGS="--cfg tokio_unstable" cargo build --release --target wasm32-wasi`

-. run the compiled wasm file with `wasmtime run ./target/wasm32-wasi/release/xitca-web-wasm.wasm --tcplisten 127.0.0.1:8080 --env FD_COUNT=3`
