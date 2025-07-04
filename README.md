# Bootloader
> _From prompt to runnable agent swarm in 30 seconds._

[![CI](https://github.com/.../actions/workflows/ci.yml/badge.svg)]()
[![npm version](https://img.shields.io/npm/v/@gentlyventures/bootloader-core)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)]()
[![GitHub stars](https://img.shields.io/github/stars/gentlyventures/bootloader?style=social)]()
![Portia adapter](https://img.shields.io/badge/adapter-Portia-lightgrey)

## What is Bootloader?
Bootloader is a monorepo-based scaffolding engine that turns a single prompt into a fully wired multi-agent project—powered by Codex, Portia, or any adapter you choose.

## Table of Contents
- [What is Bootloader?](#what-is-bootloader)
- [Pre-Setup](#pre-setup)
- [Getting Started with Codex](#getting-started-with-codex)
- [Getting Started with Portia](#getting-started-with-portia)
- [Usage](#usage)
- [Core](packages/core/README.md)
- [Init Phase](packages/init-phase/README.md)
- [Portia Adapter](packages/portia-adapter/README.md)
- [LangGraph Adapter](packages/langgraph-adapter/README.md)
- [Tools](tools/README.md)
- [Examples](examples/README.md)

## Pre-Setup

- **GitHub repository**  
  You need an existing repo (public or private) where Bootloader will scaffold your project.

- **Codex Web UI & environment**  
  A valid OpenAI Enterprise Codex account. Follow “Setup your first environment” and “Connect additional GitHub repositories with Codex” in the OpenAI Admin guide:  
  https://help.openai.com/en/articles/11390924-enterprise-admin-getting-started-guide-for-codex

- **Project context injection**  
  Prepare your full app/project context (code, configs, docs) via our Save-to-Local Chrome extension, a manual template, or another AI helper so prompts include everything the scaffold needs. See “Overview” in the Codex docs:  
  https://platform.openai.com/docs/codex/overview

- **CLI & environment variables**  
  Ensure Node.js ≥ 14 and npm (or yarn) are installed, and set `OPENAI_API_KEY` in your shell or `.env` for Codex access.

Once you’ve completed these steps, proceed to [Getting Started with Codex](#getting-started-with-codex) or [Getting Started with Portia](#getting-started-with-portia).

## Getting Started with Codex

Follow the [Usage](#usage) or [Quickstart](#-quickstart) sections to initialize a Codex-powered agent swarm.

## Getting Started with Portia

Connect Bootloader to the Portia adapter to scaffold Portia-driven agent teams.

A modular, recursive build system for Codex and agent-driven AI applications.

This repo contains the foundational instructions, templates, and scaffolding logic to:

- Bootstrap new Codex modules with zero manual setup
- Recursively generate agents, components, orchestration layers, and UI
- Maintain a consistent structure across all Gently Ventures and client repos

## ✨ How It Works

Each module (e.g. `/src/modules/little-ai-theater/`) is created using:

- `AGENTS.md` – describes the recursive agent-building logic
- `TODO.md` – defines the component and file-level tasks
- `.codex-scope.json` – restricts Codex to only write where allowed
- `bootstrap-module.ts` – CLI to scaffold a new module in seconds
- `run-all.md` – top-level Codex executor that processes all TODOs recursively

## 📦 Folder Structure

```
Bootloader/
├── AGENTS.md
├── TODO.md
├── run-all.md
├── .codex-scope.json
├── bootstrap-module.ts
└── README.md
```

## 🛠️ Usage

In any Codex-connected repo (e.g. a client project):

### 1. Clone this bootloader:

```bash
git submodule add https://github.com/gentlyventures/Bootloader src/ops/bootloader
```

Or instruct Codex to do this in its first prompt:

```
Clone https://github.com/gentlyventures/Bootloader into /src/ops/bootloader and run bootstrap-module.ts
```

### 2. Bootstrap a new module:

```bash
npx ts-node src/ops/bootloader/bootstrap-module.ts ai-showcase
```

This creates:

```
/src/modules/ai-showcase/
  ├── AGENTS.md
  └── TODO.md
```

### 3. Instruct Codex to begin building:

```
Read /src/modules/ai-showcase/TODO.md and recursively build every item. Use the connected AGENTS.md to create agent folders and subfiles as needed.
```

### 4. Customize for Each Module

You can safely edit `TODO.md` or `AGENTS.md` in any module — the originals remain in this repo.

---

## 🔮 Agent Superpowers

Codex agents can spawn sub-agents recursively. Use `AGENT_TYPES.md` to pick the right roles and design an entire swarm. With a well-defined roadmap, Codex can self-plan and then self-build complete applications.

## 🚀 Quickstart

```bash
git submodule add https://github.com/gentlyventures/Bootloader src/ops/bootloader
npx ts-node src/ops/bootloader/bootstrap-module.ts
```

## ✅ Compatible With

* Codex (chat.openai.com/codex)
* Lovable.dev (design agents)
* GitHub CLI
* Node.js + TypeScript environments
* Any AI/LLM-based automation

---

## 🔐 Scope Protection

Codex should always check `.codex-scope.json` before generating files to ensure it stays within safe bounds.

---

## 🧭 Why Use This?

Because copy-pasting prompts and wiring files manually breaks the flow.

This system lets you say:

> “Codex, go here, clone that, and start building.”

And it just works.

---

## 📡 Using Bootloader Across Repos (e.g. Client Systems)

You can run Bootloader inside one repo while targeting a **different external repo** (like a client project) for actual module building.

### 🧠 Architecture

| Repo | Role |
|------|------|
| `Bootloader` | The recursive control kernel |
| `client-repo` (e.g. `companyco`) | The build target (external repo) |

### 🧪 Setup via ChatGPT

1. Open a clean ChatGPT thread
2. Train it on the bootloader (e.g. paste this README or high-level summary)
3. Upload `.txt` transcripts of any past planning/work sessions
4. Ask it to output:
   - ✅ A Codex prompt that uses this bootloader to scaffold an external module
   - ✅ A `roadmap.md` file to include in that external module

---

## 🧠 Passing Memory to Codex

Codex does not have access to past ChatGPT discussions or project planning.  
If you want Codex to:

- Know what this module is supposed to do
- Understand what has already been built in the repo
- Continue based on ChatGPT-generated strategy

Then you must include a “Planning Context” block in the Codex prompt like this:

```markdown
## 🧠 Planning Context (from ChatGPT)

- This app builds AI-generated trend reports for hedge funds
- Data is ingested from CSVs, embedded into Weaviate, and turned into insights via RAG
- A Figma template receives the injected content, which is exported to PDF
- Final reports are delivered via email or URL

As of 2025-06-17:
- ETL code exists
- No agents are scaffolded
- Bootloader is installed but not run yet

Codex must:
- Scaffold `/src/modules/companyco/`
- Create agents + TODO.md
- Execute recursively and log progress to `/docs/`
```

Paste that into the bottom of any Codex prompt before execution.

---

## Documentation

- Architecture overview: [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)
- Agent registry: [AGENTS.md](AGENTS.md)

## 🧑‍💻 Maintained by Gently Ventures

Feel free to fork and adapt this for your own recursive agent build systems.

MIT License.

### 🏷️ Repo Tags

- `codex`
- `agents`
- `recursive-build`
- `ai-infrastructure`
- `gently-ventures`
- `llm-pipeline`

## License

Bootloader is available under the MIT License for community use.  
For a commercial license (no copyleft), see [LICENSE-COMMERCIAL.md](LICENSE-COMMERCIAL.md) or contact [sales@yourcompany.com](mailto:sales@yourcompany.com).
