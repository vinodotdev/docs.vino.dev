---
title: "Prerequisites for the getting started guide"
linkTitle: "Prerequisites"
weight: 1
description: >
  Dependencies you may need to install for this guide
---

### Rust & Cargo

To build Vino's core components you will need Rust & Cargo.

Install rust & cargo via [rustup](https://rustup.rs/)

### WebAssembly target for Rust

To build WebAssembly from Rust, you will need to install a suitable target for the compiler.

Install the wasm32 target via rustup using `rustup target add wasm32-unknown-unknown`

### Node.js & npm

Vino's support scripts are written in JavaScript and some WIDL parsing and code generation depends on node.js.

Install node.js & npm via [nvm](https://github.com/nvm-sh/nvm)

### `tomlq`

[tomlq](https://github.com/jamesmunns/tomlq) is a command line parser for TOML files and Vino uses it to automatically populate command-line flags and Makefile rules.

Install `tomlq` with `cargo install tomlq`

### `widl-template`

[widl-template](https://github.com/jsoverson/widl-template) is a templating tool that uses WIDL files as input for Handlebars templates. Vino uses `widl-template` to generated code and documentation for its manifest formats.

Install `widl-template` via `npm install -g widl-template`

### `vino-codegen`

[vino-codegen](https://github.com/vinodotdev/codegen) is Vino's code generator for a wide variety of formats. `vino-codegen` is frequently used to automatically generate code from WIDL schemas.

Install `vino-codegen` via `npm install -g @vinodotdev/codegen`

### Yeoman & yo-vino

Yeoman is a popular project setup tool and Vino provides a generator that automates the creation of new Vino WebAssembly components.

Install yeoman's command line tool `yo` via `npm install -g yo`

Install the Vino generator via `npm install -g generator-vino`
