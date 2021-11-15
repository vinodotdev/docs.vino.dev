---
title: "Adding components"
linkTitle: "Adding components"
weight: 6
description: >
  Adding additional components to our module
---

A single component isn't always that useful and Vino providers give you the ability to collect like-functionality into a distributable bundle.

Before we think about writing any code, we have to define the contract first. Make a new `widl` file in the `schemas/` directory. Let's call it "concatenate.widl" and save it with the following:

```graphql {title="./schemas/concatenate.widl"}
namespace "concatenate"

type Inputs {
  left: string
  right: string
}

type Outputs {
  output: string
}
```

{{% pageinfo %}}
_Without knowing anything about the implementation, can you guess what this component will do? If you guessed that it is going combine two strings together as output, you're correct!_

_This scenario is contrived but it extends passed "Hello World" style tutorials and is an important part of programming on Vino. Components don't need to accept data they don't act on, so you won't often see many inputs nor complex types as input. You'll usually deal with small bits of data like strings and numbers. Component ports connect directly to each other in a graph (a [schematic](/concepts/terminology)), freeing each component to be laser focused on its purpose._
{{% /pageinfo %}}

### Generate the new code

The task `codegen` will generate all the necessary files based off the WIDL files found in `schemas/`. Now that we've added a schema we will need to run `make codegen` to generate new source code and files.

```sh
$ make codegen
```

### Add our concatenation logic

Add this rust code to the new `src/components/concatenate.rs` file.

```rust
use crate::generated::concatenate::*;

pub(crate) fn job(input: Inputs, output: Outputs) -> JobResult {
  output
    .output
    .send(&format!("{}{}", input.left, input.right))?;
  Ok(())
}
```

### Build and run our new component

Our component name needs to change and the input needs reflect that we're sending data on multiple ports, but otherwise running `vow` is the same as in the earlier steps.

{{< tabpane >}}
{{< tab header="Bash" >}}
$ make
$ vow run ./build/my_component_s.wasm concatenate -- --left=Hello --right=" World"
{"output":{"value":"Hello World"}}
{{< /tab >}}
{{< tab header="Powershell" >}}
TODO
{{< /tab >}}
{{< /tabpane >}}

Success! Collections of components are called "providers" in Vino lingo and our collection is now starting to feel like one.
