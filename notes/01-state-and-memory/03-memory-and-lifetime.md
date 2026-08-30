# Memory and the Lifetime Problem

## Problem

Once State exists, a new problem appears: where should the information be stored, and when is it no
longer needed? Preserving a value is not enough; we must also determine how long it should remain
alive.

## Computational Need

A computer needs storage for State and a way to determine when that State should be created, used,
and released. Releasing memory too early breaks the program. Releasing it too late creates a memory
leak: memory that is no longer useful but has not been freed.

## Concept

**Memory** is the space used to store information. **Lifetime** is the period during which a value
or piece of State remains available.

When State is created, two important questions follow:

1. When should the State be created?
2. When is it no longer needed?

The conceptual path is:

```text
Computation
    ↓
Results must survive
    ↓
State
    ↓
State needs storage
    ↓
Memory
    ↓
Memory needs a Lifetime
    ↓
Cleanup / Deallocation
```

## Language Feature

The JavaScript runtime allocates memory for values and execution structures and manages their
continued lifetime or reclamation based on whether they remain reachable. The physical details
depend on the engine and execution conditions.

## Syntax

```js
const result = { value: 42 };

// As long as a path to result exists, the program can use it.
console.log(result.value);
```

## Personal Notes & REPL Verification

State answers the need to preserve a result. Memory introduces the problem of storing it, and
Lifetime introduces the problem of deciding how long to keep it. These concepts should not be
collapsed into one another.

| Question or hypothesis                                                         | REPL experiment                                                               | Observed result                                      | Updated understanding                                            |
| ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------------------- |
| Does leaving a binding’s scope prove that its memory was immediately released? | Create a value inside a function and preserve access to it through a closure. | The value can remain accessible through the closure. | Scope ending does not necessarily mean immediate memory release. |
