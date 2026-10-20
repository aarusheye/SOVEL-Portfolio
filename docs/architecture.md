# Architecture

[← Project overview](../README.md) · [Validation](validation.md)

SOVEL V1 is a local, single-user biomedical workspace. This document describes responsibilities and tradeoffs at a conceptual level. It deliberately omits production code, prompts, internal schemas, validation rules, and model-routing details.

![Conceptual local application architecture](../assets/architecture/overview.svg)

## Workspace separation

The interface separates Health, Research Copilot, and Evidence because their source and interpretation requirements differ. A laboratory result must retain reported measurement information; a research proposal must be identifiable as a proposal; a paper comparison must preserve which source supports each observation.

Health organizes laboratory information and compatible dated comparisons. Copilot supports concepts and conceptual planning from questions and supplied notes. Evidence analyzes supplied papers and their supporting excerpts. This separation gives each workflow an appropriate presentation and verification boundary.

## Document ingestion

Document preparation distinguishes usable native text from pages that need OCR. Supported inputs are classified and prepared for the relevant workspace, with source context retained for inspection. Missing metadata, uncertain extraction, and unreadable input are explicit review or failure conditions.

For laboratory workflows, fidelity means retaining reported values, units, and reference ranges rather than letting generative text invent measurements. For paper workflows, fidelity means preserving source identity and the excerpts used in analysis. Successful low-level extraction alone does not establish that the entire user workflow succeeded; verification also exercises upload, routing, processing, and rendering.

## Local processing and model interaction

The React/TypeScript browser interface communicates with a local Python/FastAPI service. V1 uses local Ollama inference. Deterministic processing and model-assisted interpretation have different responsibilities: measurements require faithful handling, while generated scientific explanations require checks against their permitted source context.

Locality reduces the need to transmit biomedical documents to remote inference services. It also makes local hardware, model availability, and document complexity part of the latency tradeoff. V1's accepted scope is loopback-only operation for one user, rather than a hosted service with account or tenant isolation.

## Scientific validation and source ownership

Generated output is checked for structural validity and tested scientific/source consistency before successful output is accepted. In Evidence comparisons, each paper retains ownership of its observations. A finding supported by one source must not silently become a finding attributed to another.

The interface exposes supporting excerpts and study context so the user can inspect the basis of an interpretation. Methods and limitations matter alongside findings, particularly when discussing whether a design supports a causal conclusion. These checks address defined failure modes; they do not prove that every possible scientific statement is correct.

## Private caching

Reusable Evidence results are associated with their source and processing context. Compatibility checks and revalidation guard reuse as processing contracts evolve. Failed or invalid processing is not promoted into a successful reusable result.

Caching trades repeated work for local data retention: private caches can contain source excerpts and need responsible local lifecycle management. The public showcase includes neither cache contents nor internal cache identities or formats.

## Request ownership and cancellation

Requests and background work have explicit lifecycles. Document changes, attachment removal, cancellation, and new sessions must not let an obsolete response restore previous state. Backend work has bounded execution and cleanup behavior so a stalled document or model operation does not imply unbounded waiting.

These controls are application resource-management measures. They are not a claim of operating-system sandboxing or a hard memory quota.

## Browser and UI layer

The UI presents structured results, review states, errors, and inspectable source context. Client validation checks incoming structured output before rendering. Desktop/mobile and light/dark checks help verify that evidence remains usable across layouts.

Actual browser checks exercise the same File-to-render path as normal use. Transport tests and component tests provide complementary coverage; neither substitutes for a successful real upload and rendered result.

## Engineering boundaries

The principal design tradeoff is local control with finite compute. Large or uncached document workflows can be slow, and model-generated text still requires critical review. Remote deployment, broader workflow coverage, and latency improvements are post-V1 work. Public documentation communicates the design without distributing the proprietary implementation.

© 2026 Aarushi Singh. All rights reserved.
