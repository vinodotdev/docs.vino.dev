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

```sh
vow run ./build/my_component_s.wasm greet -- --input="my_input"
```

If all has gone well, you will see nothing. Our component doesn't output anything so we don't get anything in our output. To convince ourselves that something is actually happening, pass `--trace` or `--debug` to [`vow`] for more output. Remember to add the flag before the `--` which separates arguments for [`vow`] vs arguments destined for the executed module. You should see something similar to the below.

```sh
$ vow run ./build/my_component_s.wasm greet --trace -- --input="my_input"
2021-11-15T15:56:42 TRACE Logger initialized
2021-11-15T15:56:42 DEBUG Loading wasm ./build/my_component_s.wasm
2021-11-15T15:56:42 DEBUG LOAD:AS_FILE:./build/my_component_s.wasm
2021-11-15T15:56:42 TRACE WASM:Wasmtime instance loaded in 2539 μs
2021-11-15T15:56:42 DEBUG WASM:Wasmtime initialized in 3285 μs
2021-11-15T15:56:42 DEBUG Spawning host
2021-11-15T15:56:42 DEBUG Input 'my_input' for argument 'input' is not valid JSON. Wrapping it with quotes to make it a valid string value.
2021-11-15T15:56:42 TRACE WASM:INVOKE:[ofp://__direct.prov/greet]
2021-11-15T15:56:42 DEBUG Invoking from pool
2021-11-15T15:56:42 DEBUG WASM:INVOKE[greet]:ID[1835346468]:PAYLOAD{"input": [168, 109, 121, 95, 105, 110, 112, 117, 116]}
2021-11-15T15:56:42 TRACE WASM:INVOKE[greet]:ID[1835346468]:START
2021-11-15T15:56:42 TRACE WASM:INVOKE[greet]:ID[1835346468]:FINISH[26 μs]
2021-11-15T15:56:42 DEBUG WASM:INVOKE[greet]:ID[1835346468]:RESULT:Ok([192])
```

{{% pageinfo %}}
_Note: The name of your component is dictated by the `namespace` definition in your schema. The filename is normalized based on best practices for the target language._
{{% /pageinfo %}}

In the next step we'll add logic to our component.

[`vinoc`]: /tools/vinoc/
[`vow`]: /tools/vow/
[`vino`]: /tools/vino/
