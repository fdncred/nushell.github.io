---
title: polars contains
categories: |
  dataframe
version: 0.96.0
dataframe: |
  Checks if a pattern is contained in a string.
usage: |
  Checks if a pattern is contained in a string.
---
<!-- This file is automatically generated. Please edit the command in https://github.com/nushell/nushell instead. -->

# `polars contains` for [dataframe](/commands/categories/dataframe.md)

<div class='command-title'>Checks if a pattern is contained in a string.</div>

## Signature

```> polars contains {flags} (pattern)```

## Parameters

 -  `pattern`: Regex pattern to be searched


## Input/output types:

| input | output |
| ----- | ------ |
| any   | any    |

## Examples

Returns boolean indicating if pattern was found
```nu
> [abc acb acb] | polars into-df | polars contains ab
╭───┬───────╮
│ # │   0   │
├───┼───────┤
│ 0 │ true  │
│ 1 │ false │
│ 2 │ false │
╰───┴───────╯

```
