# Stack and Heap: Two Responses to Lifetime

## Problem

Not all data has the same Lifetime. Some data is tied to a function call, while other State must
survive independently of the call stack. Using one strategy for both patterns makes memory
management difficult or inefficient.

## Computational Need

The runtime needs different allocation and reclamation patterns: one that is fast and predictable
for temporary data, and another that is more flexible for data whose lifetime is independent of the
call stack.

## Concept

**Stack** fits a data-lifetime pattern that follows LIFO—last in, first out. Each function call can
create a stack frame, and the frame can be removed when that call ends.

**Heap** fits State whose Lifetime is more independent and less predictable than a function call. It
offers more flexibility, but allocation and reclamation are more complex.

| Feature      | Stack                                  | Heap                                     |
| ------------ | -------------------------------------- | ---------------------------------------- |
| Main pattern | LIFO                                   | More flexible                            |
| Lifetime     | Usually function-bound and predictable | More independent and indeterminate       |
| Allocation   | Simple and fast                        | More complex                             |
| Deallocation | Usually when a frame is popped         | Requires memory management               |
| Suitable for | Call frames and temporary data         | Objects and data with variable lifetimes |

## Language Feature

In JavaScript, Stack and Heap are primarily conceptual models for understanding the runtime, not
exact contracts about the physical location of every value. An engine may keep a value in a
register, optimize it, manage an object differently, or eliminate an allocation.

We should not treat this statement as a precise JavaScript rule: “Every primitive is on the Stack
and every object is on the Heap.”

## Syntax

```js
function createFrame() {
  const temporaryValue = 10;
  return temporaryValue;
}

const result = createFrame();
console.log(result); // 10
```

This syntax does not guarantee a physical storage location. It is useful for reasoning about the
lifetime of a function and its data.

## Personal Notes & REPL Verification

Stack and Heap should be understood as engineering responses to different Lifetime patterns, not as
fixed labels for the physical location of every JavaScript value.

| Question or hypothesis                                              | REPL experiment                                                                   | Observed result                                                              | Updated understanding                                                                   |
| ------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| Does a JavaScript type alone determine a value’s physical location? | Compare a primitive and an object without assuming engine implementation details. | The language syntax guarantees observable behavior, not a physical location. | The Stack/Heap model is conceptual and should not be confused with a physical contract. |
