# Getting started
Noops is a new approach to serverless application development. 

## Prerequisites 
### Dependencies
- openssl

### Golang
- [Go](https://go.dev/doc/install) >= 1.20 
- [tinygo](https://tinygo.org/getting-started/install/linux/)

### Rust
- [Rust Toolchain](https://www.rust-lang.org/tools/install)
- Switch to Rust nightly  
`rustup default nightly`
- Cargo WebAssembly Compile Target  
`rustup target add wasm32-wasi`


##  Initialize a Project
When initializing the project, a *noops.yaml* file is created. This is also called manifest and contains all project information.  
The following command creates the project manifest with the name *demo*.
```
noops init demo
```
Output:
```
demo successfully initialized
```

A look at the manifest shows that we have successfully initialized the project. At the moment, we do not have any handlers.
```yaml
project: demo
handlers: []
```

## Create a handler
A handler represents an HTTP handler of the project and can be configured individually. The strength of noops is that each handler can be written in a different programming language.

:warning: Note: *The creation of handlers is simplified by templates.  
Templates can be updated via `noops template update`.*

The following command creates a new handler called *hello-rust* and lists all installed templates from which one can be selected interactively. As the chosen name for the handler suggests, let's select the *Rust Hello World* template.  
```
noops create hello-rust
```
Output:
```
--- Creating  ---
Select a template:
> Name:         Rust Hello World
  Description:  A Hello World function in Rust
  Language:     Rust

  Name:         Rust Add Params
  Description:  A Function that adds path parameters as numerals
  Language:     Rust

  Name:         Golang Hello World
  Description:  A hello world function in Go
  Language:     Golang

  Name:         Golang Fibonacci
  Description:  A Fibonacci function in Go
  Language:     Golang
```

Another look into the manifest shows that our handler has been added successfully.
```yaml
project: demo
functions:
- name: hello-rust
  language: Rust
```

In addition, a new folder named *hello-rust* has been created which contains the selected template.
```
hello-rust
├── Cargo.toml
├── src
│  └── lib.rs
└── wit
   └── handler.wit
```


## Build the project
To build the project the following command is used.
Alternatively, only a single handler can be built. In this case, the name of the handler is added as a parameter to the build command.
```
noops build
```
Output:
```
--- Building project ---
[1/1] ✔️ hello-rust
```
After successful compilation a new *out* folder is created in the handler folder which contains the *handler.wasm*.
```
hello-rust
├── Cargo.lock
├── Cargo.toml
├── out
│  └── handler.wasm
├── src
│  └── lib.rs
├── target
│  ├── CACHEDIR.TAG
│  ├── release
│  └── wasm32-wasi
└── wit
   └── handler.wit
```

## Deploy the project
The deployment process consists of matching the already uploaded handlers and creating a so-called *deployment plan* which can consist of different deployment steps:
- new (+)
- change (~)
- delete (-)

If the deployment plan is approved, the project is deployed, the handlers are stored as endpoints and the routes are set up. 

:warning: Note: *To deploy to the noops cloud, you must first login via `noops login`.  
This triggers a GitHub authentication.*

The following command deploys the whole project.
Alternatively, only one handler can be deployed by adding the name of the handler as a parameter to the deploy command.
```
noops deploy
```
Output:
```
--- Deploying project ---
Changes:
        + hello-rust
[1/1] ✔️ Creating module hello-rust  
```

## Project status
To get information about the project the following command is used. This can also be applied to a single handler by appending the handler name to the command.
```
--- Showing Project ---
Name:           demo
Deployed:       true
Components:     1

Name:           hello-rust
Language:       Rust
Build:          true
Deployed:       true
Link:           https://app.noops.rocks/rvRb1EP66VX_Nk-OhNnep
```
Since the handler is deployed, a link to the endpoint is also provided. This can be used to call the endpoint.  
:warning: Note: *Do not forget to use the link that is displayed with your handler.*
```
curl https://app.noops.rocks/rvRb1EP66VX_Nk-OhNnep
```
Output:
```
Hello from Rust!
```


