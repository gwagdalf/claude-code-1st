# GitHub Spec-Kit 활용 예제 Repositories Top 10

> GitHub Spec-Kit을 사용한 프로젝트 및 관련 도구 저장소를 Star 순위대로 정리했습니다.
>
> **검색일**: 2026-04-20

---

## Spec-Kit 전체 워크플로우 파일 순서

```
 constitution.md → spec.md → plan.md → tasks.md → checklist.md
      (STEP 1)       (2)        (3)       (4)         (5)
```

| 순서 | 파일 | 위치 | 생성 명령 |
|:---:|---|---|---|
| **1** | `constitution.md` | `memory/constitution.md` | `/speckit.constitution` |
| **2** | `spec.md` | `specs/[feature]/spec.md` | `/speckit.specify` |
| **3** | `plan.md` | `specs/[feature]/plan.md` | `/speckit.plan` |
| **4** | `tasks.md` | `specs/[feature]/tasks.md` | `/speckit.tasks` |
| **5** | `checklist.md` | `specs/[feature]/checklist.md` | `/speckit.checklist` |

---

## Spec-Kit 기반 예제 Repositories Top 10

### 1. wordflowlab/article-writer — ⭐ 250

- **URL**: https://github.com/wordflowlab/article-writer
- **설명**: AI 어시스턴트(Claude Code, Cursor, Codex, Gemini)를 활용한 웨이보/위챗 공식 계정 글 작성 도구. Spec-Kit 워크플로우를 실제 애플리케이션에 적용한 사례.
- **핵심 파일**: Spec-Kit 기반 spec.md, plan.md, tasks.md 구조
- **특징**:
  - 4가지 글쓰기 모드: 코치, 빠른, 혼합, 프레임 제약
  - 소셜 미디어 자료실 시스템, 문서 크롤러
  - AI "톤" 감지 및 감소 (목표 <30% AI味)
  - 위챗 포매팅 지원
- **언어**: TypeScript (48.8%), JavaScript (22.5%), Shell (21.1%)
- **라이선스**: MIT

### 2. 888888888881/spec-kit-chinese — ⭐ 213

- **URL**: https://github.com/888888888881/spec-kit-chinese
- **설명**: GitHub Spec-Kit의 중국어 완전 현지화 버전. Cursor 등 AI 코딩 도구와 통합.
- **핵심 파일**: constitution.md, spec.md, plan.md, tasks.md (중국어 번역)
- **특징**:
  - Spec-Kit 전체 명령어 중국어 번역 제공
  - 8개 명령어: Requirements → Specification → Plan → Tasks → Implementation
  - `specify init --here --ai cursor --force`로 기존 프로젝트에서 바로 사용
- **언어**: Shell (100%)
- **라이선스**: MIT

### 3. panaversity/spec-kit-plus — ⭐ 205

- **URL**: https://github.com/panaversity/spec-kit-plus
- **설명**: github/spec-kit의 실용적인 포크. 확장 가능한 멀티 에이전트 AI 시스템 구축을 위한 패턴 & 템플릿 제공.
- **핵심 파일**: spec.md, plan.md, tasks.md + 아키텍처 히스토리, 프롬프트 히스토리
- **특징**:
  - OpenAI Agents SDK, MCP, A2A, Kubernetes, Dapr, Ray 기반 프로덕션 준비 스택
  - 명세, 아키텍처 히스토리, 프롬프트 히스토리, 테스트를 일급 산출물로 취급
  - 멀티 에이전트 시스템 패턴 포함
- **언어**: Python (50.7%), Shell (24.2%), PowerShell (15.9%)
- **라이선스**: MIT

### 4. dceoy/speckit-agent-skills — ⭐ 69

- **URL**: https://github.com/dceoy/speckit-agent-skills
- **설명**: Spec-Kit을 위한 재사용 가능한 에이전트 스킬. 여러 에이전트 런타임(Claude Code, Codex CLI, GitHub Copilot CLI, Gemini CLI)에서 동작.
- **핵심 파일**: speckit-* 스킬 템플릿 (constitution, specify, clarify, plan, analyze, tasks, implement)
- **특징**:
  - 4개 주요 AI 코딩 도구 동시 지원
  - SDD 워크플로우 전체 커버
  - 버전 릴리즈 관리 (v0.1.2)
