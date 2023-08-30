# NoOps
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

## CLI Commands

- noops 

## Hello-World

1. Initialize your Project -- `noops init`
    [![init](./tutorials/init_to_deploy/gifs/init.gif)](./tutorials/init_to_deploy/gifs/init.gif)
2. Login into the NoOps Cloud `noops login`
3. Add your first function -- `noops create FUNCTION_NAME`
    [![create](./tutorials/init_to_deploy/gifs/create.gif)](./tutorials/init_to_deploy/gifs/create.gif)
4. The source code is created at ./YOUR_FUNCTION_NAME
5. Build the functions -- `noops build`
FUNCTION_NAME`
    [![build](./tutorials/init_to_deploy/gifs/build.gif)](./tutorials/init_to_deploy/gifs/build.gif)
6. Upload the project -- `noops deploy`
FUNCTION_NAME`
    [![deploy](./tutorials/init_to_deploy/gifs/deploy.gif)](./tutorials/init_to_deploy/gifs/deploy.gif)
7. Curl your functions with the supplied links, or use the browser -- `curl YOUR_FUNCTION_LINK`
FUNCTION_NAME`
    [![call](./tutorials/init_to_deploy/gifs/call.gif)](./tutorials/init_to_deploy/gifs/call.gif)

