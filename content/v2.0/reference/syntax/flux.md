---
title: Flux syntax
list_title: Flux
description: >
  Flux is a functional data scripting language designed for querying, analyzing, and acting on data.
menu:
  v2_0_ref:
    parent: Syntax
    name: Flux
    identifier: flux-syntax
weight: 101
v2.0/tags: [syntax, flux]
---

Flux is a functional data scripting language designed for querying, analyzing, and acting on data.

## Flux design principles
Flux takes a functional approach to data exploration and processing, but is designed
to be usable, readable, flexible, composable, testable, contributable, and shareable.

The following example returns the average CPU usage per minute over the last hour.

```js
from(bucket:"example-bucket")
  |> range(start:-1h)
  |> filter(fn:(r) =>
    r._measurement == "cpu" and
    r.cpu == "cpu-total"
  )
  |> aggregateWindow(every: 1m, fn: mean)
```

## Flux documentation
For more information about Flux syntax, packages, and functions, see:

- [Get started with Flux](/v2.0/reference/flux/)
- [Flux standard library](/v2.0/reference/flux/stdlib/)
- [Flux language specification](/v2.0/reference/flux/language/)
