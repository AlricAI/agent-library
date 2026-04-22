# Ep05 Agents

> ## 메타 정보

| 항목 | 내용 |
|------|------|
| 영상 길이 | 8-10분 |
| 대상 | Claude Code 사용자 |
| 핵심 메시지 | Agent는 독립 실행되는 전문화된 AI 프로세스다 |

---

## 인트로 (30초)

**[화면: 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# EP05: Agents AI 서브프로세스

## 메타 정보

| 항목 | 내용 |
|------|------|
| 영상 길이 | 8-10분 |
| 대상 | Claude Code 사용자 |
| 핵심 메시지 | Agent는 독립 실행되는 전문화된 AI 프로세스다 |

---

## 인트로 (30초)

**[화면: 여러 에이전트가 병렬로 작업하는 다이어그램]**

> .claude/ 시리즈 다섯 번째 영상입니다.
> 오늘은 **Agents**를 다룹니다.
>
> Command는 대화 안에서 실행됩니다.
> Agent는 다릅니다. **완전히 새로운 프로세스**로 독립 실행됩니다.
>
> 복잡한 작업을 쪼개서 전문화된 에이전트에게 맡기는 거죠.

---

## 본론 1: Agent란? (1분 30초)

**[화면: Command vs Agent 비교]**

| | Command | Agent |
|--|---------|-------|
| 실행 | 현재 대화에서 | 새 프로세스로 spawn |
| 컨텍스트 | 대화 맥락 유지 | 독립된 컨텍스트 |
| 결과 | 대화에 출력 | 호출자에게 반환 |

> Command를 실행하면 지금 대화에서 바로 동작합니다.
> Agent는 **새로운 프로세스를 띄워서** 독립적으로 작업합니다.

**[화면: spawn 흐름도]**

```
/gsd:plan-phase 실행
    ↓
gsd-planner 에이전트 spawn
    ↓
(독립된 컨텍스트에서 계획 수립)
    ↓
PLAN.md 생성 후 반환
```

> 에이전트가 끝나면 결과를 **파일로** 남깁니다.
> `PLAN.md` 같은 산출물이죠.

### Agent vs Hook

| | Agent | Hook |
|--|-------|------|
| 실행 환경 | AI 모델 | Node.js |
| 지능 | 판단하며 실행 | 정해진 로직만 |
| 속도 | 느림 | 빠름 |
| 비용 | API 토큰 소비 | 무료 |

> Hook은 Node.js 스크립트입니다. 빠르지만 단순한 작업만 가능합니다.
> Agent는 AI가 판단하며 실행합니다. 느리지만 복잡한 작업이 가능합니다.

---

## 본론 2: Agent 파일 구조 (1분 30초)

**[화면: Markdown 파일 예시]**

```markdown
---
name: gsd-planner
description: Phase를 실행 가능한 Plan으로 분해
tools: Read, Write, Bash, Glob, Grep
spawned_by:
  - /gsd:plan-phase
skills_integration:
  - superpowers:brainstorming
---

<role>
당신은 계획 수립 전문가입니다.
Phase 목표를 분석하고, 실행 가능한 태스크로 분해합니다.
</role>

<execution_flow>
## Step 1: 목표 파악
## Step 2: 태스크 분해
## Step 3: 의존성 분석
## Step 4: PLAN.md 생성
</execution_flow>
```

### frontmatter 필드

| 필드 | 역할 |
|------|------|
| `name` | 에이전트 식별자 |
| `description` | Task 도구에 표시될 설명 |
| `tools` | 사용 가능한 도구 |
| `spawned_by` | 이 에이전트를 spawn하는 명령 |
| `skills_integration` | 참조할 스킬 목록 |

> `tools`가 중요합니다.
> 검증용 에이전트는 읽기만 필요하니까 `Read, Grep, Glob`만.
> 실행용 에이전트는 쓰기도 필요하니까 `Read, Write, Edit, Bash`까지.

---

## 본론 3: GSD 에이전트 시스템 (2분)

**[화면: 에이전트 관계도]**

> GSD 프레임워크는 **11개 전문 에이전트**로 구성됩니다.

### 핵심 3종

**[화면: 3개 에이전트 아이콘]**

#### 1. gsd-planner (계획)

```
Phase "사용자 인증 구현"
    ↓

*[truncated — see source for full prompt]*