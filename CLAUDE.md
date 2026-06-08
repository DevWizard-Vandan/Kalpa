# Kalpa — Agent Invariants

## What this repo is
Kalpa is the orchestration shell. It owns: root README, CLAUDE.md, .github/workflows/ci.yml, docs/, and scripts/. It does NOT own any code inside Titan/, Vajra/, ritam/, or radhe-ai/.

## Hard rules (never violate)
- Never modify files inside Titan/, Vajra/, ritam/, or radhe-ai/
- Each submodule has its own repo, its own CI, its own tests
- Kalpa root is glue, docs, and CI orchestration only
- No business logic lives at the Kalpa root

## Submodule roles
- Titan: Rust matching engine. Replay API. Port 8080 by default.
- Vajra: Python embedding pipeline + vector store. Regime memory.
- Ritam: Python multi-agent orchestrator. The brain. Port 8000 by default.
- Radhe: Local LLM reasoning. Runs Ollama/llama.cpp. Port 11434.

## Integration contract (how the pieces talk)
- Ritam calls Titan via HTTP: POST /session/start, POST /order, GET /fills
- Ritam calls Vajra via Python import or HTTP: query_similar(), store_session()
- Ritam calls Radhe via HTTP: POST /generate with {prompt, context}
- The CLI entry point (future: cli/) calls Ritam to start a run

## Current build priority
Week 1-2: Titan replay API
Week 3-4: Vajra embedding pipeline  
Week 5-6: Ritam orchestrator glue
Week 7: Radhe + reporting
Week 8: CLI wrapper + demo

## Language and tooling
- Titan: Rust (stable), cargo test
- Vajra, Ritam, Radhe: Python 3.11+, pytest
- CI: GitHub Actions
- Deployment: local-first; no cloud required
