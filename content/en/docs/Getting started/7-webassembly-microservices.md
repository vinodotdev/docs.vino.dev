---
title: "Running your WebAssembly component as a microservice"
linkTitle: "WebAssembly Microservices"
weight: 6
description: >
  Use `vow` to turn any WebAssembly module into a standalone microservice for free.
---

To turn your WebAssembly module into a microservice, change the command you use with `vow` from `run` to `serve` and remove the extra flags. That's it.

```sh
$ vow serve ./build/my_component_s.wasm
Server bound to 127.0.0.1:45239
```

{{% pageinfo %}}
_Tip: The port above is automatically generated. Pass a port with `--port` to specify your own._
{{% /pageinfo %}}

### Testing your microservice with `vinoc`

`vinoc` is the vino controller which can talk to providers (such as your WebAssembly module) over the Vino RPC protocol. Using the port from above, run `vinoc` to make the same request we made in the last step.

```sh
$ vinoc invoke --port=45239 concatenate \
      '{"left":"Hello","right":" world"}'
{"output":{"error_kind":"None","value":"Hello world"}}
```
