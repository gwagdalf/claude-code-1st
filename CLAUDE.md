# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This is a learning repository for exploring Claude Code, created while following the tutorial: [클로드 코드 2시간 안에 마스터하기 (Master Claude Code in 2 Hours)](https://www.youtube.com/watch?v=vxEvo2BLM6A).

## Qwen Model Provider

The `.qwen/settings.json` configures an alternative model provider (Alibaba Cloud MaaS) with two models:

- **qwen3-coder-plus** — primary model, optimized for code generation, refactoring, and debugging (temperature 0.1, max_tokens 8192, thinking mode enabled)
- **qwen-max** — secondary model for general conversation

The API key is read from the `QWEN_API_KEY` environment variable (set in `.qwen/.env`).

Key settings:
- Context auto-loads from `src/`, `lib/`, `tests/`, `docs/` when those directories exist
- Shell commands `rm -rf` and `del /F /Q` are blocked; `git`, `npm`, `python`, `tsc`, `eslint`, `prettier` are pre-allowed
- Git co-author is enabled (`gitCoAuthor: true`)
- Checkpointing is enabled
