---
title: "Build and run your new WebAssembly component"
linkTitle: "Build and Run"
weight: 4
description: >
  Build and run your WebAssembly component with `vow`
---

## Build your component.

Build your component by running `make`

```sh
$ make
```

Make generates source code, builds your WebAssembly module, signs it with [`vinoc`] and stores both the signed and unsigned artifacts in a `/build` directory.

{{% pageinfo %}}
_Note: The build process also generates source code from your schema(s). Do not edit any that are prefixed with a "This is generated" warning or your changes will be lost on next build._
{{% /pageinfo %}}

## Run your component

Use [`vow`] to load your module and execute a component on the command line, sending the string `"my_input"` to the input port named `input`.

{{< tabpane >}}
{{< tab header="Bash" >}}
vow run ./build/my_component_s.wasm greet --data 'input="my_input"'
{{< /tab >}}
{{< tab header="Powershell" >}}
vow run ./build/my_component_s.wasm greet --data 'input=\"my_input\"'
{{< /tab >}}
{{< /tabpane >}}

If all has gone well, you will see nothing. Our component doesn't output anything so we don't get anything in our output. To convince ourselves that something is actually happening, pass `--trace` or `--debug` to vow for more output. You should see something similar to the below.

{{< tabpane >}}
{{< tab header="Bash" >}}
$ vow run ./build/my_component_s.wasm greet --data 'input="my_input"' --trace
[2021-08-13T14:20:33Z][t] Logger initialized
[2021-08-13T14:20:33Z][d] Loading wasm ./build/my_component_s.wasm
[2021-08-13T14:20:33Z][d] WASM:AS_FILE:./build/my_component_s.wasm
[2021-08-13T14:20:33Z][d] WASM:START:1 Threads
[2021-08-13T14:20:33Z][t] WASM:Wasmtime instance loaded in 337 μs
[2021-08-13T14:20:33Z][d] WASM:Wasmtime initialized in 3648 μs
[2021-08-13T14:20:33Z][d] PORT:'input', VALUE:'"my_input"'
[2021-08-13T14:20:33Z][t] WASM:INVOKE:[ofp://__direct.prov/greet]
[2021-08-13T14:20:33Z][t] WASM:INVOKE:greet:START
[2021-08-13T14:20:33Z][t] WASM:INVOKE:greet:FINISH
{{< /tab >}}
{{< tab header="Powershell" >}}
vow run ./build/my_component_s.wasm greet --data 'input=\"my_input\"' --trace
[2021-08-13T14:20:33Z][t] Logger initialized
[2021-08-13T14:20:33Z][d] Loading wasm ./build/my_component_s.wasm
[2021-08-13T14:20:33Z][d] WASM:AS_FILE:./build/my_component_s.wasm
[2021-08-13T14:20:33Z][d] WASM:START:1 Threads
[2021-08-13T14:20:33Z][t] WASM:Wasmtime instance loaded in 337 μs
[2021-08-13T14:20:33Z][d] WASM:Wasmtime initialized in 3648 μs
[2021-08-13T14:20:33Z][d] PORT:'input', VALUE:'"my_input"'
[2021-08-13T14:20:33Z][t] WASM:INVOKE:[ofp://__direct.prov/greet]
[2021-08-13T14:20:33Z][t] WASM:INVOKE:greet:START
[2021-08-13T14:20:33Z][t] WASM:INVOKE:greet:FINISH
{{< /tab >}}
{{< /tabpane >}}

{{% pageinfo %}}
_Note: The name of your component is dictated by the `namespace` definition in your schema. The filename and associated Rust module is dictated by the **filename** of your schema._
{{% /pageinfo %}}

In the next step we'll add logic to our component.

[`vinoc`]: /tools/vinoc/
[`vow`]: /tools/vow/
[`vino`]: /tools/vino/
