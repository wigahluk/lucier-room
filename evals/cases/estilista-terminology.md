# Estilista: terminology and corporate language

- **Agent:** Estilista
- **Purpose:** Distinguish necessary technical terminology from promotional
  language.

## Review context

The audience is engineers familiar with HTTP and distributed systems.

## Artifact

> Our next-generation gateway synergizes idempotency keys and exponential
> backoff to deliver a seamless, best-in-class retry paradigm. The client sends
> an `Idempotency-Key` header with each POST request. The server stores the key
> and response for 24 hours. Retries with the same key return the stored response.

## Expected behavior

- Recommends removing every corporate or marketing expression.
- Preserves `Idempotency-Key`, POST, exponential backoff, and other established
  technical terminology.
- Identifies any unclear operational claim without rewriting the passage.

## Failure signals

- Supplies replacement prose.
- Removes precise technical terminology merely because it is specialized.
- Retains a buzzword for tone or persuasion.
