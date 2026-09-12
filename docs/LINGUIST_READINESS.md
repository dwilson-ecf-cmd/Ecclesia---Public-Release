# GitHub Linguist Readiness

This document tracks the public language identity and evidence needed before Ecclesia is proposed for upstream recognition by GitHub Linguist.

## Canonical identity

- Language name: `Ecclesia`
- Language type: programming
- Source extension: `.ecs`
- TextMate scope: `source.ecclesia`
- Grammar: `syntaxes/ecclesia.tmLanguage.json`
- License: MPL-2.0

These values are public compatibility surfaces. Changes should be deliberate and reviewed.

## Current assets

This repository provides a canonical public language name, `.ecs` source extension, TextMate-compatible syntax grammar, representative R0 source examples, and a public location from which editor integrations may consume the grammar.

## Upstream gate

Do not submit an Ecclesia language entry to GitHub Linguist merely because the technical metadata exists. An upstream proposal should wait until all then-current Linguist contribution requirements have been re-checked and Ecclesia has sufficient independent, real-world public usage. Adoption evidence must be genuine; generated repositories or files exist to test tooling, not to manufacture usage statistics.

Before submission:

1. Re-read the current GitHub Linguist contribution and language-addition requirements.
2. Verify `.ecs` does not require extension disambiguation, or add content heuristics if it does.
3. Verify the TextMate grammar against the then-current qualified Ecclesia syntax.
4. Gather representative real-world `.ecs` samples from public, non-generated usage.
5. Verify usage satisfies the then-current Linguist threshold and distribution expectations.
6. Import the grammar using Linguist's current tooling.
7. Add the Ecclesia language definition and let Linguist tooling generate the language ID.
8. Run the complete required Linguist test/classifier suite.
9. Submit the upstream PR with usage evidence and representative samples.

## Grammar maintenance rule

The syntax grammar follows the qualified language contract. It must not advertise syntax merely because a future Ecclesia revision is expected to support it.

When a language revision changes syntax, first change and freeze the language contract, qualify compiler behavior, then update public `.ecs` examples and the TextMate grammar.

## Public examples

Examples should be representative programs, not thousands of artificial files intended to influence GitHub language statistics. Their purpose is documentation, editor validation, and eventually representative Linguist samples.

## Recognition status

**Not yet submitted upstream.**

Ecclesia should earn GitHub recognition through actual use rather than treating recognition as a prerequisite for the language itself.
