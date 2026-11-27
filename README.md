<h1 align="center">SOVEL — Biomedical Intelligence Workspace</h1>
<p align="center">Created and developed by Aarushi Singh</p>
<p align="center"><strong>Live Application: <a href="https://sovel.punimon.com">sovel.punimon.com</a></strong></p>

## Overview

SOVEL is an independent biomedical software project that brings three kinds of reading into one browser workspace. An explanation can change with the reader’s background. A finding needs a passage that supports it. A laboratory measurement needs its original unit and reference range. I built SOVEL around those differences.

## Quick Start

Open the live application above and complete guest verification. Choose a workspace, then enter a question or attach a supported document. Each verified browser session has five AI messages per UTC day, subject to a shared monthly budget. The interface shows the remaining allowance and reset time.

## Workspaces

| Workspace | What you can do |
| --- | --- |
| **Research Assistant** | Explore a biomedical concept or develop a research question. Selecting a different explanation depth is free. Explicitly requesting an updated answer uses one message. |
| **Research Evidence Workspace** | Examine a paper or compare several papers you supply. Trace a finding to its supporting excerpt and consider how differences in methods or outcomes affect the comparison. |
| **Health Report Explainer** | Review reported values, units and reference ranges in plain language. Compare compatible dated reports and check individual measurements against the original. |

## Architecture

The browser sends questions and attachments to a single application service. Its processing path depends on the task. Paper analysis preserves source identity and excerpts. Report parsing uses native text, page layout or OCR to associate a value with its unit. The public service calls the OpenAI API directly. The local configuration supports Ollama with Qwen3-14B. [Architecture and system diagram](docs/architecture.md)

## Engineering & Validation

One browser regression test submitted two papers together and checked that the comparison retained both source identities. Another verified that changing research depth left the guest allowance intact until an update was requested. These checks used simulated inference. The release record distinguishes automated results, live observations and known limitations. [Validation record](docs/validation.md)

## Technology

| Component | Stack |
| --- | --- |
| Browser interface | React, TypeScript, Vite, Zod |
| Application service | Python, FastAPI, Pydantic, HTTPX |
| Document processing | unpdf, native PDF layout processing, Tesseract OCR |
| Deployment and usage accounting | Docker, Render, SQLite |

## Development

- **October 18, 2026** — The local V1 release candidate completed acceptance across all three workspaces.
- **November 2026** — The public beta introduced browser guest access and hosted inference. Later release checks covered multi-document submissions and explicit answer updates.

## Responsible Use

SOVEL is for research and education. **Do not enter or upload identifiable patient information.** Cloud AI requests may send relevant question or document text to the provider. Check scientific claims against their sources and extracted measurements against the original report. [Privacy notice](https://sovel.punimon.com/privacy)
