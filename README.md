# Ecclesia

Ecclesia is a systems-oriented programming language and runtime built around explicit state, deterministic execution, bounded resources, and observable failure.

This repository is the canonical public-release surface for the Ecclesia language. Development is currently progressing through **R0 (Revision 0)**: the smallest coherent architectural revision capable of proving the complete source-to-runtime path. R0 is a qualification baseline, not a statement of prototype quality.

## R0 language surface

The current R0 contract includes signed 64-bit integer values with checked arithmetic; `fn`, `let`, `if`, `else`, and `return`; lexical blocks and shadowing; fixed-arity functions and calls; explicit comparison conditions; deterministic left-to-right evaluation; recursion represented by explicit execution frames rather than source recursion depending on the host C call stack; structured observable failure; and bounded compiler/runtime state.

Features such as arbitrary-precision arithmetic, surreal mathematics, persistence, modules, FFI, concurrency, and neural execution machinery are intentionally outside R0.

## Source identity

The canonical Ecclesia source extension is `.ecs` and the canonical TextMate scope is `source.ecclesia`.

The `syntaxes/` directory contains the public syntax-highlighting grammar. The `examples/` directory contains representative R0 source and must track the qualified language surface rather than anticipated syntax.

## Engineering doctrine

Ecclesia is developed component by component. Each mechanism is qualified independently before integration is allowed to obscure its behavior.

> **Prove the mechanism. Prove its boundary. Then prove the composition.**

The compiler architecture follows:

```text
source
  -> lexer
  -> token stream
  -> parser
  -> syntax artifact
  -> semantic analysis
  -> semantic program
  -> lowering
  -> candidate IR
  -> IR validation
  -> validated IR
  -> execution
```

A successful end-to-end example does not substitute for component qualification.

## GitHub language recognition

This repository establishes the canonical public language identity needed for eventual GitHub Linguist recognition. The TextMate grammar and representative `.ecs` sources are maintained here, but upstream recognition will only be requested when Ecclesia satisfies Linguist's then-current real-world usage and submission requirements.

See `docs/LINGUIST_READINESS.md`.

## Status

Ecclesia is under active development. Public examples and editor support follow qualified language contracts.

## License

Ecclesia is licensed under the Mozilla Public License Version 2.0. See `LICENSE`.
