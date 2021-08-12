---
title: "Terminology"
linkTitle: "Terminology"
description: >
  Providers, modules, components, schematics, oh my!
---

### Components

Vino _components_ are the smallest unit of logic in Vino and can be thought of like a common `function` in any other platform. Components have input and output ports that can connect to any other component.

### Ports

Vino _ports_ are asynchronous streams of versioned, chunked tuples.

In everyday terms, Vino's ports are the inputs and outputs to components. They can represent any kind of data, from simple to complex, asynchronous to synchronous, successful computation to internal error or edge cases. Vino's ports are what make it possible to connect arbitrary components.

### Providers

Vino _providers_ are collections of components. If components are functions, providers are libaries.

### Schematics

Vino _schematics_ are the configuration that defines how component connect, what namespace a provider is registered under, etc. Schematics have inputs and outputs as well and thus can also be treated like components.

### Networks

Vino _networks_ are collections of schematics. Since schematics are components, networks are also providers and can be exposed as such to be referenced by other schematics.

### Runtime

The Vino _runtime_ is the library implementation that manages a network, its schematics, and exposes internal components.

### Hosts

A Vino _host_ is an implementation of a runtime that exposes a network to connections and requests.

### WaPC

The WebAssembly Procedure Call project is an open source standard for communicating in and out of WebAssembly modules.

### WIDL

WIDL (WebAssembly Interface Definition Language) is a specification for defining the interface into and out of WebAssembly modules. It is loosely based on GraphQL and is generic enough to use for non-WebAssembly purposes.

### VRPC

VRPC stands for "Vino Remote Procedure Call" and is the core set of services and types that a Vino provider must implement to connect to other providers. The external intreface is implemented as a streaming GRPC (Google RPC) server.

### Manifest

Manifests are configuration definitions for different parts of Vino.

#### Host Manifest

The configuration of a Vino host

#### Network Manifest

The configuration of a Vino network, its schematics, providers, et al.

#### Schematic Manifest

A configuration for a single schematic.

### WebAssembly Module

A "WebAssembly Module" is a generic term for any compiled WebAssembly but when used in Vino's context it refers to a WebAssembly implementation of a Vino provider, a collection of components.

### `vino`

The `vino` command is the executable implementation of a Vino host. It can start a network and schematics from a host manifest.

### `vinoc`

`vinoc` (pronounced **vih**-nik) is the Vino controller. It can query running hosts or providers that implement VRPC and can sign or inspect WebAssembly modules.

### `vow`

`vow` is the executable that can run WebAssembly modules or wrap them into a standalone VRPC microservice.
