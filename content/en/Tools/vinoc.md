---
title: "Vinoc"
linkTitle: "vinoc"
description: >
  The Vino controller.
---

`vinoc` is the executable that speaks common Vino protocols. It signs and inspects wasm binaries & invokes and queries remote hosts and providers.

```
vinoc 0.3.1
Vino controller

USAGE:
    vinoc <SUBCOMMAND>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

SUBCOMMANDS:
    help       Prints this message or the help of the given subcommand(s)
    inspect    Inspect the claims of a signed WaPC component
    invoke     Invoke a component or schematic on a provider
    list       Query a provider for a list of its hosted components
    sign       Sign a WaPC component
    stats      Query a provider for its runtime statistics
```
