---
title: "Vinoc"
linkTitle: "vinoc"
description: >
  The Vino controller.
---

`vinoc` is the executable that speaks common Vino protocols. It signs and inspects wasm binaries & invokes and queries remote hosts and providers.

## USAGE

```sh
vinoc <SUBCOMMAND>
```

## Subcommands

### invoke

Invoke a component or schematic on a provider

### list

Query a provider for a list of its hosted components

### inspect

Inspect the claims of a signed WebAssembly module

### sign

Sign a WaPC component

### stats

Query a provider for its runtime statistics

### help

Prints this message or the help of the given subcommand(s)
