# Reachability and Garbage Collection

## Problem

In the Heap, we cannot simply say, “Delete the last thing that was created.” An older object may
still be needed while a newer object is no longer useful. Creation order is therefore not a reliable
reclamation rule.

## Computational Need

The runtime must determine which objects are still reachable through valid paths from the active
program and which objects have no remaining use. It must then make the space occupied by unreachable
objects available again.

## Concept

**Reachability** means that an object can still be accessed through active roots and references.
Conceptually:

```text
Still reachable?
      ↓
YES → keep
NO  → reclaim
```

This need leads to a **Garbage Collector**: a system that identifies unreachable objects and
reclaims their storage.

The fuller conceptual path is:

```text
Need to preserve results
        ↓
Need State
        ↓
State needs Memory
        ↓
Memory needs Lifetime
        ↓
Lifetimes are not identical
        ↓
Stack (lifetime order is known)
Heap  (lifetime order is unknown → Reachability + GC)
```

## Language Feature

In JavaScript, the runtime performs garbage collection automatically. A programmer usually does not
explicitly free an object; instead, the programmer removes unnecessary references and allows the
object to become unreachable.

## Syntax

```js
let user = { name: "Ali" };

console.log(user.name); // The object is reachable.

user = null;
// If no other reference exists, the object is now eligible for reclamation.
```

Being eligible for reclamation does not mean that memory is freed immediately or observably by the
program. The runtime controls the timing.

## Personal Notes & REPL Verification

The primary criterion for garbage collection is not age but Reachability. I must also distinguish
between “the object is no longer reachable through the program” and “its memory has been freed right
now.”

| Question or hypothesis                                                  | REPL experiment                                          | Observed result                                                                                            | Updated understanding                                                          |
| ----------------------------------------------------------------------- | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Can assigning `user = null` reveal the exact time when memory is freed? | Remove the reference and observe the program’s behavior. | The object is no longer reachable through that binding, but reclamation timing is not directly guaranteed. | Reachability is a conceptual condition for reclamation, not an exact schedule. |
