---
title: "Publishing components"
linkTitle: "Publishing components"
weight: 9
description: >
  Store and run signed artifacts from an OCI registry.
---

Vino tools will automatically pull from an OCI registry if the passed filename isn't found on the local filesystem. If you don't have an OCI registry handy, you can start one easily with Docker.

```sh
docker run -it --rm -p 5000:5000 registry
```

{{% pageinfo %}}
_Note: This will spin up an insecure local registry. It's suitable for testing but production registries will need more configuration._
{{% /pageinfo %}}

### Publish your artifact

Run the following command to publish `build/my_component_s.wasm` to the path and tag `test/my-component:latest` on the registry we spun up at `127.0.0.1:5000`.

```sh
vinoc push 127.0.0.1:5000/test/my-component:latest build/my_component_s.wasm --insecure 127.0.0.1:5000
```

### Fetch your remote components

To run your components remotely all you do is pass the registry URL to vow in place of the filename we've used previously. `vow` will take care of fetching and caching the remote artifact.

```sh
$ vow run 127.0.0.1:5000/test/my-component:latest greet --latest --insecure 127.0.0.1:5000 -- \
 --input="Jane Doe"
{"output":{"value":"Hello Jane Doe"}}
```

Hopefully everything feels like it "just works" which is what Vino should always feel like. Now that we can make simple connections between local and remote components, it's time to step it up to more complex configurations. For that, we need schematics.
