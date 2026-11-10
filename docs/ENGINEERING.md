# Agent Reliability Lab: engineering notes

A convincing answer can hide a broken run. Agent Reliability Lab runs the same task through naive and protected workers so output quality and execution integrity can be examined separately.

## System path

~~~mermaid
flowchart LR
  Task --> Baseline
  Task --> ProtectedRunner
  Fault --> Baseline
  Fault --> ProtectedRunner
  Baseline --> IndependentVerifier
  ProtectedRunner --> IndependentVerifier
  IndependentVerifier --> Comparison
~~~

This diagram describes the demonstrated system boundary, not a production deployment topology.

## Decisions and tradeoffs

### Commit acceptance atomically

The protected runner writes an idempotency receipt with the queued run. Repeating the same request returns the original run; a changed intent conflicts.

### Make ownership expire safely

Workers publish under leases and owner tokens. Checkpoints are reusable only when their content, input and configuration digests match.

### Judge the run independently

Verification checks receipts, publication ownership, checkpoint integrity and artifact freshness separately from answer quality. Comparisons retain failed runs.

## Review questions

- What evidence demonstrates **commit acceptance atomically**, and what would fail without it?
- What evidence demonstrates **make ownership expire safely**, and what would fail without it?
- What evidence demonstrates **judge the run independently**, and what would fail without it?

## Verification boundary

18 database regressions covering replay, ownership, interruption, checkpoints and verification boundaries. Five browser checks passed for the current demo. Recorded walkthrough includes controlled fault injection and inspection of the resulting evidence.

Fixture faults demonstrate specific failure modes; they are not a benchmark of all real models or an availability guarantee. The baseline is intentionally unsafe inside the experiment only.
