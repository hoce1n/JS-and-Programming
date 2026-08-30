# JS-and-Programming

## Project Vision

This repository documents a long-term effort to understand JavaScript deeply—not merely to memorize
syntax, but to build an accurate mental model of how the language and its execution runtime behave.

The goal is to connect everyday JavaScript features to the computational problems they solve. Each
topic is approached from first principles and tested through deliberate reasoning, handwritten code,
and experiments in a personal REPL. Framework experience with React, TypeScript, Next.js, and Prisma
provides practical context, but the focus here is the underlying language and runtime.

> The central question is not only “What is this syntax?” but also “What problem did this language
> solve with this feature?”

## Core Framework

Every concept is studied through the following progression:

| Layer                  | Guiding question                                                 |
| ---------------------- | ---------------------------------------------------------------- |
| **Problem**            | What real-world or programming difficulty needs to be addressed? |
| **Computational Need** | What capability must a computer have to address that difficulty? |
| **Concept**            | What general programming idea satisfies that need?               |
| **Language Feature**   | How does JavaScript model or implement the concept?              |
| **Syntax**             | How is that feature expressed in JavaScript code?                |

Syntax is therefore the final expression of understanding, not the starting point. Notes also
include personal explanations and REPL verification so that claims about behavior are checked
against observation rather than accepted passively.

## Learning and Documentation Workflow

Daily learning notes belong in the relevant topic directory under `notes/`. Reusable structures
belong in `templates/`. When a topic cluster is complete, a polished narrative can be prepared under
`drafts/medium/`, while condensed visual-content drafts can be prepared under `drafts/instagram/`.

The learner writes the explanations and code. Review focuses on correctness, precision, hidden
assumptions, and the difference between observed behavior and mental-model claims.

## Progress Tracking

The table below is the initial map of the conceptual journey. It is intentionally broad and can be
refined as the study progresses.

| Core topic                   | Central computational question                                                               | Status      | Primary notes                                              |
| ---------------------------- | -------------------------------------------------------------------------------------------- | ----------- | ---------------------------------------------------------- |
| **State & Memory**           | How can a program preserve, update, and retrieve information over time?                      | In progress | [`notes/01-state-and-memory/`](notes/01-state-and-memory/) |
| **Control Flow**             | How can a program choose actions, repeat work, and determine execution order?                | Not started | —                                                          |
| **Data Organization**        | How can related values be represented, grouped, and accessed effectively?                    | Not started | —                                                          |
| **Abstraction**              | How can complexity be hidden while useful behavior remains available?                        | Not started | —                                                          |
| **Composition**              | How can smaller behaviors be combined into larger systems?                                   | Not started | —                                                          |
| **Errors & Failure**         | How can a program detect, represent, and recover from things going wrong?                    | Not started | —                                                          |
| **Concurrency & Asynchrony** | How can a program coordinate work that does not complete in a single uninterrupted sequence? | Not started | —                                                          |
| **Communication & I/O**      | How can a program exchange information with the outside world?                               | Not started | —                                                          |
| **Identity & Scope**         | How can a program determine which value or resource a name refers to?                        | Not started | —                                                          |
| **Execution Runtime**        | How does the JavaScript runtime evaluate code and manage execution resources?                | Not started | —                                                          |

## Repository Structure

```text
.
├── drafts/
│   ├── instagram/       # Condensed visual-content drafts
│   └── medium/          # Polished topic-cluster drafts
├── notes/
│   └── 01-state-and-memory/
│       └── .gitkeep
├── templates/
│   └── concept-template.md
└── README.md
```

## References and Tools

[MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript) is used as a parallel
reference. Runtime behavior is explored with the personal REPL at
[runtimejs.hoce1n.ir](https://runtimejs.hoce1n.ir/). Professional application context comes from
work with Next.js 15 and TypeScript.
