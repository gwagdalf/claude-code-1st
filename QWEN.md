# QWEN.md - Claude Code 학습 저장소

## 프로젝트 개요

이 저장소는 "[2시간 안에 Claude Code 마스터하기](https://www.youtube.com/watch?v=vxEvo2BLM6A)" 튜토리얼을 따라가며 Claude Code를 탐색하기 위해 만들어졌습니다. 특히 Spec-Driven Development(SDD) 방법론에 중점을 두고 Claude Code 기능과 workflow를 실험해볼 수 있는 실습 환경입니다.

## 저장소 구조

```
claude-code-1st/
├── .gitignore
├── CLAUDE.md                 # Claude Code 설정 및 안내
├── README.md                 # 기본 프로젝트 식별 정보
├── First/
│   └── README.md             # 튜토리얼 참고자료
├── sdd/                      # Spec-Driven Development 리소스
│   ├── sdd-examples.md       # SDD GitHub 저장소 예제
│   ├── spec-kit-examples.md  # spec-kit 예제
│   ├── spec-kit-guide-powershell.md  # PowerShell 특정 가이드
│   ├── spec-kit-guide.md     # 주요 spec-kit 가이드
│   └── qwen/                 # Qwen 특정 가이드
│       ├── constitution-workflow.md
│       ├── sdd-examples-qwen.md
│       ├── spec-kit-examples-qwen.md
│       └── spec-kit-guide-qwen.md
└── .qwen/                    # Qwen Code 설정 디렉토리
```

## 주요 기능 및 설정

### Claude Code 통합
- `.qwen/settings.json` 파일은 알리바바 클라우드 MaaS와 같은 대체 모델 제공업체를 설정하며 두 가지 모델을 포함:
  - **qwen3-coder-plus** — 주 모델로, 코드 생성, 리팩토링, 디버깅에 최적화됨 (temperature 0.1, max_tokens 8192, thinking mode 활성화)
  - **qwen-max** — 일반 대화를 위한 보조 모델

### API 설정
- API 키는 `QWEN_API_KEY` 환경 변수에서 읽어옴 (.qwen/.env 파일에 설정)

### 보안 설정
- `rm -rf` 및 `del /F /Q` 쉘 명령어는 차단됨
- 미리 승인된 명령어: `git`, `npm`, `python`, `tsc`, `eslint`, `prettier`

### 언어 설정
- 모든 응답과 상호작용은 한국어(Korean)로 진행되어야 함
- 이 설정은 프로젝트 전체에서 일관된 언어 사용을 보장함

### 추가 기능
- `src/`, `lib/`, `tests/`, `docs/` 디렉토리가 존재할 경우 자동으로 context 로드
- Git 공동 저자 활성화 (`gitCoAuthor: true`)
- 체크포인팅 활성화

## Spec-Driven Development(SDD) 중점

이 저장소에는 다음을 포함한 SDD 방법론 관련 포괄적인 문서와 예제가 포함되어 있습니다:

- GitHub의 spec-kit 가이드
- SDD 구현 예제
- 사양 주도 workflow의 모범 사례
- AI 코딩 어시스턴트와의 통합

## 개발 규칙

저장소 구조와 설정에 기반하여 이 프로젝트는 다음과 같은 SDD 원칙을 따릅니다:
1. 코드 작성 전에 사양(specifications)을 작성
2. 명확한 문서화가 구현에 선행
3. AI 지원 개발 workflow를 강조
4. 구조화된 접근 방식을 우선

## 빌드 및 실행

이 저장소는 주로 Claude Code 기능을 위한 학습 및 실험 공간으로 사용됩니다. 전통적인 빌드 단계는 없으며, SDD 개념을 탐색하려면 다음을 수행하세요:

1. `sdd/` 디렉토리의 문서 검토
2. spec-kit 예제 실험
3. 가이드에 설명된 workflow 구현 시도

## 사용법

이 저장소는 다음을 위한 참조 및 실험 공간으로 설계되었습니다:
- Claude Code workflow
- Spec-Driven Development 관행
- AI 지원 코딩 기법
- 사양 우선 개발 접근법

시작하려면 SDD 개념을 이해하기 위해 `sdd/` 디렉토리의 자료부터 시작한 후, 설정된 구성으로 Claude Code를 실험해보세요.