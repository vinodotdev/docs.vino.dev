---
title: "Installing Vino"
linkTitle: "Installing Vino"
weight: 2
description: >
  How to install `vino`, `vow`, & `vinoc`
---

## Pre-build binary installation

Head over to [releases.vino.dev](https://releases.vino.dev/) to get the latest version of the Vino tools for your platform

Unless you are developing on Vino, you should stick with the pre-built binaries.

## Building from source

{{% pageinfo %}}
_Note: The source code for Vino tools is available to limited users at the moment. Vino and its tools will be open sourced once the Vino runtime is mature enough to be released publicly._
{{% /pageinfo %}}

`make install` will build everything in the Vino monorepo and install any binaries into your `~/.cargo/bin` directory.

```sh
$ git clone https://github.com/vinodotdev/vino
$ cd vino && make install
```
