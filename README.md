# 🚀 Claude Full-Stack Ultimate Setup 사용 설명서

이 디렉토리는 현존하는 최고의 오픈소스 Claude 커스텀 워크플로우 4종(`superpowers`, `oh-my-agent`, `advanced-harness`, `kimoring-ai-skills`)의 핵심 기능만을 추출하여 결합한 **궁극의 풀스택 AI 페어 프로그래밍 작업 공간**입니다.

이 폴더 안에서 Claude(Cursor, Claude Code, 혹은 웹 UI 등)를 실행하면, 자동으로 이 시스템을 인식하여 프로 수준의 엔지니어링 프로세스를 준수합니다.

---

## 🎯 케이스별 사용 가이드

### 케이스 1: 새로운 기능(Feature)을 개발할 때 (정석 워크플로우)

새로운 기능을 무턱대고 "만들어줘"라고 하지 마세요. 다음 단계에 따라 Claude에게 지시하면 완벽한 아키텍처와 코드를 얻을 수 있습니다.

1. **기획 및 요구사항 분석 (초기 설계)**
   > 🗣️ *"새로운 유저 프로필 이미지 업로드 기능을 만들거야. `/agent pm-planner` (또는 `/skill brainstorming`)를 호출해서 데이터베이스 스키마와 API 명세부터 작성해줘."*
   Claude가 무작정 코드를 짜는 대신, 필요한 제약 조건, 에지 케이스 등을 질문하며 마크다운 파일로 완벽한 기획서를 먼저 만들어줍니다.

2. **계획(Plan) 분할**
   > 🗣️ *"기획이 끝났으니 `/skill writing-plans`를 호출해서 프론트엔드와 백엔드 작업으로 단위 태스크를 분할해줘."*

3. **기능 구현 (TDD 방식)**
   > 🗣️ *"이제 작업 목록을 바탕으로 `/skill subagent-driven-development` 프로세스를 시작해줘. 프론트엔드는 `@frontend-impl`, 백엔드는 `@backend-impl` 에이전트가 맡도록 해."*
   이 단계를 실행하면 Claude가 스스로 테스트 코드를 먼저 작성하고(`test-driven-development` 스킬 발동), 실제 코드를 작성한 뒤 통과 여부를 검증합니다.

---

### 케이스 2: 완성된 코드의 품질 검수만 받고 싶을 때 (QA 단독 호출)

전체 워크플로우를 타지 않고, 이미 작성된 코드의 성능, 보안, 접근성 검수만 따로 진행할 수 있습니다.

> 🗣️ *"방금 작성한 `UserContoller`와 `ProfileComponent` 파일에 대해 `/agent qa-reviewer`를 호출해줘."*

* **효과**: Claude가 역할을 QA 시니어 리뷰어로 전환하여 OWASP Top 10 시큐어 코딩 기준, 웹 접근성(WCAG), N+1 쿼리 등 렌더링 최적화 관점에서 코드를 뜯어보고 리포트를 작성합니다.

---

### 케이스 3: 버그나 에러가 발생해서 디버깅해야 할 때

에러 로그를 던져주고 "고쳐줘"라고 하면 흔히 땜질식 처방을 합니다. 다음과 같이 지시하세요.

> 🗣️ *"서버에서 `TypeError: undefined is not an object` 에러가 발생했어. `/agent debug-investigator`를 호출해서 분석해줘."*

* **효과**: 에이전트가 에러의 **근본 원인(Root Cause)**을 분석하고, 수정 코드를 제공할 뿐만 아니라, 이후 같은 에러가 나지 않도록 **회귀 테스트(Regression Test) 코드 작성까지 강제**(`systematic-debugging` 스킬 자동 발동)합니다.

---

### 케이스 4: 우리 프로젝트의 스타일 가이드를 강제하고 싶을 때

코드를 일관성 있게 작성하도록 사전에 저장해둔 코딩 컨벤션 스킬을 함께 주입할 수 있습니다.

> 🗣️ *"로그인 페이지 UI를 작성해줘. 작업 시 반드시 `/skill frontend-guidelines`를 참고해서 shadcn/ui와 Tailwind 방식으로 작성해."*

---

## ⚙️ 백그라운드 자동화 작동 원리 (세션 관리)

이 작업 공간 안에는 `kimoring-ai-skills`에서 차용한 **자동화 훅(Hooks)**이 설정되어 있습니다 (`settings.json`).

* **작업을 시작할 때**: 이전에 중단되었던 Git 변경 사항들을 Claude가 자동으로 읽어들여 컨텍스트를 복구합니다.
* **작업을 종료할 때**: 개발 중간 상태가 유실되지 않도록 Claude가 `.claude/hooks/commit-session.sh`를 알아서 호출해 작업 기록을 백업합니다.

**🎉 당신은 이제 그저 Claude를 부르고 지시만 내리면 됩니다!**
