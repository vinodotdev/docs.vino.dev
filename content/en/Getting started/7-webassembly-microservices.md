---
title: "Running your WebAssembly component as a microservice"
linkTitle: "WebAssembly Microservices"
weight: 7
description: >
  Use `vow` to turn any WebAssembly module into a standalone microservice for free.
---

To turn your WebAssembly module into a microservice, change the command you use with `vow` from `run` to `serve` and remove the extra flags. That's it.

```sh
$ vow serve ./build/my_component_s.wasm --port 8060
[2021-08-13T14:54:13Z][I] Starting insecure server on 127.0.0.1:8060
[2021-08-13T14:54:13Z][I] Waiting for ctrl-C
```

{{% pageinfo %}}
_Tip: Starting `vow serve` without providing `--port` will cause `vow` to choose a random, unused port._
{{% /pageinfo %}}

### Testing your microservice with `vinoc`

`vinoc` is the vino controller which can talk to providers (such as your WebAssembly module) over the Vino RPC protocol. Using the port from above, run `vinoc` to make the same request we made in the last step.

```sh
$ vinoc invoke --port=8060 concatenate  \
  --data 'left="Hello"' \
  --data 'right=" World"'
{"output":{"value":"Hello World"}}
```

Congratulations, you just got a command line tool and a streaming GRPC microservice with a few lines of Rust and a wasm file!

Getting functionality for free is what we live for at Vino. Next we're going to connect some components and see how we can start building.
