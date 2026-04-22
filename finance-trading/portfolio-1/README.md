# Portfolio

> > 이 문서는 2026년 3월 13일 기준으로 정리한 포트폴리오 초안입니다.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 포트폴리오

> 이 문서는 2026년 3월 13일 기준으로 정리한 포트폴리오 초안입니다.  
> 스크린샷은 같은 날짜에 실제 실행 또는 공개 배포본에서 직접 캡처했습니다.

## 한 줄 소개

42서울 정규과정 수료 이후, 프론트엔드 단독 배포 프로젝트를 직접 완성하고, 현재 워크스페이스에서는 프론트엔드부터 백엔드, 모바일, 보안, 네트워크, CS 기초까지 학습 순서에 맞춘 대규모 프로젝트 세트를 순차적으로 끝까지 구현하고 검증해 온 개발자입니다.

핵심 강점은 세 가지입니다.

- 화면을 만드는 프론트엔드 감각과 시스템 단위의 구조 이해를 함께 가져가려는 태도
- 프로젝트를 `문제 정의 -> 구현 -> 검증 -> 문서화` 흐름으로 끝까지 정리하는 실행력
- "동작했다" 수준이 아니라 다시 실행 가능한 상태로 남기는 재현성 중심 습관

## 대표 프로젝트 1. mini-vrew

- 형태: 프론트엔드 단독 개발 및 배포
- 링크:
  - GitHub: <https://github.com/seungwoo7050/mini-vrew>
  - Deploy: <https://mini-vrew.vercel.app>
- 핵심 설명:
  - 브라우저에서 동작하는 AI 비디오 편집기 성격의 웹앱
  - FFmpeg WASM, WebGL 2.0, Web Audio API, IndexedDB를 조합해 업로드부터 편집, 자막, 필터, 내보내기 흐름을 프론트엔드에서 직접 처리
- 내가 보여 줄 수 있는 역량:
  - React 19, TypeScript, Vite 기반 제품형 UI 구성
  - 비디오 플레이어, 파형 시각화, 트리밍, 자막 편집, 필터, 썸네일, 내보내기까지 이어지는 복합 UI 설계
  - 브라우저 API를 이용한 무거운 클라이언트 작업 분리와 사용자 경험 구성

![mini-vrew 실행 화면](./assets/mini-vrew.png)

## 대표 프로젝트 2. Frontend Portfolio Track

현재 워크스페이스의 [`front-react`](../front-react/README.md)는 웹 기초, React internal, 제품형 UI까지 이어지는 흐름으로 정리되어 있고, 마지막 `frontend-portfolio` 트랙에서 채용용으로 설명 가능한 결과물을 만들었습니다.

### 2-1. Ops Triage Console

- 위치: [`front-react/study/frontend-portfolio/01-ops-triage-console`](../front-react/study/frontend-portfolio/01-ops-triage-console/README.md)
- 문제:
  - 데이터가 많은 운영 화면에서 triage workflow를 어떻게 설계하고 검증할 것인가
- 구현 포인트:
  - dashboard summary, triage queue, saved view, bulk action, optimistic update, rollback, retry
  - Next.js App Router 기반 구조
  - typecheck, Vitest, Playwright를 묶은 검증 루프

![ops triage console 실행 화면](./assets/ops-triage-console.png)

### 2-2. Client Onboarding Portal

- 위치: [`front-react/study/frontend-portfolio/02-client-onboarding-portal`](../front-react/study/frontend-portfolio/02-client-onboarding-portal/README.md)
- 문제:
  - 고객-facing onboarding flow에서 validation, draft restore, route guard, submit retry를 어떻게 하나의 제품 흐름으로 묶을 것인가
- 구현 포인트:
  - sign-in, onboarding wizard, invite flow, review, retry 처리
  - React Hook For

*[truncated — see source for full prompt]*