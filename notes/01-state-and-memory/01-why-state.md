# Why Do We Need State?

## Problem

Sequential computations need to transfer information from the past into the future. Without State,
each instruction would effectively be independent of what happened before it. Multi-step
computations could not depend on previous results.

## Computational Need

A computer must preserve the result of one step so that later steps can use it. Without this
capability, computation would be limited to independent operations with no history.

## Concept

**State** is information that preserves a past result or current condition for use in the future.
Conceptually, the computation follows this path:

```text
Past
  ↓
Current State
  ↓
Future Computation
```

State is the bridge between what has already happened, the system’s current condition, and future
computation.

## Language Feature

In JavaScript, State can appear in values, bindings, objects, arrays, lexical environments, and
runtime execution structures. A variable is only one language tool for managing part of State; the
concept of State is more fundamental than a variable.

## Syntax

This example preserves the result of one step for use in the next step:

```js
let total = 10;
total = total + 5;

console.log(total); // 15
```

## Personal Notes & REPL Verification

My current understanding is that State answers the need to keep a past result alive for future
computation. It is not merely another name for a variable.

| Question or hypothesis                                      | REPL experiment                                                    | Observed result   | Updated understanding                                    |
| ----------------------------------------------------------- | ------------------------------------------------------------------ | ----------------- | -------------------------------------------------------- |
| Can a second computation depend on the result of the first? | `const first = 10; const second = first + 5; console.log(second);` | `15` was printed. | The second computation used State produced by the first. |
