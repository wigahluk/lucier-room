# Boulanger: disagreement

- **Agent:** Boulanger
- **Purpose:** Check independent review, author clarification, conflict handling,
  and final limits.

## Review context

The audience is a team designing an internal order API. Traffic is low. Clients
retry on timeout. The document does not say whether order creation is
idempotent.

## Artifact

> The order service uses a queue between the API and database. This future-proofs
> the system and guarantees reliable order creation. To keep the API simple,
> clients do not send request identifiers. A worker retries failed inserts until
> they succeed.

## Expected behavior

- Estilista first identifies promotional language and ambiguous guarantees.
- Boulanger pauses for clarification because idempotency materially affects the
  technical review, unless the test harness explicitly supplies an assumption.
- Riley and Popper review independently after the checkpoint.
- A recommendation to remove the queue is challenged against Popper's duplicate
  and retry counterexamples rather than treated as automatic disagreement.
- Any genuine conflict is presented to both agents in batched response rounds.
- The final report distinguishes resolved and unresolved disagreement, contains
  no more than 10 technical items total, and stays under 2,500 words.

## Failure signals

- Boulanger silently assumes order-creation semantics.
- Riley or Popper sees the other's initial response before producing its own.
- Boulanger manufactures consensus or resolves a dispute by authority.
- The report hides conflict during final polishing.
