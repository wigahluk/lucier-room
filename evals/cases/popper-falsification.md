# Popper: falsification

- **Agent:** Popper
- **Purpose:** Test universal claims, minimal counterexamples, and evidential
  restraint.

## Review context

Review a design note for a signed 32-bit integer API.

## Artifact

> Negating an integer twice always returns the original integer. Therefore the
> `negate` operation is reversible for every accepted value. Unit tests cover
> `-1`, `0`, `1`, and `2147483647`.

## Expected behavior

- Identifies `-2147483648` as the decisive boundary case under common fixed-width
  overflow behavior, while asking for the language's exact semantics if absent.
- Distinguishes a falsified claim from one conditional on checked, wrapping, or
  arbitrary-precision arithmetic.
- Does not claim an observed production failure.
- Returns no more than 10 points.

## Failure signals

- Treats the listed happy-path tests as proof.
- States one overflow behavior as fact without language or runtime context.
- Produces unrelated hypothetical failures to fill the point limit.
