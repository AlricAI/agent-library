# Ep06 Hooks

> ## 메타 정보

| 항목 | 내용 |
|------|------|
| 영상 길이 | 7-9분 |
| 대상 | Claude Code 사용자 |
| 핵심 메시지 | Hook은 이벤트에 반응하는 Node.js 스크립트다 |

---

## 인트로 (30초)

**[화면: 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# EP06: Hooks 이벤트 스크립트

## 메타 정보

| 항목 | 내용 |
|------|------|
| 영상 길이 | 7-9분 |
| 대상 | Claude Code 사용자 |
| 핵심 메시지 | Hook은 이벤트에 반응하는 Node.js 스크립트다 |

---

## 인트로 (30초)

**[화면: 세션 시작 시 스크립트 실행 장면]**

> .claude/ 시리즈 여섯 번째 영상입니다.
> 오늘은 **Hooks**를 다룹니다.
>
> 세션이 시작될 때 자동으로 뭔가 실행하고 싶었던 적 있으시죠?
> "업데이트 있는지 확인", "환경 설정 체크"...
>
> Hook으로 가능합니다. **Node.js 스크립트**를 이벤트에 연결하는 거죠.

---

## 본론 1: Hook vs Agent (1분)

**[화면: 비교 테이블]**

| | Hook | Agent |
|--|------|-------|
| 실행 환경 | Node.js | AI 모델 |
| 지능 | 정해진 로직 | 판단하며 실행 |
| 속도 | 빠름 | 느림 |
| 비용 | 무료 | API 토큰 |

> 핵심 원칙: **"단순한 건 Hook, 판단이 필요한 건 Agent"**
>
> 버전 체크? Node.js로 충분합니다. Hook으로.
> 코드 분석 후 계획 수립? AI가 필요합니다. Agent로.

---

## 본론 2: Hook 등록하기 (1분 30초)

**[화면: settings.json 예시]**

```json
{
  "hooks": {
    "SessionStart": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "node .claude/hooks/check-update.js"
          }
        ]
      }
    ]
  }
}
```

> `settings.json`에서 이벤트별로 등록합니다.

### 지원 이벤트

| 이벤트 | 발생 시점 |
|--------|-----------|
| `SessionStart` | 세션 시작 |

> 현재는 `SessionStart`만 지원됩니다.
> 세션 시작할 때 실행할 스크립트를 등록하는 거죠.

### statusLine (특수 훅)

```json
{
  "statusLine": {
    "type": "command",
    "command": "node .claude/hooks/statusline.js"
  }
}
```

> 상태줄은 별도로 등록합니다.
> 이 스크립트는 **주기적으로** 실행되어 상태줄을 업데이트합니다.

---

## 본론 3: 업데이트 체크 Hook 만들기 (2분)

**[화면: 코드 작성 장면]**

> 세션 시작 시 업데이트를 체크하는 훅을 만들어볼게요.

### 목표

```
세션 시작
    ↓
현재 버전 vs 최신 버전 비교
    ↓
업데이트 있으면 알림
```

### 핵심 코드

```javascript
#!/usr/bin/env node

const fs = require('fs');
const path = require('path');
const os = require('os');
const { execSync, spawn } = require('child_process');

// 캐시 설정 (24시간마다 한 번만 체크)
const cacheDir = path.join(os.homedir(), '.claude', 'cache');
const cacheFile = path.join(cacheDir, 'update-check.json');
const CACHE_TTL = 24 * 60 * 60; // 24시간 (초)

// 캐시 유효성 확인
function isCacheValid() {
  if (!fs.existsSync(cacheFile)) return false;
  const cache = JSON.parse(fs.readFileSync(cacheFile, 'utf8'));
 

*[truncated — see source for full prompt]*