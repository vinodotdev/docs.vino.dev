---
title: "Create a new project"
linkTitle: "Create a new project"
weight: 3
description: >
  Using Yeoman to create a new WebAssembly provider
---

## Create an empty directory

```sh
$ mkdir my-component && cd my-component
```

## Run `yo vino`

```sh
$ yo vino
```

Yeoman will ask you several questions that it will use to bootstrap your project well.

{{% pageinfo %}}
_Note: The generated project comes with some recommended and default settings for Visual Studio Code users. Feel free to ignore, change, or remove them. They are not required to build the project._
{{% /pageinfo %}}

## Your first schema

Take note of the schema found in schemas/my-component.widl

```graphql
namespace "my-component"

type Inputs {
  input: string
}

type Outputs {
  output: string
}
```

This schema defines a component named `my-component` with one input port named `input` and one output port named `output`, both dealing with `string` data.

Let's change our component name to 'greet' so we have something slightly more meaningful. Your new schema should look like this:

```graphql
namespace "greet"

type Inputs {
  input: string
}

type Outputs {
  output: string
}
```