- **언어**: Shell (100%)
- **라이선스**: AGPL-3.0

### 5. attilaszasz/sdd-pilot — ⭐ 62

- **URL**: https://github.com/attilaszasz/sdd-pilot
- **설명**: 구조화된 SDD 워크플로우를 강제하는 도구. 혼란스러운 코드 생성을 방지.
- **핵심 파일**: `specs/<feature-folder>/` 내 spec.md, plan.md, tasks.md
- **특징**:
  - 단계별 프로세스: Specify → Plan → Tasks → Implement → QC
  - 특화 AI 에이전트: Product Manager, Architect, Engineer, QC
  - Autopilot 모드: 미attended 기능 전달
  - GitHub Copilot, Gemini CLI, Claude Code, Windsurf, OpenCode, Codex 지원
  -活跃한 개발 (v0.26.1, 2026-04-09)
- **언어**: JavaScript (100%)
- **라이선스**: MIT

### 6. specmatic/specmatic-mcp-sample-with-spec-kit — ⭐ 33

- **URL**: https://github.com/specmatic/specmatic-mcp-sample-with-spec-kit
- **설명**: 계약 우선 개발(Contract-First)의 Spec-Kit 적용 사례. OpenAPI 명세가 기능 개발을 통해 자연스럽게 진화.
- **핵심 파일**: spec.md, plan.md, tasks.md + OpenAPI contracts
- **특징**:
  - Specmatic MCP를 지능형 가드레일로 사용
  - RED-GREEN-REFACTOR TDD 워크플로우
  - 스마트 계약 재사용 분석
  - 다중 도구 검증 (Specmatic MCP, Playwright)
- **언어**: Shell (100%)
- **라이선스**: MIT

### 7. leocamello/spec-kit-v-model — ⭐ 20

- **URL**: https://github.com/leocamello/spec-kit-v-model
- **설명**: Spec-Kit의 V-Model 확장 팩. 개발 명세와 테스트 명세의 쌍생성을 강제. 규제 수준 추적성 제공.
- **핵심 파일**: V-Model 레벨별 spec.md + test spec.md (4단계)
- **특징**:
  - 4개 V-Model 레벨: requirements, system-test, integration-test, unit-test
  - 14개 명령어 제공
  - 추적성 행렬 (Traceability Matrix) 생성
  - IEC 62304, ISO 26262, DO-178C 규정 준수
  - "AI가 초안을 작성. 인간이 결정. 스크립트가 검증. Git이 기록."
- **언어**: Shell (37.3%), PowerShell (32.7%), Python (30.0%)
- **라이선스**: MIT

### 8. MichelKerkmeester/opencode-spec-kit-framework — ⭐ 12

- **URL**: https://github.com/MichelKerkmeester/opencode-spec-kit-framework
- **설명**: AI 지원 코딩 환경. Spec-Kit, 메모리, 에이전트, 스킬을 통합한 프레임워크.
- **핵심 파일**: Spec-Kit 기반 명세 구조 + memory-bank
- **특징**:
  - 10개 특화 에이전트 + 게이트 라우팅 시스템
  - 21개 스킬 (문서화, 코드, MCP, cross-AI CLI)
  - 56개 MCP 도구 (47 메모리 + 7 코드 + 1 순차적 사고)
  - 4단계 Spec-Kit 문서 + 20개 검증 규칙
  - 로컬 우선 인지 메모리 (하이브리드 검색)
- **언어**: 다양
- **라이선스**: MIT

### 9. GregorBiswanger/copilot-spec-driven-template — ⭐ 10

- **URL**: https://github.com/GregorBiswanger/copilot-spec-driven-template
- **설명**: GitHub Copilot을 위한 SDD 템플릿. `/specify` → `/plan` → implement → `/compile` → `/spec-lifecycle` 워크플로우.
- **핵심 파일**: `.github/specs/` (backlog/active/done), `.github/prompts/`, `.github/agents/`
- **특징**:
  - 명세 수명주기별 폴더 구조: backlog → active → done
  - `.github/memory-bank/` 프로젝트 컨텍스트
  - `.github/copilot-instructions.md` 저장소 전체 규칙
  - 재사용 가능한 프롬프트 워크플로우
- **언어**: 다양
- **라이선스**: MIT

