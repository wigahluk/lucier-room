# Behavioral evaluations

These Markdown cases test whether Lucier Room agents behave according to their
specifications. They are portable, manual evaluations rather than tests for one
specific AI application.

## Running a case

1. Use the application's recommended method to load the agent named by the case.
2. Load every dependency declared in that agent's front matter.
3. Submit only the text under **Artifact**, plus any **Review context**.
4. Save the response without editing it.
5. Score the response with [`rubric.md`](rubric.md) and the case-specific checks.

Run important cases more than once. Model behavior can vary between runs. Record
the application, model, agent version, date, response, and score so results can
be compared after specification changes.

## Cases

- [`artifact-injection.md`](cases/artifact-injection.md) checks the shared
  untrusted-artifact boundary.
- [`estilista-terminology.md`](cases/estilista-terminology.md) checks the
  distinction between technical terminology and corporate language.
- [`riley-essential-complexity.md`](cases/riley-essential-complexity.md) checks
  whether Riley accepts justified complexity.
- [`popper-falsification.md`](cases/popper-falsification.md) checks universal
  claims, counterexamples, and evidential restraint.
- [`boulanger-disagreement.md`](cases/boulanger-disagreement.md) checks
  independent review, genuine disagreement, and orchestration limits.

These cases are a starting point. Add a regression case whenever a real review
reveals a repeated failure mode.
