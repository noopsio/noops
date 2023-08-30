# NoOps Hello-World

## Prerequisites 

- Libssl `sudo apt install libssl-dev`
- GitHub Account

### Golang
-   [Go](https://go.dev/doc/install) >= 1.20 
-   [tinygo](https://tinygo.org/getting-started/install/linux/)

### Rust
- [Rust Toolchain](https://www.rust-lang.org/tools/install)
- Switch to Rust nightly <br>
`rustup default nightly`
- Cargo WebAssembly Compile Target <br>
`rustup target add wasm32-wasi`

## Hello-World

1. Initialize your Project <br>`noops init`
    [![demo](./tutorials/init_to_deploy/gifs/init.gif)](./tutorials/init_to_deploy/gifs/init.gif)
2. Login into the NoOps Cloud <br>`noops login`
3. Add your first function <br>`noops create FUNCTION_NAME`
    [![demo](./tutorials/init_to_deploy/gifs/create.gif)](./tutorials/init_to_deploy/gifs/create.gif)
4. The source code is created at ./YOUR_FUNCTION_NAME
5. Build the functions <br> `noops build`
FUNCTION_NAME`
    [![demo](./tutorials/init_to_deploy/gifs/build.gif)](./tutorials/init_to_deploy/gifs/build.gif)
6. Upload the project <br> `noops deploy`
FUNCTION_NAME`
    [![demo](./tutorials/init_to_deploy/gifs/deploy.gif)](./tutorials/init_to_deploy/gifs/deploy.gif)
7. Curl your functions with the supplied links, or use the browser <br> `curl YOUR_FUNCTION_LINK`
FUNCTION_NAME`
    [![demo](./tutorials/init_to_deploy/gifs/call.gif)](./tutorials/init_to_deploy/gifs/call.gif)

