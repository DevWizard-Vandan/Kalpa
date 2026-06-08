# Kalpa

> A complete cycle for local quant research.

Kalpa is a local-first quant research operating system designed to automate and streamline the entire strategy development and evaluation lifecycle. It leverages **Ritam** for multi-agent orchestration to coordinate the system's execution workflow, queries **Vajra** for regime memory and vector-based semantic retrieval of historical sessions, executes strategy backtests and market replays with nanosecond-precision order book fills using **Titan**, and utilizes **Radhe** for local LLM inference to synthesize simulation results, explain metrics, and flag potential risks in plain, actionable language.

## Submodules

Kalpa integrates four key subprojects as Git submodules:

*   **[Titan](https://github.com/DevWizard-Vandan/Titan)**: A high-performance Rust matching engine and replay API (running on port `8080` by default).
*   **[Vajra](https://github.com/DevWizard-Vandan/Vajra)**: A Python embedding pipeline and vector store that acts as the regime memory for trading sessions.
*   **[Ritam](https://github.com/DevWizard-Vandan/ritam)**: A Python-based multi-agent orchestrator that serves as the brain of the system (running on port `8000` by default).
*   **[Radhe](https://github.com/DevWizard-Vandan/radhe-ai)**: A local LLM reasoning shell running Ollama/llama.cpp (running on port `11434` by default).

## Getting Started

To get started with Kalpa, clone the repository along with its submodules:

```bash
git clone --recurse-submodules https://github.com/DevWizard-Vandan/Kalpa
cd Kalpa
```

### Running Kalpa

*(Placeholder for future CLI execution command)*
```bash
kalpa run
```

## Architecture

```text
      RESEARCHER INPUT
            │
            ▼
         [Ritam] ──► [Vajra] find similar sessions
            │
            ├──► [Titan] replay with real order book fills
            │
            ├──► [Radhe] explain results in plain language
            │
            └──► REPORT: regime match, metrics, risk flags
```
