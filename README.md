# Ecclesia

**A systems-oriented programming language designed for predictable execution and explicit control.**

Ecclesia is an experimental compiled programming language and execution environment. Its familiar procedural syntax sits on top of a bounded execution model, validated compiler artifacts, and a deliberately clear boundary between program meaning and physical resource management.

The project has grown well beyond its original R0 foundation. Current private development includes typed functions, signed and unsigned integer types, floating-point values, loops, structs, enums, fixed arrays, imports, strings and printing, a standard library, an interactive REPL/editor, and a native executable pipeline.

> **Public availability:** This repository is a public presentation and historical release surface. It is **not** a complete current compiler distribution or a buildable mirror of the active private development repository. The capabilities described here reflect ongoing development; publication of source, executables, or releases is a separate milestone. No current compiler download or build procedure is implied.

## A glimpse of Ecclesia

```ecs
fn main() {
    println("Hello from Ecclesia!");
    return 0;
}
```

The example demonstrates the modern language's entry point and print facility. It is illustrative source, **not a claim that the current compiler is downloadable from this repository**.

Ecclesia is designed to make familiar code coexist with explicit runtime limits:

```ecs
fn sum_to(limit: i32) -> i32 {
    let total: i32 = 0;
    let n: i32 = 1;

    while (n <= limit) {
        total = total + n;
        n = n + 1;
    }
    return total;
}

fn main() {
    return sum_to(7);
}
```

Explore [the examples](examples/README.md) for more short illustrations of the current language.

## What makes Ecclesia different?

- **Bounded execution.** The compiler and execution environment operate under explicit resource and instruction limits rather than assuming unlimited capacity.
- **Validated intermediate representation.** Successful parsing is not enough: lowered programs must pass IR validation before execution.
- **Separation of concerns.** Ecclesia owns computation and language semantics. Physical resource management can be supplied by [Ouroboros-GPA](https://github.com/dwilson-ecf-cmd/Ouroboros-GPA) through a dedicated adapter; allocator topology is not part of Ecclesia source-language semantics.
- **A capable developer environment.** The active implementation includes an interactive REPL and editor, a library/module workflow, compiler diagnostics, and a staged path to native executables.
- **Cross-platform engineering.** POSIX/Linux and Windows/MinGW are development targets; individual tools and integrations have their own qualification boundaries.

These are architecture and implementation characteristics, not blanket assurances about production, real-time, or safety-critical suitability.

## Language features under development

| Area | Current development capabilities |
| --- | --- |
| Computation | Typed functions, local variables, arithmetic, comparisons, explicit returns |
| Control flow | Conditions, structured loops, break/continue, recursion |
| Types | Fixed-width integer families, booleans, floating point, structs, enums, typed pointers |
| Data | Fixed and multidimensional arrays, strings, constrained type sets |
| Organization | Source modules, imports, standard-library packages |
| Tools | REPL, editor, compiler diagnostics, intermediate artifacts, native build pipeline |
| I/O | Text output, minimal platform I/O boundary, evolving device discovery and binding |

These rows summarize broad active-development surfaces, not a frozen public-release compatibility promise. Some device and platform integrations are still evolving.

## Architecture at a glance

```text
Ecclesia source (.ecs)
      ↓
Lexing and parsing
      ↓
Module resolution and semantic analysis
      ↓
Lowering
      ↓
IR validation
      ↓
Validated execution or native artifact pipeline
```

A validated program is executed within the runtime's defined capacities. Modern development also supports an artifact chain from `.ecs` through `.ecx` and `.elo` to a native executable.

The guiding principle remains:

> **Ecclesia owns computation. Ouroboros owns resources.**

The language does not require a programmer to understand physical allocator internals to express a computation.

## Repository contents

This public repository contains the project introduction, illustrative examples, editor support where included, and the MPL-2.0 license. It should not be mistaken for the full development source tree.

- [Examples](examples/README.md): beginner-oriented modern syntax samples
- [Syntax highlighting](syntaxes/): editor grammar, where available; editor highlighting may lag newer language features
- [License](LICENSE): Mozilla Public License 2.0

## Availability and project status

Ecclesia began with a small, certified **R0** executable core: a contract-driven demonstration of the source-to-validated-execution path. Subsequent private development has substantially expanded the language and runtime. **R0 describes a historical baseline, not the full present language.**

This repository does not currently offer an independently verified downloadable latest compiler, package, or installation workflow. We will add concrete build and installation directions only alongside a public artifact that readers can actually reproduce.

Until then, the examples are provided as readable documentation, rather than as executable tests within this public repository.

## License

Content distributed here is subject to the [Mozilla Public License 2.0](LICENSE), to the extent it constitutes covered software. The existence of this public repository does not itself publish or license the separate private development repository.
