---
title: "Connecting components"
linkTitle: "Connecting components"
weight: 8
description: >
  Start connecting simple components on the command line.
---

The command line is a pipeline of streaming data where every component feeds directly into one other. To Vino it's like a schematic that never branches and it's a great way to test and experiment with small bits of logic.

The following command pipes one execution of vow into another, both running the same `wasm` but pointing to different components.

{{< tabpane >}}
{{< tab header="Bash" >}}
$ vow run ./build/my_component_s.wasm concatenate \
 --data 'left="Jane"' \
 --data 'right=" Doe"' | \
 vow run ./build/my_component_s.wasm greet
{"output":{"value":"Hello Jane Doe"}}
{{< /tab >}}
{{< tab header="Powershell" >}}
vow run ./build/my_component_s.wasm concatenate \
 --data 'left=\"Jane\"' \
 --data 'right=\" Doe\"' | \
 vow run ./build/my_component_s.wasm greet
{"output":{"value":"Hello Jane Doe"}}
{{< /tab >}}
{{< /tabpane >}}

`vow` output is directly pipable to another execution of `vow`! You can string together any number of connections to experiment, test, or build on the command line.

{{% pageinfo %}}
_Note: `vow` connects output from a named port to an incoming port of the same name with one exception shown above. Data coming out of a port named `output` will be mapped to a port named `input` on the downstream component. This is a common practice and makes CLI testing more intuitive. Turn it off by passing the `--raw` flag to `vow`._
{{% /pageinfo %}}

### Connecting to remote components

Every tool in the Vino suite talks the same language so switching from one to another should be seamless. This means that you can pipe from `vow` running WebAssembly locally to `vinoc` which connects to any remote provider and then back to `vow` again.

Start up WebAssembly microservice to use it as a sample microservice...

```sh
$ vow serve ./build/my_component_s.wasm --port 8060
```

...then run the following command...

{{< tabpane >}}
{{< tab header="Bash" >}}
$ vow run ./build/my_component_s.wasm concatenate \
 --data 'left="Jane"' \
 --data 'right=" Doe"' | \
 vinoc invoke --port 8060 greet
{"output":{"value":"Hello Jane Doe"}}
{{< /tab >}}
{{< tab header="Powershell" >}}
vow run ./build/my_component_s.wasm concatenate \
 --data 'left=\"Jane\"' \
 --data 'right=\" Doe\"' | \
 vinoc invoke --port 8060 greet
{"output":{"value":"Hello Jane Doe"}}
{{< /tab >}}
{{< /tabpane >}}

In the next step we will publish our artifact to a remote registry so we can access it anywhere.
