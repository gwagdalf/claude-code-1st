# GitHub Spec-Kit Windows PowerShell 전용 SDD 개발 가이드

> **Spec-Driven Development (SDD)**: 명세(Specification)가 실행 가능해지고, 코드 구현을 직접 생성하는 개발 방식
>
> **플랫폼**: Windows PowerShell 전용 가이드
>
> **작성일**: 2026-04-20

---

## 목차

1. [SDD란 무엇인가?](#1-sdd란-무엇인가)
2. [왜 SDD가 필요한가?](#2-왜-sdd가-필요한가)
3. [PowerShell에서 Spec-Kit 설치하기](#3-powershell에서-spec-kit-설치하기)
4. [PowerShell에서 프로젝트 초기화](#4-powershell에서-프로젝트-초기화)
5. [6단계 워크플로우 완전 정복](#5-6단계-워크플로우-완전-정복)
6. [Windows 폴더 구조 이해하기](#6-windows-폴더-구조-이해하기)
7. [실전 예제: PowerShell로 할 일 앱 만들기](#7-실전-예제-powershell로-할-일-앱-만들기)
8. [Extensions & Presets](#8-extensions--presets)
9. [PowerShell 초보자를 위한 핵심 팁](#9-powershell-초보자를-위한-핵심-팁)
10. [PowerShell 유용한 명령어 모음](#10-powershell-유용한-명령어-모음)

---

## 1. SDD란 무엇인가?

### 전통적 개발 vs SDD

```
전통적 개발:
아이디어 → 머리 속에서 설계 → 바로 코드 작성 → "이게 맞나?" → 수정 → 수정 → ...

SDD (Spec-Driven Development):
아이디어 → 명세(Spec) 작성 → 구현 계획(Plan) → 태스크 분해(Tasks) → 코드 구현
```

**핵심 개념**: "명세가 곧 코드다" (Specs are the new code)

기존에는 명세 문서를 작성하고 나면 코드가 별도로 작성되어 명세와 코드 사이에 괴리가 생겼습니다. SDD에서는 **명세가 실행 가능(executable)**해집니다. 즉, AI가 명세를 읽고 코드를 직접 생성합니다.

### 3가지 개발 시나리오

| 시나리오 | 설명 | 예시 |
|---------|------|------|
| **0-to-1 (Greenfield)** | 무에서 유를 창조 | 완전히 새로운 앱 만들기 |
| **창의적 탐색** | 여러 구현 방식 병렬 탐색 | React vs Vue vs Svelte 비교 |
| **반복적 개선 (Brownfield)** | 기존 프로젝트에 기능 추가 | 기존 앱에 로그인 기능 추가 |

`★ Insight ─────────────────────────────────────`
SDD는 "생각의 버전 관리(version control for your thinking)"입니다. 코드는 최종 산출물일 뿐이고, 명세가 진정한 소스 오브 트루스입니다. 명세가 바뀌면 코드도 자동으로 따라갑니다.
`─────────────────────────────────────────────────`

---

## 2. 왜 SDD가 필요한가?

### 문제: "Vibe Coding"의 함정

AI 코딩 도구를 쓰다 보면 이런 경험을 하게 됩니다:

- "로그인 페이지 만들어줘" → AI가 대충 만듦 → "아니, 내가 원하는 건..." → 끝없는 수정
- 코드는 나오는데 구조가 엉망
- 보안, 규정, 디자인 시스템을 고려하지 않음
- 2주 후에 "이 코드 왜 이랬지?" 상태

### SDD의 해결책

| 문제 | SDD 해결 방법 |
|------|--------------|
| 모호한 프롬프트 | 명확한 spec.md로 "무엇(What)"과 "왜(Why)" 정의 |
| 기술적 결정의 암묵화 | plan.md에 명시적 기록, 검토 가능 |
| 컨텍스트 손실 | constitution.md에 불변 원칙 고정 |
| 거대한 한 번 생성 | tasks.md로 작은 테스트 가능 단위로 분해 |

---

## 3. PowerShell에서 Spec-Kit 설치하기

### 3.1 PowerShell 버전 확인

먼저 PowerShell 5.1 이상인지 확인합니다:

```powershell
$PSVersionTable.PSVersion
```

### 3.2 Python 3.11+ 설치

PowerShell에서 다음 명령어로 Python 설치를 확인합니다:

```powershell
# Python 버전 확인
python --version

# Python이 없으면 winget으로 설치
winget install Python.Python.3.12
```

> **참고**: 설치 후 **반드시 PowerShell을 재시작**하세요. PATH가 갱신됩니다.

### 3.3 Git 설치 확인

```powershell
# Git 버전 확인
git --version

# Git이 없으면 winget으로 설치
winget install Git.Git
```

### 3.4 uv 패키지 관리자 설치

**방법 1: PowerShell 명령어로 설치 (권장)**

```powershell
# PowerShell에서 uv 인스톨러 실행
irm https://astral.sh/uv/install.ps1 | iex
```

> `irm`은 `Invoke-RestMethod`, `iex`는 `Invoke-Expression`의 별칭입니다.

**방법 2: winget으로 설치**

```powershell
winget install --id=astral-sh.uv -e
```

**설치 확인:**

```powershell
uv --version
```

> **참고**: 설치 후 PowerShell을 재시작해야 `uv` 명령어를 인식합니다.

### 3.5 Spec-Kit 설치

```powershell
# 최신 버전 설치 (vX.Y.Z는 실제 버전 번호로 대체)
uv tool install specify-cli --from "git+https://github.com/github/spec-kit.git@vX.Y.Z"
```

> **주의**: PyPI에 있는 unofficial 패키지를 사용하지 마세요. 오직 `github.com/github/spec-kit`에서만 설치하세요.

### 3.6 설치 확인

```powershell
specify version
```

출력 예시:
```
specify-cli vX.Y.Z
```

### 3.7 버전 업그레이드

```powershell
# 최신 버전으로 업그레이드
uv tool upgrade specify-cli
```

---

## 4. PowerShell에서 프로젝트 초기화

### 4.1 새 프로젝트 생성

```powershell
# 새로운 프로젝트 생성
specify init my-awesome-app

# 프로젝트 생성 후 해당 디렉토리로 이동
Set-Location my-awesome-app

# 또는 축약형
cd my-awesome-app
```

### 4.2 현재 디렉토리에 초기화

```powershell
# 현재 작업 중인 디렉토리에 Spec-Kit 초기화
specify init .
```

### 4.3 AI 에이전트 지정

```powershell
# Claude Code 지정
specify init my-app --ai claude

# Cursor 지정
specify init my-app --ai cursor

# GitHub Copilot CLI 지정
specify init my-app --ai copilot

# Gemini CLI 지정
specify init my-app --ai gemini
```

### 4.4 PowerShell 스크립트 명시 지정

```powershell
# PowerShell 스크립트(.ps1)를 명시적으로 생성하도록 지정
specify init my-app --ai claude --script ps
```

### 4.5 오프라인 설치 (Air-Gapped 환경)

```powershell
# 1. 연결된 머신에서 wheel 빌드 및 의존성 다운로드
python -m build --wheel
pip download -d dist/

# 2. dist 폴더를 오프라인 머신으로 복사

# 3. 오프라인 머신에서 설치
pip install --no-index --find-links=".\dist" specify-cli

# 4. 오프라인 초기화
specify init my-project --ai claude --offline
```

### 4.6 초기화 후 생성되는 폴더 구조 (Windows)

```
my-awesome-app\
├── .github\
│   └── prompts\
│       ├── specify.prompt.md     ← /speckit.specify 프롬프트
│       ├── plan.prompt.md        ← /speckit.plan 프롬프트
│       └── tasks.prompt.md       ← /speckit.tasks 프롬프트
├── .specify\
│   ├── memory\
│   │   ├── constitution.md                ← 프로젝트 헌법
│   │   └── constitution_update_checklist.md
│   ├── scripts\
│   │   ├── create-new-feature.ps1         ← 새 기능 생성 PowerShell 스크립트
│   │   └── setup-template.ps1             ← 템플릿 설정 PowerShell 스크립트
│   └── templates\
│       ├── spec-template.md     ← 명세 템플릿
│       ├── plan-template.md     ← 계획 템플릿
│       └── tasks-template.md    ← 태스크 템플릿
```

> **Windows 참고**: PowerShell로 초기화하면 `.specify\scripts\` 폴더에 `.sh` 대신 **`.ps1`** 파일이 생성됩니다.

---

## 5. 6단계 워크플로우 완전 정복

전체 워크플로우는 6단계로 구성됩니다. **순서가 매우 중요**합니다.

```
┌──────────────────────────────────────────────────────┐
│  STEP 1: Constitution (헌법)                          │
│  "/speckit.constitution"                              │
│  "이 프로젝트에서 절대 깨지 않는 규칙은?"               │
└──────────────────────────────────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────────┐
│  STEP 2: Specify (명세)                               │
│  "/speckit.specify"                                   │
│  "무엇(What)을 왜(Why) 만드는가?"                      │
└──────────────────────────────────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────────┐
│  STEP 2.5: Clarify (명세 명확화)                      │
│  "/speckit.clarify"                                   │
│  "명세에서 모호한 부분은?"                              │
└──────────────────────────────────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────────┐
│  STEP 3: Plan (계획)                                  │
│  "/speckit.plan"                                      │
│  "어떻게(How) 만들 것인가?"                            │
└──────────────────────────────────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────────┐
│  STEP 4: Tasks (태스크 분해)                           │
│  "/speckit.tasks"                                     │
│  "작은 실행 단위로 쪼개자"                             │
└──────────────────────────────────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────────┐
│  STEP 5: Implement (구현)                             │
│  "/speckit.implement"                                 │
│  "태스크를 하나씩 실행!"                               │
└──────────────────────────────────────────────────────┘
```

### STEP 1: Constitution (헌법) — `/speckit.constitution`

**제일 먼저** 만드는 문서입니다. 프로젝트의 **불변 원칙**을 정의합니다.

```markdown
# 프로젝트 헌법 (constitution.md)

## 핵심 원칙
1. 테스트 먼저 작성한다 (TDD: Red/Green/Refactor)
2. 라이브러리를 먼저 만들고, CLI로 감싼다
3. 복잡도는 최대 3개 프로젝트까지만
4. 불필요한 추상화를 만들지 않는다
5. 통합 테스트가 단위 테스트보다 중요하다
```

**위치는** `.specify\memory\constitution.md` 입니다.

**왜 먼저 만들까요?** → 이후 모든 명세와 계획이 이 헌법을 준수해야 하기 때문입니다. 헌법을 위반하는 plan.md는 자동 거부됩니다.

### STEP 2: Specify (명세) — `/speckit.specify`

기능의 **"무엇(What)"과 "왜(Why)"**를 정의합니다. **기술 스택은 여기서 말하지 않습니다.**

AI 에이전트에게 이렇게 말합니다:

> "사용자가 이메일로 로그인하고, 할 일을 CRUD하는 앱을 만들고 싶어."

그러면 AI가 다음을 생성합니다:

```
specs\001-todo-app\
└── spec.md
    ├── 요구사항
    ├── 유저 스토리
    │   ├── "사용자로서 이메일로 로그인하고 싶다"
    │   ├── "사용자로서 할 일을 추가하고 싶다"
    │   └── ...
    └── 성공 조건
```

**중요**: spec.md에는 **어떻게** 구현할지 (React? Flask? PostgreSQL?)를 적지 않습니다. 오직 **무엇**을 원하는지만 적습니다.

### STEP 2.5: Clarify (명세 명확화) — `/speckit.clarify`

plan 단계로 가기 전에, 명세의 **모호한 부분**을 찾아 질문합니다.

예를 들어:
- "할 일의 마감 날짜는 필수인가?"
- "로그인 실패 시 몇 번까지 재시도 가능한가?"
- "모바일 반응형이 필요한가?"

AI가 `[NEEDS CLARIFICATION]` 마커로 표시된 부분을 질문으로 바꿔줍니다.

### STEP 3: Plan (계획) — `/speckit.plan`

드디어 **"어떻게(How)"**를 정의합니다. 여기서 기술 스택을 선택합니다.

```
specs\001-todo-app\
├── spec.md         ← STEP 2에서 생성
├── plan.md         ← STEP 3에서 생성 (새로!)
├── data-model.md   ← 데이터 모델
├── contracts\      ← API 계약
├── quickstart.md   ← 빠른 시작 가이드
└── research.md     ← 조사 자료
```

**plan.md는 constitution.md의 검사를 받습니다.** 헌법 위반 시 재작성됩니다.

예시:
```markdown
# 구현 계획

## 기술 스택
- 프론트엔드: React 18 + TypeScript
- 백엔드: FastAPI (Python)
- 데이터베이스: SQLite (개발) → PostgreSQL (프로덕션)

## 아키텍처
- REST API
- JWT 인증
```

### STEP 4: Tasks (태스크 분해) — `/speckit.tasks`

spec.md와 plan.md를 읽고 **작고 테스트 가능한 작업 단위**로 분해합니다.

```
specs\001-todo-app\
└── tasks.md
    ├── Task 1: 사용자 등록 API 엔드포인트 생성
    ├── Task 2: 로그인 API 엔드포인트 생성
    ├── Task 3: 할 일 CRUD API 생성
    ├── Task 4: 프론트엔드 로그인 페이지
    ├── Task 5: 프론트엔드 할 일 목록 페이지
    └── ...
```

병렬 가능한 태스크는 `[P]` 마커가 붙습니다.

### STEP 5: Implement (구현) — `/speckit.implement`

tasks.md의 태스크를 **순서대로** 실행합니다. AI가 코드를 직접 작성합니다.

- 각 태스크마다 독립된 컨텍스트에서 실행 → "컨텍스트 붕괴" 방지
- 태스크 완료 시 원자적 Git 커밋
- 개발자는 각 태스크의 결과만 검토하면 됨

---

## 6. Windows 폴더 구조 이해하기

전체 폴더 구조를 한눈에 보면 (Windows 표기법):

```
my-awesome-app\
├── .github\
│   └── prompts\
│       ├── specify.prompt.md     ← /speckit.specify 프롬프트 정의
│       ├── plan.prompt.md        ← /speckit.plan 프롬프트 정의
│       └── tasks.prompt.md       ← /speckit.tasks 프롬프트 정의
│
├── .specify\
│   ├── memory\
│   │   ├── constitution.md                ← [프로젝트당 1개] 헌법
│   │   └── constitution_update_checklist.md
│   │
│   ├── scripts\
│   │   ├── create-new-feature.ps1         ← 새 기능 생성 PowerShell 스크립트
│   │   └── setup-template.ps1             ← 템플릿 설정 PowerShell 스크립트
│   │
│   └── templates\
│       ├── spec-template.md     ← spec.md 템플릿
│       ├── plan-template.md     ← plan.md 템플릿
│       └── tasks-template.md    ← tasks.md 템플릿
│
├── specs\
│   ├── 001-todo-app\            ← [기능별] 첫 번째 기능
│   │   ├── spec.md              ← 명세
│   │   ├── plan.md              ← 계획
│   │   ├── tasks.md             ← 태스크
│   │   ├── data-model.md        ← 데이터 모델
│   │   ├── contracts\           ← API 계약
│   │   ├── quickstart.md        ← 빠른 시작
│   │   └── research.md          ← 조사 자료
│   │
│   └── 002-user-profile\        ← [기능별] 두 번째 기능
│       ├── spec.md
│       ├── plan.md
│       └── tasks.md
│
└── src\                         ← 실제 코드 (AI가 생성)
    └── ...
```

### 핵심 규칙

| 파일 | 개수 | 위치 | 언제 생성 |
|:---:|:---:|---|---|
| `constitution.md` | **프로젝트당 1개** | `.specify\memory\` | 프로젝트 시작 시 |
| `spec.md` | **기능별 1개** | `specs\[기능]\` | 새 기능 추가 시 |
| `plan.md` | **기능별 1개** | `specs\[기능]\` | spec.md 작성 후 |
| `tasks.md` | **기능별 1개** | `specs\[기능]\` | plan.md 작성 후 |

### PowerShell에서 폴더 탐색하기

```powershell
# 프로젝트 구조 한눈에 보기
Get-ChildItem -Recurse -Depth 2 | Select-Object FullName

# spec.md 파일들만 찾기
Get-ChildItem -Recurse -Filter "spec.md" | Select-Object FullName

# 최근 수정된 파일 확인
Get-ChildItem -Recurse | Sort-Object LastWriteTime -Descending | Select-Object -First 10 Name, LastWriteTime

# specs 폴더 트리 구조 보기
tree specs /F
```

---

## 7. 실전 예제: PowerShell로 할 일 앱 만들기

### 전체 과정 따라하기

#### 0. 프로젝트 초기화

```powershell
# 프로젝트 생성
specify init todo-app --ai claude

# 프로젝트 디렉토리로 이동
Set-Location todo-app
```

#### 1. 헌법 만들기

AI 에이전트(Claude Code 등)를 열고:

```
/speckit.constitution
```

대화 예시:

> **AI**: "이 프로젝트의 핵심 원칙을 정립하겠습니다. 다음 질문에 답해주세요:
> 1. 테스트는 어떻게 진행하시겠습니까? (TDD / 구현 후 테스트 / 테스트 없음)
> 2. 프론트엔드와 백엔드를 분리하시겠습니까?
> 3. 데이터베이스는 무엇이 좋을까요?"

> **나**: "TDD로 하고, 프론트/백 분리하고, SQLite로 하자."

→ `.specify\memory\constitution.md` 생성 완료

PowerShell에서 확인:

```powershell
Get-Content .specify\memory\constitution.md
```

#### 2. 명세 만들기

```
/speckit.specify
```

> **AI**: "어떤 기능을 만들까요?"

> **나**: "사용자가 할 일을 추가·수정·삭제하고, 완료 표시를 할 수 있는 앱을 만들고 싶어."

→ `specs\001-todo-app\spec.md` 생성:
- 유저 스토리 5개
- 성공 조건 8개
- 기능 요구사항 6개

PowerShell에서 확인:

```powershell
Get-Content specs\001-todo-app\spec.md
```

#### 3. 명세 명확화

```
/speckit.clarify
```

> **AI**: "spec.md에서 다음 부분이 모호합니다:
> 1. 할 일의 마감일이 필요한가요?
> 2. 사용자 인증이 필요한가요?
> 3. 카테고리 분류 기능이 있나요?"

> **나**: "마감일은 선택 사항으로, 인증은 필요 없고, 카테고리는 나중에 추가."

→ spec.md 업데이트

#### 4. 계획 세우기

```
/speckit.plan
```

> **AI**: "기술 스택을 정하겠습니다:
> - 프론트엔드: React + TypeScript
> - 백엔드: FastAPI
> - 저장소: 로컬 JSON 파일 (간단한 앱을 위해)"

→ `specs\001-todo-app\plan.md` 생성 (constitution.md 준수 검증 완료)

#### 5. 태스크 분해

```
/speckit.tasks
```

→ `specs\001-todo-app\tasks.md` 생성:

```markdown
## Tasks
- [ ] Task 1: 백엔드 프로젝트 구조 설정
- [ ] Task 2: 할 일 CRUD API 엔드포인트 (테스트 먼저!)
- [ ] Task 3: 프론트엔드 프로젝트 구조 설정
- [P] Task 4: 할 일 목록 UI
- [P] Task 5: 할 일 추가 UI
- [ ] Task 6: 할 일 수정/삭제 UI
- [ ] Task 7: 통합 테스트
```

#### 6. 구현

```
/speckit.implement
```

AI가 태스크를 하나씩 실행합니다. 각 태스크 완료 후 PowerShell에서 Git 커밋:

```powershell
git add -A
git commit -m "implement: Task 1 - backend project setup"
```

### PowerShell에서 진행 상황 확인

```powershell
# 생성된 모든 명세 파일 확인
Get-ChildItem specs -Recurse -Filter "*.md" | Select-Object FullName, Length

# Git 상태 확인
git status

# 최근 커밋 이력
git log --oneline -5
```

### 완료!

이제 당신의 할 일 앱이 작동합니다. 모든 결정이 문서로 기록되어 있고, 코드는 명세에서 유도되었습니다.

---

## 8. Extensions & Presets

Spec-Kit은 확장 가능합니다.

### Extensions (확장) — 새로운 명령 추가

```powershell
# 확장 검색
specify extension search

# 확장 추가
specify extension add <extension-name>

# 확장 제거
specify extension remove <extension-name>
```

확장은 새로운 `/speckit.*` 명령어를 추가합니다.

### Presets (프리셋) — 템플릿 커스터마이징

```powershell
# 프리셋 검색
specify preset search

# 프리셋 추가
specify preset add <preset-name>
```

프리셋은 기존 템플릿의 형식이나 용어를 변경합니다.

### 우선순위

| 수준 | 설명 |
|:---:|------|
| **1 (최우선)** | 프로젝트 로컬 오버라이드 (`.specify\templates\overrides\`) |
| **2** | Preset |
| **3** | Extension |

---

## 9. PowerShell 초보자를 위한 핵심 팁

### Tip 1: spec.md에 기술을 적지 마세요

```
나쁨: "React로 로그인 페이지를 만들어"
좋음: "사용자가 이메일로 로그인할 수 있어야 한다"
```

spec.md는 **무엇**, plan.md는 **어떻게**입니다.

### Tip 2: 헌법을 가볍게 시작하세요

처음부터 9개 원칙을 다 정할 필요 없습니다. 3~4개로 시작해서 필요시 추가하세요.

### Tip 3: Clarify 단계를 건너뛰지 마세요

`/speckit.clarify`가 찾아내는 모호한 부분이 실제 개발 중 버그가 되는 부분입니다.

### Tip 4: 작은 기능부터 시작하세요

첫 프로젝트는 "할 일 1개 추가/삭제"처럼 아주 작은 기능으로 시작하세요. Spec-Kit의 가치를 빠르게 느낄 수 있습니다.

### Tip 5: 명세는 살아있는 문서입니다

기능이 바뀌면 명세도 바꿉니다. 코드를 먼저 바꾸지 말고, 명세를 먼저 수정한 후 AI가 코드를 재생성하게 하세요.

### Tip 6: 병렬 태스크 활용

`[P]` 마커가 붙은 태스크는 동시에 진행할 수 있습니다. 여러 AI 에이전트를 쓰면 더 빠릅니다.

### Tip 7: PowerShell Execution Policy 확인

`.ps1` 스크립트를 실행할 때 권한 문제가 발생하면:

```powershell
# 현재 Execution Policy 확인
Get-ExecutionPolicy

# CurrentUser 범위로 설정 (권장)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Tip 8: PowerShell에서 파일 인코딩 주의

Windows 기본 인코딩은 UTF-8이 아닐 수 있습니다. Spec-Kit 파일들은 UTF-8로 저장됩니다:

```powershell
# 파일 인코딩 확인
Get-Content .specify\memory\constitution.md -Encoding UTF8

# 파일 저장 시 UTF-8 명시
Get-Content spec.md | Out-File -FilePath spec.md -Encoding UTF8
```

### Tip 9: VS Code 터미널에서 사용하기

PowerShell에서 Claude Code를 사용할 때 VS Code 터미널을 추천합니다:

```powershell
# VS Code에서 현재 폴더 열기
code .

# VS Code 터미널에서 Claude Code 실행
claude
```

### Tip 10: Windows 파일 경로 길이 제한

Windows는 기본 파일 경로 길이가 260자로 제한됩니다. 긴 경로 문제가 발생하면:

```powershell
# 관리자 PowerShell에서 실행
Set-ItemProperty "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1
```

---

## 10. PowerShell 유용한 명령어 모음

### 프로젝트 관리

```powershell
# 새 Spec-Kit 프로젝트 생성
specify init MyProject --ai claude

# 기존 프로젝트에 Spec-Kit 추가
cd C:\git\my-existing-project
specify init . --ai claude --script ps

# Spec-Kit 버전 확인
specify version

# Spec-Kit 버전 업데이트 확인
specify check
```

### 파일 탐색

```powershell
# 모든 명세 파일 목록
Get-ChildItem -Path specs -Recurse -Include "spec.md","plan.md","tasks.md"

# 헌법 파일 내용 확인
Get-Content .specify\memory\constitution.md

# specs 폴더 트리 구조
tree specs /F

# 가장 최근에 수정된 명세 파일
Get-ChildItem specs -Recurse -Filter "*.md" | Sort-Object LastWriteTime -Descending | Select-Object -First 5 Name, LastWriteTime
```

### Git 연동

```powershell
# 현재 상태 확인
git status

# 변경사항 커밋
git add -A
git commit -m "feat: add login feature spec and plan"

# Git 브랜치 목록
git branch -a

# 새 기능 브랜치 생성 (Spec-Kit이 자동으로 생성)
git checkout -b 002-user-profile
```

### PowerShell 스크립트 실행

```powershell
# 새 기능 생성 스크립트 실행
.\.specify\scripts\create-new-feature.ps1 -Name "user-profile"

# 템플릿 설정 스크립트 실행
.\.specify\scripts\setup-template.ps1
```

---

## 부록: 전체 Slash 명령어 목록

| 명령어 | 설명 | 단계 |
|--------|------|:---:|
| `/speckit.constitution` | 프로젝트 원칙 정의 | 1 |
| `/speckit.specify` | 기능 명세 생성 | 2 |
| `/speckit.clarify` | 명세 모호한 부분 질문 | 2.5 |
| `/speckit.plan` | 구현 계획 수립 | 3 |
| `/speckit.analyze` | 산출물 간 일관성 분석 | 3.5 |
| `/speckit.tasks` | 태스크 분해 | 4 |
| `/speckit.implement` | 태스크 순차 실행 | 5 |
| `/speckit.checklist` | 품질 검증 체크리스트 | 5.5 |
| `/speckit.taskstoissues` | 태스크를 GitHub Issues로 변환 | 4.5 |

---

## 부록: PowerShell별 자주 묻는 질문 (FAQ)

### Q: Spec-Kit은 무료인가요?
A: 네. MIT 라이선스의 오픈소스입니다.

### Q: Windows에서 어떤 AI 코딩 도구와 호환되나요?
A: Claude Code, GitHub Copilot CLI, Gemini CLI, Codex CLI, Cursor, Windsurf, OpenCode 등을 지원합니다.

### Q: PowerShell에서 `.ps1` 파일이 실행되지 않아요.
A: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` 명령어로 실행 권한을 설정하세요.

### Q: 기존 프로젝트(Brownfield)에도 사용할 수 있나요?
A: 네. `specify init .`로 현재 디렉토리에 초기화하면 기존 코드베이스에 Spec-Kit 워크플로우를 적용할 수 있습니다.

### Q: 헌법을 수정해도 되나요?
A: 네. 하지만 헌법 수정 시 `constitution_update_checklist.md`의 검증 절차를 따릅니다.

### Q: spec.md를 여러 개 만들 수 있나요?
A: 네. 기능(feature)별로 spec.md를 만듭니다. 예: `specs\001-login\spec.md`, `specs\002-dashboard\spec.md`

### Q: cmd.exe에서도 사용할 수 있나요?
A: 네. 하지만 `.ps1` 스크립트는 PowerShell에서만 실행됩니다. 가급적 PowerShell을 사용하세요.

### Q: Windows 터미널 vs PowerShell ISE 중 무엇을 써야 하나요?
A: **Windows 터미널(Windows Terminal)**을 권장합니다. PowerShell ISE는 더 이상 actively maintained되지 않습니다.

---

`★ Insight ─────────────────────────────────────`
- Spec-Kit의 진짜 가치는 "문서를 많이 만드는 것"이 아니라, **명세를 통해 AI의 출력 품질을 통제**하는 데 있습니다. 좋은 명세 = 좋은 코드.
- SDD에서 코드는 "부산물(byproduct)"입니다. 진짜 핵심 산출물은 명세서입니다. 이 인식이 바뀌어야 SDD를 제대로 활용할 수 있습니다.
- Spec-Kit은 "폭포수 개발의 재발명"이 아닙니다. 전통적인 폭포수는 명세 → 구현의 단방향이지만, SDD는 명세가 살아있고 진화하며, 코드는 명세에서 재생성됩니다.
`─────────────────────────────────────────────────`
