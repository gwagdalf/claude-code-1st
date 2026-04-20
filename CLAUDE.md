# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

Claude Code 학습 저장소 — [2시간 안에 마스터하기](https://www.youtube.com/watch?v=vxEo2BLM6A) 튜토리얼 기반, Spec-Driven Development(SDD) 중심.

## Documents

| 문서 | 설명 |
|------|------|
| [README.md](README.md) | 프로젝트 개요 |
| [QWEN.md](QWEN.md) | SDD 방법론, 저장소 구조, 개발 규칙 상세 |
| [First/README.md](First/README.md) | 튜토리얼 참고자료 |

### Spec-Driven Development (SDD)

| 문서 | 설명 |
|------|------|
| [sdd/sdd-examples.md](sdd/sdd-examples.md) | SDD GitHub 저장소 예제 |
| [sdd/spec-kit-examples.md](sdd/spec-kit-examples.md) | spec-kit 예제 |
| [sdd/spec-kit-guide.md](sdd/spec-kit-guide.md) | 주요 spec-kit 가이드 |
| [sdd/spec-kit-guide-powershell.md](sdd/spec-kit-guide-powershell.md) | PowerShell 전용 가이드 |
| [sdd/spec-kit-guide-mac.md](sdd/spec-kit-guide-mac.md) | Mac 전용 가이드 |
| [sdd/qwen/constitution-workflow.md](sdd/qwen/constitution-workflow.md) | Constitution 워크플로우 |
| [sdd/qwen/sdd-examples-qwen.md](sdd/qwen/sdd-examples-qwen.md) | Qwen 전용 SDD 예제 |
| [sdd/qwen/spec-kit-examples-qwen.md](sdd/qwen/spec-kit-examples-qwen.md) | Qwen 전용 spec-kit 예제 |
| [sdd/qwen/spec-kit-guide-qwen.md](sdd/qwen/spec-kit-guide-qwen.md) | Qwen 전용 spec-kit 가이드 |

## Configuration

`.qwen/settings.json` — Qwen 모델 제공업체 설정 (Alibaba Cloud MaaS):
- **qwen3-coder-plus** — 주 모델 (코드 생성/리팩토링/디버깅)
- **qwen-max** — 보조 모델 (일반 대화)
- API 키: `QWEN_API_KEY` 환경변수 (`.qwen/.env`)
- `rm -rf`, `del /F /Q` 차단 | `git`, `npm`, `python`, `tsc`, `eslint`, `prettier` 허용
- Git co-author 활성화, 체크포인팅 활성화
