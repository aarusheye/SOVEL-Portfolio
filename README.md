# SOVEL — Biomedical Intelligence Workspace

**Created and developed by Aarushi Singh**

**Live Application: [sovel.punimon.com](https://sovel.punimon.com)**

SOVEL brings three kinds of biomedical reading into one browser workspace. Ask a question about a concept, compare the evidence in papers you supply, or make sense of the measurements in a laboratory report.

| Workspace | Try it when you want to… |
| --- | --- |
| **Research Assistant** | Understand a concept or develop a research question. Choose an explanation depth and explicitly request a new answer when you want another level of detail. |
| **Research Evidence Workspace** | Read one paper closely or compare several. Inspect a finding alongside its supporting excerpt and check which paper it came from. |
| **Health Report Explainer** | Read a supported lab report in plain language. Review the reported values, units and reference ranges, and compare compatible dated reports. |

## Why I built SOVEL

I wanted a biomedical workspace that respected the difference between explaining an idea, interpreting a paper and reading a measurement. An explanation can change with the reader’s background. A finding needs a source. A reported value needs its original unit and context. Those differences shaped SOVEL as an independent project connecting biotechnology, biomedical science and AI.

## Using the public beta

Open SOVEL in a browser and complete guest verification. Each verified browser session has five AI messages per UTC day, subject to a shared monthly budget. Selecting a research depth is free. Explicitly updating an answer uses one message. The app shows the remaining allowance and reset time.

Use public papers or synthetic examples. **Do not enter identifiable patient information.** SOVEL is for research and education. Check generated explanations against the sources and review extracted measurements against the original report before drawing conclusions. [Privacy notice](https://sovel.punimon.com/privacy)

## Development milestones

- **October 18, 2026** — The local V1 release candidate completed acceptance with three workspaces and local model inference.
- **November 2026** — The public beta brought browser guest access and hosted inference to SOVEL. Local inference remains available in the project.
- **November 27, 2026** — Release testing covered document routing, guest message accounting and the explicit answer-update interaction. [Validation record](docs/validation.md)

[Architecture and technology](docs/architecture.md)
