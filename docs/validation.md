# V1 validation and acceptance

[← Project overview](../README.md) · [Architecture](architecture.md)

**Status: V1 Release Candidate accepted October 18, 2026.**

This summary was checked against the private accepted release record and draft pull request. It reports recorded evidence, not a new rerun or an independent certification. Production test fixtures, raw reports, internal review artifacts, and implementation details remain private.

## Acceptance scope

V1 covers the local, single-user Health, Research Copilot, and Research Evidence workspaces. Under the bounded release criteria, known P0/P1 correctness, safety, privacy, and functional findings were closed, and required functional/build/browser gates passed. Acceptance does not imply cloud readiness, regulatory clearance, clinical validation, or absence of all possible defects.

## Recorded results

| Verification layer | Result | Meaning |
| --- | --- | --- |
| Backend suite | 578 run; 575 passed; 3 opt-in skips | Backend regression coverage; skips are not counted as passes |
| Focused Evidence suite | 136 passed | Targeted Evidence verification; overlaps broader coverage |
| Fast evaluations | 75 passed of 75 | Deterministic evaluation checks |
| Frontend suite | 352 passed; 6 opt-in skips | Client/UI regression coverage |
| Browser transport | 17 passed | Browser-control transport behavior |
| TypeScript | Passed | Static type checking |
| Production build | Passed | Frontend build completed |
| Final Evidence File/browser run | 3 required cases passed | Actual upload, routing, API, validation, and rendered output |
| Evidence theme/viewport checks | 24 passed | Presentation across the required layouts/themes |
| Final isolated live Evidence run | Four HTTP 200 responses; all correctness checks passed | Real model workflow completion with performance disposition below |

These are different suites and checks, with overlap. Their counts must not be summed into a unique test total. Opt-in skips remain unexecuted coverage, not failed tests or implied passes.

## Correctness, function, and performance

**Correctness** concerns the content and attribution of a result: scientific claims, cited support, source identity, structured output validity, and cache consistency in the evaluated cases.

**Function** concerns whether the supported workflow completes and returns a usable result through its actual application path. An HTTP 200 alone is insufficient: the output must also pass its required functional and content checks. A workflow that times out without a valid result is a functional failure, even if a smaller input passes.

**Performance** concerns elapsed time against a stated target when the workflow otherwise completes correctly. A latency miss remains a failed timing assertion; acceptance does not rewrite it into a pass.

## Final isolated live Evidence evaluation

| Case | Completion | Correctness / source checks | Timing disposition |
| --- | --- | --- | --- |
| Single-paper analysis | HTTP 200 | Passed | 42.499 s; passed its case-specific target |
| Standard comparison | HTTP 200 | Passed | 81.481 s; passed its case-specific target |
| Complementary evidence | HTTP 200 | Passed | 41.176 s; exceeded 30 s target |
| Renamed-document identity | HTTP 200 | Passed | 42.049 s; exceeded 30 s target |

Each case retains its original timing assertion; the 30-second target applies to the last two cases, not to every workflow. All four passed the recorded correctness, source/structure, identity, and cache checks. Because two timing assertions failed, the raw all-criteria report remains **2/4**.

The two latency-only misses are recorded as post-V1 performance work. No timeout, target, retry count, or correctness assertion was relaxed to manufacture acceptance.

## Browser and document-path verification

The final Evidence browser run covered two single-paper questions and a comparison through actual browser Files, PDF processing, routing, API calls, client validation, and rendering. All three required cases and 24 theme/viewport checks passed; representative comparison captures were inspected during release verification.

Earlier accepted Health and Copilot checks remain part of the release evidence. The final isolated Evidence run is an affected-workflow verification, not a claim that the entire application's live suite was rerun at final closure.

## Remaining boundaries

The release record retains performance work, an existing PDF.js build-size warning, and a deferred development test-tool major upgrade. The production build passed; the full development-tool dependency audit is not claimed clean. Long documents, local compute constraints, and finite scientific checks limit generalization beyond the tested scope.

No public raw reports or fixtures are supplied, so readers cannot independently reproduce the private test suites from this showcase. This document is a transparent engineering summary of the recorded release evidence.

© 2026 Aarushi Singh. All rights reserved.
