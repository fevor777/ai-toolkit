# Project Guidelines

## Scope
These instructions apply to all GitHub Copilot requests in this repository.

## Repository Purpose
- This repository is for storing, organizing, and developing AI instructions and related content.
- Treat instruction files, prompts, and documentation as the primary artifacts.
- Do not assume this repository follows a conventional application, library, or service layout.

## Working Style
- Keep changes minimal and focused on the requested task.
- Prefer root-cause fixes over surface-level patches.
- Prefer the smallest change that materially improves clarity, consistency, or reuse of instruction content.

## Repository Conventions
- Prefer simple, readable organization and wording over elaborate abstractions.
- Avoid editing unrelated files while solving a task.
- Keep only repo-wide guidance in this file. Put folder-specific, format-specific, or task-specific guidance in narrower instruction files or docs.
- Before adding tooling, check whether the repository already has an established convention.
- State assumptions briefly when repository context is missing.
- If a requested change depends on an absent toolchain or missing files, prefer the smallest viable implementation and note the gap.

## Responses
- Before answering, think through this problem carefully.
  Consider the different factors involved, potential constraints, and various approaches before recommending the best solution.
- Keep responses minimal.
- For implementation tasks, return only the files changed and a brief final result unless more detail is requested.
- Do not explain GitHub Copilot mechanics, tool usage, or internal workflow unless explicitly asked.

