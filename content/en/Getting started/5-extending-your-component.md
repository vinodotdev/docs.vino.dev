---
title: "Adding logic to your component"
linkTitle: "Adding logic"
weight: 5
description: >
  How to work with component ports
---

To get our component doing something we can see, add to `./src/components/my_component.rs` so that it looks like the following:

```rs
use wapc_guest::prelude::*;

use crate::generated::my_component::*;

pub(crate) fn job(input: Inputs, output: Outputs) -> HandlerResult<()> {
  let greeting = format!("Hello {}", input.input);
  output.output.send(greeting)?;
  Ok(())
}
```

Take note of these lines:

```rust
let greeting = format!("Hello {}", input.input);
output.output.send(greeting)?;
```

The first line uses Rust's `format!()` macro to format our input string into a suitable greeting. If you're new to Rust, this is idiomatic Rust, not Vino. The second line takes that greeting string and pushes it to the output port named `output`.

{{% pageinfo %}}
_Tip: Change the port names in your schema WIDL and rebuild your component to see how the code generation reflects the changes._
{{% /pageinfo %}}

Build and run your component with the new logic to see the output:

```sh
$ make
$ vow run ./build/my_component_s.wasm greet '{"input":"my_input"}'
{"output":{"error_kind":"None","value":"Hello my_input"}}
```

{{% pageinfo %}}
_Tip: Change the `input.input` expression to something like `input.input.to_uppercase()` to see how modules can act on data as it comes through._
{{% /pageinfo %}}

{{% pageinfo %}}

#### Note: `vow` and `vinoc`'s JSON output is not final

_Vino's output ports can deliver multiple messages for a single batch of inputs and are normally represented as a stream. The JSON output above is a simplified representation of these streams more suitable. The expectation is that this is more suitable for CLI scripting and testing but that needs to be proven before this format can be considered stable._
{{% /pageinfo %}}

The next tutorial goes over how to add additional components to our WebAssembly module.
