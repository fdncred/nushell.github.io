---
title: polars filter
categories: |
  lazyframe
version: 0.104.0
lazyframe: |
  Filter dataframe based in expression.
usage: |
  Filter dataframe based in expression.
editLink: false
contributors: false
---
<!-- This file is automatically generated. Please edit the command in https://github.com/nushell/nushell instead. -->

# `polars filter` for [lazyframe](/commands/categories/lazyframe.md)

<div class='command-title'>Filter dataframe based in expression.</div>

::: warning This command requires a plugin
The `polars filter` command resides in the `polars` plugin.
To use this command, you must install and register `nu_plugin_polars`.
See the [Plugins](/book/plugins.html) chapter in the book for more information.
:::


## Signature

```> polars filter {flags} (filter expression)```

## Parameters

 -  `filter expression`: Expression that define the column selection


## Input/output types:

| input | output |
| ----- | ------ |
| any   | any    |
## Examples

Filter dataframe using an expression
```nu
> [[a b]; [6 2] [4 2] [2 2]] | polars into-df | polars filter ((polars col a) >= 4)
╭───┬───┬───╮
│ # │ a │ b │
├───┼───┼───┤
│ 0 │ 6 │ 2 │
│ 1 │ 4 │ 2 │
╰───┴───┴───╯

```

Filter dataframe for rows where dt is within the last 2 days of the maximum dt value
```nu
> [[dt val]; [2025-04-01 1] [2025-04-02 2] [2025-04-03 3] [2025-04-04 4]] | polars into-df | polars filter ((polars col dt) > ((polars col dt | polars max | $in - 2day)))
╭───┬─────────────┬─────╮
│ # │     dt      │ val │
├───┼─────────────┼─────┤
│ 0 │ 3 weeks ago │   3 │
│ 1 │ 3 weeks ago │   4 │
╰───┴─────────────┴─────╯

```
