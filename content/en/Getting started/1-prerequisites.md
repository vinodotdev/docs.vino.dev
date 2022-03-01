---
title: "Prerequisites for the getting started guide"
linkTitle: "Prerequisites"
weight: 1
description: >
  Dependencies you may need to install for this guide
---

### Rust & Cargo

Vino can run WebAssembly built from any language, but the current code generation tools prioritize Rust above others and this guide expects a Rust development environment with Cargo.

Install rust & cargo via [rustup](https://rustup.rs/) for Windows, Mac, or Linux. Windows users may need to install the [C++ build tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) with the "Desktop development with C++" module.

### WebAssembly target for Rust

To build WebAssembly from Rust, you will need to install a suitable target for the compiler.

Install the wasm32 target via rustup using

```sh
rustup target add wasm32-unknown-unknown
```

### Node.js & npm

Vino's support scripts are written in JavaScript and some WIDL parsing and code generation depends on node.js.

Install node.js & npm via [nvm](https://github.com/nvm-sh/nvm) on Mac or Linux or [nvm-windows](https://github.com/coreybutler/nvm-windows/releases) on Windows.

### `tomlq`

[tomlq](https://github.com/jamesmunns/tomlq) is a command line parser for TOML files and Vino uses it to automatically populate command-line flags and Makefile rules.

Install `tomlq` with

```
cargo install tomlq
```

### `vino-codegen`

[vino-codegen](https://github.com/vinodotdev/codegen) is Vino's code generator for a wide variety of formats. `vino-codegen` is frequently used to automatically generate code from WIDL schemas.

Install `vino-codegen` via `npm install -g @vinodotdev/codegen`

### Yeoman & yo-vino

Yeoman is a popular project setup tool and Vino provides a generator that automates the creation of new Vino WebAssembly components.

Install yeoman's command line tool `yo` and Vino's generator with:

```sh
npm install -g yo generator-vino
```

## `make` on Windows

Vino and generated projects use Makefiles to automate builds and code generation. The easiest way to install `make` on Windows is via [Chocolatey](https://chocolatey.org/install).

```sh
$ choco install make
```

## Optional: `docker` or an existing OCI registry for publishing artifacts

Install docker from [docker.com](https://docs.docker.com/get-docker/).
