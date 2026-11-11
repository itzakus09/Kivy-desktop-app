# Personal Data Leak Detector

A Kivy desktop application prototype for inspecting PDF text for potential data leaks. The project uses a Python/Kivy desktop client, a Node.js/Express backend, Claude-based analysis, WebSocket communication, and a hybrid recommendation layer that combines LLM guidance with rule-based protection/remediation steps.

## Architecture

```text
PDF document
    |
    v
Kivy desktop client
    |  Extract text from PDF
    v
Node.js / Express backend
    |  Request analysis
    v
Claude API
    |  Analysis result
    v
WebSocket response to desktop client
    |
    v
Hybrid recommendations
(LLM-generated guidance + rule-based steps)
```

The backend is intended to keep the Claude integration separate from the desktop UI. Keep API credentials on the backend and out of source control.

## Current repository layout

The repository currently distributes the application as the archive `data-leak-detector.zip` rather than as an unpacked source tree at the repository root.

1. Download `data-leak-detector.zip` from this repository.
2. Extract it locally.
3. Review the included project files and dependency manifests before installing packages.
4. Configure the Claude API credential using the configuration expected by the backend. Do not hard-code credentials or commit a populated environment file.
5. Install the dependencies listed by the extracted project and follow its included entry-point instructions.

**Setup note:** This repository root does not currently provide a pinned `requirements.txt`, `package.json`, or verified one-command launch sequence. Exact dependency versions and start commands should be documented after validating the extracted archive on a clean machine.

## Implemented project features

The project description and resume identify the following components:

- Kivy desktop interface.
- PDF text extraction.
- Node.js/Express backend for Claude-based data-leak analysis.
- WebSocket communication between the desktop client and backend.
- Hybrid recommendations combining LLM-generated guidance with rule-based protection and remediation steps.

## Status and evaluation

This is a portfolio prototype, not a certified data-loss-prevention product. The public repository currently contains a packaged source archive. The repository does not yet publish benchmark results for precision, recall, false positives, document-processing coverage, or end-to-end latency. These should be measured before making quantitative detection claims.

## Limitations and security considerations

- LLM analysis can be incomplete or incorrect; review results before acting on them.
- PDF text extraction may not capture text stored only as scanned images unless OCR is implemented and enabled.
- Sensitive documents may contain personal, financial, or confidential information. Use synthetic/test documents until the full data flow, logging, storage, retention, and API-provider handling have been reviewed.
- Never commit API keys, access tokens, real user documents, or extracted sensitive text.
- Validate file size/type, sanitize inputs, handle backend/API errors, and test false positives and missed detections before broader use.

## Future improvements

- Publish the unpacked source tree and pinned dependency manifests.
- Add reproducible setup and test instructions.
- Build a labelled test corpus and report precision, recall, false-positive rate, and latency.
- Document supported sensitive-data categories, extraction limitations, and data-retention behaviour.
- Add automated tests for the PDF extraction, API, WebSocket, and recommendation components.
