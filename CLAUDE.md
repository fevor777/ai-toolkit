# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This repository stores, organizes, and develops AI instructions, prompts, and agent definitions. The primary artifacts are Markdown files — there is no application code, build system, or test framework.

## Working Style

- Keep changes minimal and focused on the requested task.
- Prefer the smallest change that materially improves clarity, consistency, or reuse.
- Avoid editing unrelated files while solving a task.
- State assumptions briefly when context is missing.

## Architecture

The repo follows a **fan-out / consensus orchestration pattern** for GitHub Copilot agents:

- **`.github/copilot-instructions.md`** — repo-wide Copilot instructions (applies to all requests)
- **`.github/agents/ConsensusRouter.agent.md`** — the only `user-invocable: true` agent; fans a question out to three model-specific sub-agents in parallel, then synthesizes or surfaces disagreements
- **`.github/agents/CarefulAnswer.agent.md`** — sub-agent using Claude Sonnet 4.5 (careful/thorough answers)
- **`.github/agents/FastAnswer.agent.md`** — sub-agent using GPT-5.4 mini (quick answers)
- **`.github/agents/Model_GPT4o.agent.md`** — sub-agent using GPT-4o
- **`.github/agents/PromptExpert.instructions.md`** — standalone prompt-engineering assistant; runs an interview (Task/Context/Format/Constraints) then generates a Role+Task+Steps+Format prompt

## Conventions

- Agent files use YAML frontmatter with fields: `description`, `name`, `model`, `tools`, `agents`, `argument-hint`, `user-invocable`, `disable-model-invocation`.
- Sub-agents (model branches) are `user-invocable: false`; orchestrators are `user-invocable: true`.
- Instruction content and agent prompts are written in Russian.
- Repo-wide guidance belongs in `.github/copilot-instructions.md`; scope-specific guidance belongs in individual agent or instruction files.
- Before adding new tooling or infrastructure, check whether the repository already has an established convention.

## Responses
- Before answering, think through this problem carefully.
  Consider the different factors involved, potential constraints, and various approaches before recommending the best solution.

## Agent Usage
- Do NOT proactively spawn `critic-router` or any `critic-*` subagents on your own. These are expensive multi-agent pipelines (4+ subagents per call). Only invoke them when the user explicitly calls `/critic`.
- Do NOT use the `critic-router` agent type via the `Agent` tool unless directly instructed by the user.