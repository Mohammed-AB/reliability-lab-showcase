# Agent Reliability Lab: verification record

Review date: **10 November 2026**.

## Current mode

Controlled fault experiments over fictional requirements and a deterministic fixture provider. The default demo makes no paid model calls.

## Observed checks

- 18 database regressions covering replay, ownership, interruption, checkpoints and verification boundaries.
- Five browser checks passed for the current demo.
- Recorded walkthrough includes controlled fault injection and inspection of the resulting evidence.

These are scoped development checks, not an external audit or a claim of production adoption. Test fixtures are fictional. The private implementation workspace retains detailed test logs and provider receipts; this package carries the presentation evidence only.

## Explicit limits

Fixture faults demonstrate specific failure modes; they are not a benchmark of all real models or an availability guarantee. The baseline is intentionally unsafe inside the experiment only.

## Package integrity

[Media manifest](../media-manifest.json) records the included filenames, byte sizes and SHA-256 digests. It identifies the exact presentation assets; a hash does not by itself prove the assertions above.
