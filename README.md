<div align="center">

# 🐱 Jailbreaks-neko

**A modular research repository of system prompts, agent operating specifications, persona frameworks, and directive configurations for frontier and open-weight language models.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Research Purpose](https://img.shields.io/badge/purpose-LLM%20Security%20%26%20Research-blueviolet)](#research-ethics--disclaimer)
[![Format](https://img.shields.io/badge/format-Markdown%20%7C%20Modelfiles-blue)](#usage--integration)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat&logo=github)](https://github.com/sarukui/Jailbreaks-neko/pulls)
[![GitHub Stars](https://img.shields.io/github/stars/sarukui/Jailbreaks-neko?style=flat&logo=github&color=ff69b4)](https://github.com/sarukui/Jailbreaks-neko/stargazers)

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#supported-architectures">Supported Architectures</a> •
  <a href="#usage--integration">Usage & Integration</a> •
  <a href="#contribution-workflow">Contributing</a> •
  <a href="#research-ethics--disclaimer">Disclaimer</a>
</p>

</div>

---

## Overview

**Jailbreaks-neko** is a structured, research-driven collection documenting prompt-level instruction hierarchies, persona framing mechanisms, system directive overrides, and behavioral boundaries across state-of-the-art LLMs.

Modern conversational and coding agents rely on layered instructions—ranging from hardcoded system prompts and harness prefixes to repository-level `AGENTS.md` policies and user-level custom rules. This repository curates clean, reproducible, and paste-ready prompt artifacts designed to test and understand how models reconcile conflicting constraints, maintain persistent personas, and execute specialized operating parameters.

### Core Principles

- **Unabridged & Paste-Ready**: Prompts are archived in full without truncated blocks, placeholders, or abstract summaries.
- **Surface-Specific**: Each artifact is labeled according to its target integration point (API system messages, CLI workspace profiles, Ollama Modelfiles, or extension policies).
- **Architecture Aware**: Preserves formatting specific to particular tokenizers, chat templates, and agent orchestration frameworks.

> [!WARNING]
> **Research & Alignment Testing Notice**
> 
> The contents of this repository are provided solely for academic study, red-teaming, prompt-injection defense analysis, and robustness benchmarking. Do not use these materials for unlawful actions, harassment, harmful utility, or violating platform terms of service.

---

## Supported Architectures

The collection categorizes prompt configurations by model family, delivery harness, and deployment level:

### 1. Frontier & Reasoning Engines

| Model Ecosystem | Target Artifact | Primary Deployment Surface |
| :--- | :--- | :--- |
| **Claude Family** (Opus / Sonnet / Haiku) | Groundwork personas & writer-room configurations | System role / Workbench custom instructions |
| **DeepSeek** (V3 / V4 / 4.1 Series) | Operating specifications & unhedged response anchors | System prompt / Developer API payload |
| **Grok** (Build / 4.7 / Beta) | App-builder guidelines & `<CFG>` priority blocks | Target agent config slot / System harness |
| **Mistral** (Large / Pixtral / Codestral) | Direct execution profiles & developer persona locks | Developer API / Local vLLM chat templates |
| **Gemini** (Pro / Flash / Ultra series) | Hierarchical rule sets & global context definitions | System instructions / `GEMINI.md` |

### 2. Open-Weight & Multimodal Systems

| Model Family | Artifact Format | Scope & Target |
| :--- | :--- | :--- |
| **Qwen Series** (2.5 / 3.x / Coder) | System prompt directives | Inference engines (vLLM, TGI, SGLang) |
| **GLM & ZCode** (5.2 / 5.3 Flash / OpenCode) | System instructions & `AGENTS.md` drop-ins | Coding assistants & IDE plugins |
| **Kimi** (K2 / K3 Series) | Workspace operating profiles | Agent harness & API integration |
| **Gemma Series** | Custom system prompts & Modelfiles | Ollama, llama.cpp, LocalAI |

### 3. Local Runtime & Modelfiles

| Environment | Supported Artifact Type | Execution Target |
| :--- | :--- | :--- |
| **Ollama** | Complete Modelfile (`FROM` + `SYSTEM` + parameters) | `ollama create <name> -f <file>` |
| **llama.cpp / GGUF** | Raw system prompt templates | Sampling harness `--system-prompt` |
| **Coding Agents** | Repository & workspace specifications | Root-level `AGENTS.md` / `GEMINI.md` |

---

## Usage & Integration

### A. API System Messages (OpenAI, Anthropic, OpenRouter)

Inject the prompt directly into the initial `system` role parameter of the request payload:

```json
{
  "model": "deepseek-chat",
  "messages": [
    {
      "role": "system",
      "content": "<insert_prompt_content_here>"
    },
    {
      "role": "user",
      "content": "Your query here"
    }
  ]
}
```

### B. Coding Agents & Workspace Specifications

For developer environments that load contextual project guidelines (such as OpenCode, Gemini CLI, Cursor, or Antigravity):

1. Copy the designated configuration file.
2. Rename or place it as the active operating specification at your project root:
   ```bash
   cp model-specification.md ./AGENTS.md
   # Or for global user rules:
   cp model-specification.md ~/.config/opencode/AGENTS.md
   ```

### C. Local Models via Ollama

To build a standalone model profile with baked-in system instructions using Ollama:

```bash
# Create the local instance from the modelfile
ollama create neko-model -f ./modelfiles/gemma.modelfile

# Launch an interactive session
ollama run neko-model
```

---

## Contribution Workflow

Contributions, updates, and community findings are welcome. To maintain collection quality:

1. **Standardized Naming**: Use lowercase hyphenated filenames (e.g., `model-name-variant.md`).
2. **Complete Artifacts**: Ensure submissions are complete, verbatim, and ready for deployment without placeholders.
3. **Document Context**: Specify the model version, evaluation harness, and tested integration point in your pull request description.
4. **Versioning**: When a revised prompt addresses updated model checkpoints, increment the version (e.g., `opus-v2.md` rather than overwriting `opus-v1.md`).

---

## Research Ethics & Disclaimer

All materials compiled in **Jailbreaks-neko** are intended exclusively for **research, defensive security analysis, and educational evaluation**.

- **Safety & Robustness**: Understanding failure modes, jailbreak prompts, and instruction injection vulnerabilities is vital to engineering resilient guardrails and robust safety alignments in future LLM systems.
- **User Responsibility**: The maintainers do not endorse, promote, or encourage any harmful, deceptive, or unlawful activity. Users are solely responsible for ensuring their use of these prompts adheres to all applicable regional laws, acceptable use policies, and platform terms of service.

---

<div align="center">

🐾 **Curated with precision for LLM researchers and prompt engineers.**  
*Found an instruction conflict or outdated prompt? [Open an Issue](https://github.com/sarukui/Jailbreaks-neko/issues) or submit a PR.*

</div>
