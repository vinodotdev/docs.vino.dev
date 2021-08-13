---
title: "Prerequisites for the getting started guide"
linkTitle: "Prerequisites"
weight: 1
description: >
  Dependencies you may need to install for this guide
---

### Rust & Cargo

Vino can run WebAssembly built from any language, but the current code generation tools prioritize Rust above others and this guide expects a Rust development environment with Cargo.

Install rust & cargo via [rustup](https://rustup.rs/) via

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### WebAssembly target for Rust

To build WebAssembly from Rust, you will need to install a suitable target for the compiler.

Install the wasm32 target via rustup using

```sh
rustup target add wasm32-unknown-unknown
```

### Node.js & npm

Vino's support scripts are written in JavaScript and some WIDL parsing and code generation depends on node.js.

Install node.js & npm via [nvm](https://github.com/nvm-sh/nvm):

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash

# Reload your shell to get nvm added to your $PATH

exec $SHELL

# Use nvm to install the latest LTS node and make it the default

nvm install --lts --default
```

### `tomlq`

[tomlq](https://github.com/jamesmunns/tomlq) is a command line parser for TOML files and Vino uses it to automatically populate command-line flags and Makefile rules.

Install `tomlq` with

```
cargo install tomlq
```

<!--
### `widl-template`

[widl-template](https://github.com/jsoverson/widl-template) is a templating tool that uses WIDL files as input for Handlebars templates. Vino uses `widl-template` to generated code and documentation for its manifest formats.

Install `widl-template` with

```
npm install -g widl-template
``` -->

### `vino-codegen`

[vino-codegen](https://github.com/vinodotdev/codegen) is Vino's code generator for a wide variety of formats. `vino-codegen` is frequently used to automatically generate code from WIDL schemas.

Install `vino-codegen` via `npm install -g @vinodotdev/codegen`

### Yeoman & yo-vino

Yeoman is a popular project setup tool and Vino provides a generator that automates the creation of new Vino WebAssembly components.

Install yeoman's command line tool `yo` and Vino's generator with:

```sh
npm install -g yo generator-vino
```
