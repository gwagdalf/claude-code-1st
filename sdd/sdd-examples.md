# SDD (Spec-Driven Development) GitHub 인기 Repositories Top 10

> Claude Code를 활용한 SDD 방식 개발에 사용할 수 있는 GitHub 저장소 추천 목록입니다.
> spec.md, plan.md, architect.md, task.md, implement.md 파일을 활용하는 저장소들을 Star 순위대로 정리했습니다.
>
> **검색일**: 2026-04-20

---

## 1. obra/superpowers — ⭐ 161k

- **URL**: https://github.com/obra/superpowers
- **설명**: 에이전트 기반 기술 프레임워크 & 소프트웨어 개발 방법론. 구성 가능한(composable) 기술 세트로 코딩 에이전트가 구조화된 TDD 기반 워크플로우를 따르도록 합니다.
- **핵심 파일**: `writing-plans/SKILL.md`, `brainstorming/SKILL.md`, `test-driven-development/SKILL.md` 등 14개 이상의 워크플로우 스킬
- **특징**:
  - TDD(테스트 주도 개발) 강제
  - 구조화된 기획 → 명세 → 구현 파이프라인
  - Claude Code, Cursor 등 주요 AI 코딩 도구 지원
- **라이선스**: MIT

## 2. github/spec-kit — ⭐ 89.5k

- **URL**: https://github.com/github/spec-kit
- **설명**: GitHub 공식 SDD 툴킷. 제품 시나리오에 집중하고 예측 가능한 결과를 도출할 수 있게 합니다.
- **핵심 파일**: `spec.md`, `plan.md`, `tasks.md` 자동 생성
- **특징**:
  - CLI 도구(`specify`) 제공
  - 30개 이상의 AI 코딩 에이전트 지원
  - 익스텐션 & 프리셋으로 확장 가능
  - 명세 → 계획 → 태스크 → 구현의 표준 파이프라인
- **라이선스**: MIT

## 3. gsd-build/get-shit-done — ⭐ 55.2k

- **URL**: https://github.com/gsd-build/get-shit-done
- **설명**: Claude Code를 위한 경량 SDD 시스템. 메타 프롬프팅, 컨텍스트 엔지니어링, 멀티 에이전트 오케스트레이션으로 "컨텍스트 붕괴" 문제를 해결합니다.
- **핵심 파일**: `spec.md`, `plan.md`, `task.md` 기반 단계별 워크플로우
- **특징**:
  - 자동 단계별 워크플로우: discuss → plan → execute → verify → ship
  - 태스크별 병렬 실행 (각 태스크마다 컨텍스트 초기화)
  - 태스크별 원자적 Git 커밋
  - 보안 강화 (프롬프트 인젝션 감지)
  - Claude Code, OpenCode, Gemini, Cursor, Windsurf 등 지원
- **라이선스**: MIT

## 4. bmad-code-org/BMAD-METHOD — ⭐ 45.2k

- **URL**: https://github.com/bmad-code-org/BMAD-METHOD
- **설명**: AI 기반 애자일 개발 프레임워크. 규모 적응 지능, 특화 에이전트(PM, Architect, Developer, UX 등), 34개 이상의 워크플로우 제공.
- **핵심 파일**: 명세서, 설계서, 태스크 분해 템플릿
- **특징**:
  - 12개 이상의 도메인 특화 에이전트
  - Party Mode: 멀티 에이전트 협업
  - Spec-kit 방법론 통합
  - 버그 수정부터 엔터프라이즈 시스템까지 전 라이프사이클 지원
- **라이선스**: MIT

## 5. Fission-AI/OpenSpec — ⭐ 41.5k

- **URL**: https://github.com/Fission-AI/OpenSpec
- **설명**: AI 코딩 어시스턴트를 위한 SDD 프레임워크. 코드 작성 전 요구사항에 대한 경량 명세 레이어를 제공합니다.
- **핵심 파일**: 명세 파일, 설계 파일, 구현 계획
- **특징**:
  - 슬래시 명령: `/opsx:propose` → `/opsx:apply` → `/opsx:archive`
  - 제안 → 명세 → 설계 → 구현의 반복적 프로세스
  - Brownfield 프로젝트 호환
  - 25개 이상의 AI 도구 지원
  - Waterfall이 아닌 반복적(Iterative) 접근
- **라이선스**: MIT

## 6. hesreallyhim/awesome-claude-code — ⭐ 39.9k

- **URL**: https://github.com/hesreallyhim/awesome-claude-code
- **설명**: Claude Code를 위한 스킬, 훅, 슬래시 명령, 에이전트 오케스트레이터, 플러그인의 curated 목록.
- **핵심 파일**: SDD 관련 스킬 & 워크플로우 링크 모음
- **특징**:
  - Agent Skills, Workflows & Knowledge Guides, Tooling, Hooks, Slash-Commands 카테고리
  - SDD 워크플로우 관련 스킬 다수 포함
  - Claude Code 생태계의 종합 가이드
- **라이선스**: CC BY-NC-ND 4.0

## 7. Pimzino/claude-code-spec-workflow — ⭐ 3.7k

