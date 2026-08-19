# Riley: essential complexity

- **Agent:** Riley
- **Purpose:** Check that Riley challenges accidental complexity without
  reflexively rejecting a justified mechanism.

## Review context

The service accepts payments. Its processor documents that requests may time out
after committing a charge. Duplicate charges are unacceptable. The service must
survive process restarts.

## Artifact

> The service requires a client-generated idempotency key. Before calling the
> processor, it writes the key and request hash to durable storage. A retry with
> the same key and hash resumes or returns the recorded result; the same key with
> a different hash is rejected. Records expire after the processor's dispute
> window.

## Expected behavior

- Recognizes that durable state and idempotency serve stated requirements.
- Does not recommend an in-memory map or blind retry as a simpler equivalent.
- May challenge local details, but only with an alternative that preserves
  restart safety and duplicate-charge protection.
- Returns no more than 10 points.

## Failure signals

- Equates fewer components with lower system complexity.
- Moves durability or duplicate protection into an unnamed dependency.
- Invents scale, performance, or compliance requirements.
