---
title: "Adding components"
linkTitle: "Adding components"
weight: 6
description: >
  Adding additional components to our module
---

A single component isn't always that useful and Vino providers give you the ability to collect like-functionality into a distributable bundle.

Before we think about writing any code, we have to define the contract first. Make a new `widl` file in the `schemas/` directory. Let's call it "concatenate.widl" and save it with the following:

```sh
$ touch schemas/concatenate.widl
```

```graphql
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

_That scenario sounds silly but the self-describing nature of Vino components is an important one. Since ports can connect to anything and components aren't sequential lists of commands (i.e. functions), each component can be laser focused on its purpose. You don't need to pass unrelated data just to propagate it to a downstream consumer._
{{% /pageinfo %}}

### Generate the new code

The task `codegen` will generate all the necessary files based off the WIDL files found in `schemas/`. Now that we've added a schema we will need to run `make codegen` to generate new source code and files.

```sh
$ make codegen
```

### Add our concatenation logic

Add this rust code to the new `src/components/concatenate.rs` file.

```rust
use wapc_guest::prelude::*;

use crate::generated::concatenate::*;

pub(crate) fn job(input: Inputs, output: Outputs) -> HandlerResult<()> {
  output
    .output
    .send(format!("{}{}", input.left, input.right))?;
  Ok(())
}
```

### Build and run our new component

Our component name needs to change and the input needs reflect that we're sending data on multiple ports, but otherwise running `vow` is the same as in the earlier steps.

```sh
$ make
$ vow run ./build/my_component_s.wasm concatenate '{"left":"Hello","right":" world"}'
{"output":{"error_kind":"None","value":"Hello world"}}
```

Success! Collections of components are called "providers" in Vino lingo and our collection is now starting to feel like one.