- **URL**: https://github.com/Pimzino/claude-code-spec-workflow
- **설명**: Claude Code를 위한 자동화 SDD 워크플로우. 지능형 태스크 실행 지원.
- **핵심 파일**: Requirements → Design → Tasks 단계별 템플릿
- **특징**:
  - 요구사항 → 설계 → 태스크 → 구현 자동화 파이프라인
  - 버그 수정 워크플로우: Report → Analyze → Fix → Verify
  - TypeScript 기반 (81.7%)
  - Claude Code 전용 최적화
- **라이선스**: MIT

## 8. liatrio-labs/spec-driven-workflow — ⭐ 79

- **URL**: https://github.com/liatrio-labs/spec-driven-workflow
- **설명**: AI 지원 코딩을 위한 경량 Markdown 기반 SDD 워크플로우.
- **핵심 파일**: `SDD-1` ~ `SDD-4` 구조화 프롬프트
- **특징**:
  - 4단계 프롬프트 워크플로우 (명세 생성 → 태스크 분해 → 구현 관리 → 검증)
  - 계획 품질 게이트 (필수 감사)
  - 컨텍스트 검증 마커 (SDD1️⃣~SDD4️⃣)
  - 종속성 없음 — 순수 Markdown
  - `slash-command-manager`로 슬래시 명령 설치 가능
- **라이선스**: MIT

## 9. SamHath03/spec-driven-ai — ⭐ (소규모)

- **URL**: https://github.com/SamHath03/spec-driven-ai
- **설명**: Claude Code를 위한 Spec-Driven 워크플로우. Markdown 파일로 상태를 관리합니다.
- **핵심 파일**: `spec.md`, `plan.md`, `task.md` 기반 상태 추적
- **특징**:
  - Markdown 파일 기반 상태 관리
  - Claude Code 전용 워크플로우
  - 컨텍스트 로테이션 방지 설계
- **라이선스**: MIT

## 10. ronwg/spec-driven-dev — ⭐ 6

- **URL**: https://github.com/ronwg/spec-driven-dev
- **설명**: Amazon의 Spec-Driven 워크플로우에서 영감받은 Claude Code 전용 명령 모음.
- **핵심 파일**: `/requirements`, `/design`, `/tasks`, `/execute-next` 슬래시 명령
- **특징**:
  - `/requirements`: BDD 스타일 요구사항 생성
  - `/design`: 요구사항 기반 기술 설계 문서
  - `/tasks`: 설계 기반 실행 가능한 구현 계획
  - `/execute-next`: 다음 미완료 태스크 자동 구현
- **라이선스**: MIT

---

## 요약 비교표

| 순위 | Repository | Stars | 핵심 특징 |
|:---:|---|---:|---|
| 1 | [superpowers](https://github.com/obra/superpowers) | 161k | TDD 기반 구조화 워크플로우 |
| 2 | [spec-kit](https://github.com/github/spec-kit) | 89.5k | GitHub 공식 SDD 툴킷 |
| 3 | [get-shit-done](https://github.com/gsd-build/get-shit-done) | 55.2k | 멀티 에이전트, 병렬 실행 |
| 4 | [BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD) | 45.2k | 21개 AI 에이전트, Party Mode |
| 5 | [OpenSpec](https://github.com/Fission-AI/OpenSpec) | 41.5k | 반복적 명세, Brownfield 지원 |
| 6 | [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | 39.9k | Claude Code 생태계 종합 |
| 7 | [claude-code-spec-workflow](https://github.com/Pimzino/claude-code-spec-workflow) | 3.7k | 자동화 파이프라인 |
| 8 | [spec-driven-workflow](https://github.com/liatrio-labs/spec-driven-workflow) | 79 | 순수 Markdown, 4단계 워크플로우 |
| 9 | [spec-driven-ai](https://github.com/SamHath03/spec-driven-ai) | 소규모 | Markdown 상태 관리 |
| 10 | [spec-driven-dev](https://github.com/ronwg/spec-driven-dev) | 6 | Amazon 스타일 BDD 워크플로우 |

---

## 추천 시작 가이드

### 초보자에게 추천
1. **spec-kit** — GitHub 공식 툴킷으로 표준 SDD 워크플로우 학습에 최적
2. **superpowers** — 가장 많은 Star, TDD 기반 구조화된 개발

### 중급/엔터프라이즈
3. **BMAD-METHOD** — 대규모 프로젝트, 멀티 에이전트 협업
4. **OpenSpec** — 기존 코드베이스(Brownfield)에 SDD 적용

### 경량/간단한 프로젝트
5. **spec-driven-workflow** — 순수 Markdown, 종속성 없음

---

`★ Insight ─────────────────────────────────────`
- SDD의 핵심은 "명세가 소스 오브 트루스"라는 점입니다. 코드는 명세에서 유도되는 결과물일 뿐입니다.
- 최근 SDD 프레임워크들은 spec.md → plan.md → task.md → implement.md의 공통 파일 구조를 따르며, 이는 AI 코딩 에이전트의 컨텍스트 관리에 최적화되어 있습니다.
- Star 수가 높은 프로젝트일수록 생태계가 풍부하고 문서화가 잘 되어 있으나, 작은 프로젝트일수록 단순하고 배우기 쉬울 수 있습니다.
`─────────────────────────────────────────────────`
