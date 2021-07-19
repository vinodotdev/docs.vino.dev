---
title: "Build and run your new WebAssembly component"
linkTitle: "Build and Run"
weight: 4
description: >
  Build and run your WebAssembly component with `vow`
---

## Build your component.

Build your component by running `make`

```shell
$ make
```

Make generates source code, builds your WebAssembly module, signs it with `vinoc` and stores both the signed and unsigned artifacts in a `/build` directory.

{{% pageinfo %}}
_Note: The build process also generates source code from your schema(s). Do not edit any that are prefixed with a "This is generated" header or your changes will be lost on next build._
{{% /pageinfo %}}

## Run your component

Use `vow` to load your module and execute a component on the command line, sending the string `"my_input"` to the input port named `input`.

```shell
$ vow run ./build/my_component_s.wasm greet '{"input":"my_input"}'
{}
```

If all has gone well, you will see a very (un)exciting empty JSON object as the output. Our component doesn't actually output anything so naturally we don't get anything in our output.

{{% pageinfo %}}
_Note: The name of your component is dictated by the `namespace` definition in your schema. The filename and associated Rust module is dictated by the **filename** of your schema._
{{% /pageinfo %}}

Next step is to add logic to our component!