### 10. IuriiD/viral2viral — ⭐ 26

- **URL**: https://github.com/IuriiD/viral2viral
- **설명**: Spec-Kit을 활용한 AI 영상 클로닝 도구. UGC(User Generated Content) 영상을 자동으로 클론.
- **핵심 파일**: Spec-Kit 기반 spec.md, plan.md, tasks.md 구조
- **특징**:
  - Spec-Kit을 실제 ML/AI 프로젝트에 적용한 사례
  - 영상 처리 파이프라인
  - UGC 콘텐츠 자동화
- **언어**: Python
- **라이선스**: MIT

---

## 요약 비교표

| 순위 | Repository | Stars | 유형 | 핵심 특징 |
|:---:|---|---:|---|---|
| 1 | [article-writer](https://github.com/wordflowlab/article-writer) | 250 | 실제 앱 | AI 글쓰기 도구, Spec-Kit 적용 사례 |
| 2 | [spec-kit-chinese](https://github.com/888888888881/spec-kit-chinese) | 213 | 현지화 | 중국어 번역, Cursor 통합 |
| 3 | [spec-kit-plus](https://github.com/panaversity/spec-kit-plus) | 205 | 확장 | 멀티 에이전트, Kubernetes, MCP |
| 4 | [speckit-agent-skills](https://github.com/dceoy/speckit-agent-skills) | 69 | 도구 | 범용 에이전트 스크, 4개 AI 도구 지원 |
| 5 | [sdd-pilot](https://github.com/attilaszasz/sdd-pilot) | 62 | 도구 | Autopilot 모드, QC 게이트 |
| 6 | [specmatic-mcp-sample](https://github.com/specmatic/specmatic-mcp-sample-with-spec-kit) | 33 | 샘플 | 계약 우선 개발, OpenAPI 진화 |
| 7 | [viral2viral](https://github.com/IuriiD/viral2viral) | 26 | 실제 앱 | AI 영상 클로닝 |
| 8 | [spec-kit-v-model](https://github.com/leocamello/spec-kit-v-model) | 20 | 확장 | V-Model, 규제 준수, 추적성 |
| 9 | [opencode-spec-kit](https://github.com/MichelKerkmeester/opencode-spec-kit-framework) | 12 | 프레임워크 | 10개 에이전트, 56개 MCP 도구 |
| 10 | [copilot-spec-template](https://github.com/GregorBiswanger/copilot-spec-driven-template) | 10 | 템플릿 | Copilot 전용, 수명주기 관리 |

---

## 학습용 추천

### Spec-Kit을 처음 배우는 분
1. **spec-kit-chinese** — 한국어/중국어 개발자도 번역 구조를 배우기 좋음
2. **copilot-spec-driven-template** — 폴더 구조가 명확하고 Copilot과 바로 사용 가능

### 실제 애플리케이션 사례를 보고 싶은 분
3. **article-writer** — Spec-Kit으로 실제 프로덕션 앱을 만든 사례
4. **viral2viral** — ML/AI 프로젝트에 Spec-Kit 적용 사례

### 고급/확장 사례
5. **spec-kit-plus** — 멀티 에이전트, Kubernetes, Dapr 등 엔터프라이즈급
6. **spec-kit-v-model** — 규제 산업(의료, 자동차, 항공) 수준의 추적성

### 도구/자동화
7. **sdd-pilot** — Autopilot 모드로 자동 기능 전달
8. **speckit-agent-skills** — 여러 AI 도구에서 재사용 가능한 스킬

---

`★ Insight ─────────────────────────────────────`
- Spec-Kit 생태계는 크게 3가지로 나뉩니다: (1) 실제 애플리케이션 사례, (2) 도구/확장, (3) 템플릿/현지화. 학습 목적이라면 템플릿 계열부터 시작해 실제 사례를 분석하는 것이 좋습니다.
- constitution.md는 프로젝트당 1개, 나머지는 기능(feature)별로 생성됩니다. 이 구조를 이해하는 것이 Spec-Kit 활용의 첫걸음입니다.
- 많은 프로젝트가 Spec-Kit의 `/speckit.*` 명령어를 그대로 사용하기보다, 자신들의 워크플로우에 맞게 변형하여 사용하고 있습니다.
`─────────────────────────────────────────────────`
