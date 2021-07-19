---
title: "Wiring your component into a schematic"
linkTitle: "Schematics"
weight: 7
description: >
  Bringing it all together
---

TODO: Writeup

```sh
$ touch manifest.yaml
```

Manifest.yaml:

```yaml
---
version: "0"
network:
  providers:
    - namespace: my_component
      kind: WaPC
      reference: ./build/my_component_s.wasm
  schematics:
    - name: hello_world
      components:
        greet:
          id: my_component::greet
        concatenate:
          id: my_component::concatenate
      connections:
        - <>[first_name] => concatenate[left]
        - <>[last_name] => concatenate[right]
        - concatenate[output] => greet[input]
        - greet[output] => <>
```

Run schematic directly

```sh
vino run manifest.yaml -d greet_me \
  '{"first_name": "Jarrod", "last_name":" Overson"}'
```

Start vino as a persistent host

```sh
$ vino start manifest.yaml
[2021-07-19 20:58:14] Manifest applied
[2021-07-19 20:58:14] Starting insecure server on 127.0.0.1:8060
[2021-07-19 20:58:14] Bound to 127.0.0.1:8060
[2021-07-19 20:58:14] Waiting for Ctrl-C
```

Command:

```sh
$ vinoc invoke --port=8060 greet_me \
  '{"first_name": "Jarrod", "last_name":" Overson"}'
{"output":{"error_kind":"None","value":"Hello Jarrod Overson"}}
```
