# State Is Deeper Than a Variable

## Problem

If we equate State with a variable, our mental model becomes limited to language syntax and cannot
explain the state of an entire system.

## Computational Need

To understand program execution, we need to describe the current condition of a system at multiple
levels—from hardware and the runtime to the data the program directly manipulates.

## Concept

State is the information that describes a system’s current condition. It is not limited to one named
value in source code.

For example, the CPU has State: registers, the program counter, flags, and more. A program also has
State: variables, objects, arrays, the call stack, and other execution structures. An operating
system has State as well.

Therefore, **State is a more fundamental concept than a variable**. A variable is only one tool for
managing part of State.

## Language Feature

JavaScript models some State through bindings and the values associated with them. The runtime also
manages state such as the call stack and lexical environments during execution.

## Syntax

```js
let x = 10;
```

`x` is a language-level binding that is currently associated with the value `10`. This line
represents only one part of the program’s State, not all of it.

## Personal Notes & REPL Verification

The key distinction is that a variable is a language-level response to part of the State problem. I
should not reduce the larger conceptual model to the syntax of a declaration.

| Question or hypothesis                   | REPL experiment               | Observed result                | Updated understanding                                                                       |
| ---------------------------------------- | ----------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------- |
| Is a program’s State only its variables? | `let x = 10; console.log(x);` | The value `10` was observable. | A variable is part of the State visible at the language level, not the whole runtime state. |
