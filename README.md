# Ecclesia

Ecclesia is a systems-oriented programming language and execution architecture built around explicit state, deterministic computation, bounded resources, and observable failure.

This repository is the canonical public-release surface for the Ecclesia language. Development is currently progressing through **R0 (Revision 0)** — the smallest coherent architectural revision capable of proving the complete path from source through compilation, validated intermediate representation, and deterministic execution.

R0 is a qualification baseline, not a statement of prototype quality.

## Governing principle

> **Ecclesia owns computation. Ouroboros owns resources.**

Ecclesia defines language meaning, compiler artifacts, validated IR, execution state, values, failures, and semantic lifetimes. Resource management lives behind a narrow adapter boundary and is not part of language semantics.

## R0 language surface

The current R0 contract includes:

- signed 64-bit integers with checked arithmetic
- `fn`, `let`, `if` / `else`, and `return`
- lexical blocks and shadowing
- fixed-arity functions and calls
- explicit comparison conditions (no integer truthiness)
- deterministic left-to-right evaluation
- recursion represented by explicit execution frames rather than dependence on the host C call stack
- structured, observable failure
- bounded compiler and runtime state

Features such as arbitrary-precision arithmetic, surreal mathematics, persistence, modules, FFI, concurrency, loops in source, and neural execution machinery are intentionally outside R0.

## What R0 has proven

The R0 executable core has been certified. The complete vertical path is proven and frozen:

```text
source
  → lexer
  → token stream
  → parser
  → syntax artifact
  → semantic analysis
  → semantic program
  → lowering
  → candidate IR
  → IR validation
  → validated IR
  → deterministic execution
```

Every compiler handoff is an artifact boundary. Execution consumes only validated IR. The execution engine is an explicit bounded state machine; language recursion does not rely on the host C call stack.

## Engineering doctrine

Ecclesia is developed component by component:

1. Define the contract
2. Define invariants and ownership
3. Define failure and observability
4. Implement the smallest mechanism that satisfies the contract
5. Qualify it adversarially
6. Freeze proven behavior before expanding scope

> **Prove the mechanism. Prove its boundary. Then prove the composition.**

A successful end-to-end example does not substitute for component qualification.

## Source identity

- Canonical source extension: `.ecs`
- Canonical TextMate scope: `source.ecclesia`

The `syntaxes/` directory contains the public syntax-highlighting grammar.  
The `examples/` directory contains representative R0 programs that track the *qualified* language surface rather than anticipated future syntax.

## Status

The R0 executable core is certified and frozen.  
Public examples and editor support follow the qualified language contracts.  
Further work (runtime composition, REPL surface, richer language features, and full resource-backend qualification) continues under the same architectural discipline.

## License

Ecclesia is licensed under the **Mozilla Public License 2.0 (MPL-2.0)**.  
See [`LICENSE`](LICENSE) for the complete terms.
