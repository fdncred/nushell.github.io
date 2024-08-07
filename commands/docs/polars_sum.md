---
title: polars sum
categories: |
  expression
version: 0.96.0
expression: |
  Creates a sum expression for an aggregation or aggregates columns to their sum value.
usage: |
  Creates a sum expression for an aggregation or aggregates columns to their sum value.
---
<!-- This file is automatically generated. Please edit the command in https://github.com/nushell/nushell instead. -->

# `polars sum` for [expression](/commands/categories/expression.md)

<div class='command-title'>Creates a sum expression for an aggregation or aggregates columns to their sum value.</div>

## Signature

```> polars sum {flags} ```


## Input/output types:

| input | output |
| ----- | ------ |
| any   | any    |

## Examples

Sums all columns in a dataframe
```nu
> [[a b]; [6 2] [1 4] [4 1]] | polars into-df | polars sum
╭───┬────┬───╮
│ # │ a  │ b │
├───┼────┼───┤
│ 0 │ 11 │ 7 │
╰───┴────┴───╯

```

Sum aggregation for a group-by
```nu
> [[a b]; [one 2] [one 4] [two 1]]
    | polars into-df
    | polars group-by a
    | polars agg (polars col b | polars sum)
╭───┬─────┬───╮
│ # │  a  │ b │
├───┼─────┼───┤
│ 0 │ one │ 6 │
│ 1 │ two │ 1 │
╰───┴─────┴───╯

```
