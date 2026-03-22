# Superpowers

Superpowers는 코딩 에이전트를 위한 완전한 소프트웨어 개발 워크플로우로, 조합 가능한 "스킬(skills)" 세트와 에이전트가 이를 활용하도록 하는 초기 설정으로 구성되어 있습니다.

## 작동 방식

코딩 에이전트를 시작하는 순간부터 작동합니다. 에이전트는 무언가를 만들고 있다는 것을 인식하면, 바로 코드를 작성하려고 하지 *않습니다*. 대신 한 발 물러서서 실제로 무엇을 하려는지 물어봅니다.

대화를 통해 스펙을 이끌어낸 후, 실제로 읽고 소화할 수 있을 만큼 짧은 단위로 보여줍니다.

설계를 승인하면, 에이전트는 열정적이지만 취향이 부족하고, 판단력이 없으며, 프로젝트 맥락이 없고, 테스트를 싫어하는 주니어 엔지니어도 따를 수 있을 만큼 명확한 구현 계획을 작성합니다. 진정한 RED/GREEN TDD, YAGNI(You Aren't Gonna Need It), DRY를 강조합니다.

그 다음, "시작"이라고 말하면 *서브에이전트 기반 개발* 프로세스를 시작하여, 에이전트들이 각 엔지니어링 작업을 수행하고, 그들의 작업을 검사하고 리뷰하며, 계속 진행합니다. Claude가 계획에서 벗어나지 않고 몇 시간 동안 자율적으로 작업하는 것은 드문 일이 아닙니다.

더 많은 내용이 있지만, 이것이 시스템의 핵심입니다. 그리고 스킬이 자동으로 트리거되기 때문에 특별한 것을 할 필요가 없습니다. 당신의 코딩 에이전트가 그냥 Superpowers를 가지게 됩니다.

## 후원

Superpowers가 수익을 올리는 데 도움이 되었다면, [오픈소스 작업 후원](https://github.com/sponsors/obra)을 고려해 주시면 감사하겠습니다.

감사합니다!

\- Jesse

## 설치

**참고:** 설치 방법은 플랫폼마다 다릅니다. Claude Code, Cursor, GitHub Copilot은 내장 플러그인 마켓플레이스를 가지고 있습니다. Codex와 OpenCode는 수동 설정이 필요합니다.

### Claude Code 공식 마켓플레이스

Superpowers는 [공식 Claude 플러그인 마켓플레이스](https://claude.com/plugins/superpowers)에서 이용할 수 있습니다.

Claude 마켓플레이스에서 플러그인을 설치하세요:

```bash
/plugin install superpowers@claude-plugins-official
```

### Claude Code (플러그인 마켓플레이스를 통해)

Claude Code에서 먼저 마켓플레이스를 등록하세요:

```bash
/plugin marketplace add obra/superpowers-marketplace
```

그런 다음 이 마켓플레이스에서 플러그인을 설치하세요:

```bash
/plugin install superpowers@superpowers-marketplace
```

### Cursor (플러그인 마켓플레이스를 통해)

Cursor Agent 채팅에서 마켓플레이스로부터 설치하세요:

```text
/add-plugin superpowers
```

또는 플러그인 마켓플레이스에서 "superpowers"를 검색하세요.

### Codex

Codex에 다음을 입력하세요:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

**상세 문서:** [docs/README.codex.md](docs/README.codex.md)

### OpenCode

OpenCode에 다음을 입력하세요:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

**상세 문서:** [docs/README.opencode.md](docs/README.opencode.md)

### GitHub Copilot / Copilot CLI

```bash
copilot plugin install obra/superpowers
```

업데이트:

```bash
copilot plugin update superpowers
```

**상세 문서:** [docs/README.copilot.md](docs/README.copilot.md)

### Gemini CLI

```bash
gemini extensions install https://github.com/obra/superpowers
```

업데이트:

```bash
gemini extensions update superpowers
```

### 설치 확인

선택한 플랫폼에서 새 세션을 시작하고 스킬을 트리거할 수 있는 요청을 해보세요 (예: "이 기능 설계 도와줘" 또는 "이 이슈 디버깅하자"). 에이전트가 자동으로 관련 superpowers 스킬을 호출해야 합니다.

## 기본 워크플로우

1. **brainstorming (브레인스토밍)** - 코드 작성 전에 활성화됩니다. 질문을 통해 대략적인 아이디어를 다듬고, 대안을 탐색하며, 검증을 위해 설계를 섹션별로 제시합니다. 설계 문서를 저장합니다.

2. **using-git-worktrees (깃 워크트리 사용)** - 설계 승인 후 활성화됩니다. 새 브랜치에 격리된 작업 공간을 만들고, 프로젝트 설정을 실행하며, 깨끗한 테스트 기준선을 확인합니다.

3. **writing-plans (계획 작성)** - 승인된 설계가 있을 때 활성화됩니다. 작업을 작은 단위(각 2-5분)로 분할합니다. 모든 작업에는 정확한 파일 경로, 완전한 코드, 검증 단계가 포함됩니다.

4. **subagent-driven-development (서브에이전트 기반 개발)** 또는 **executing-plans (계획 실행)** - 계획이 있을 때 활성화됩니다. 작업별로 새로운 서브에이전트를 배치하여 2단계 리뷰(스펙 준수, 코드 품질)를 수행하거나, 사람의 체크포인트와 함께 배치로 실행합니다.

5. **test-driven-development (테스트 주도 개발)** - 구현 중에 활성화됩니다. RED-GREEN-REFACTOR를 강제: 실패하는 테스트 작성, 실패 확인, 최소한의 코드 작성, 통과 확인, 커밋. 테스트 전에 작성된 코드는 삭제합니다.

6. **requesting-code-review (코드 리뷰 요청)** - 작업 사이에 활성화됩니다. 계획 대비 리뷰하고, 심각도별로 이슈를 보고합니다. 치명적인 이슈는 진행을 차단합니다.

7. **finishing-a-development-branch (개발 브랜치 마무리)** - 작업이 완료되면 활성화됩니다. 테스트를 검증하고, 옵션(머지/PR/유지/폐기)을 제시하며, 워크트리를 정리합니다.

**에이전트는 모든 작업 전에 관련 스킬을 확인합니다.** 제안이 아닌 필수 워크플로우입니다.

## 구성 요소

### 스킬 라이브러리

**테스팅**
- **test-driven-development** - RED-GREEN-REFACTOR 사이클 (테스팅 안티패턴 참조 포함)

**디버깅**
- **systematic-debugging** - 4단계 근본 원인 프로세스 (근본 원인 추적, 다층 방어, 조건 기반 대기 기법 포함)
- **verification-before-completion** - 실제로 수정되었는지 확인

**협업**
- **brainstorming** - 소크라테스식 설계 정제
- **writing-plans** - 상세한 구현 계획
- **executing-plans** - 체크포인트 포함 배치 실행
- **dispatching-parallel-agents** - 동시 서브에이전트 워크플로우
- **requesting-code-review** - 사전 리뷰 체크리스트
- **receiving-code-review** - 피드백에 대한 대응
- **using-git-worktrees** - 병렬 개발 브랜치
- **finishing-a-development-branch** - 머지/PR 결정 워크플로우
- **subagent-driven-development** - 2단계 리뷰(스펙 준수, 코드 품질)를 통한 빠른 반복

**메타**
- **writing-skills** - 모범 사례에 따른 새 스킬 생성 (테스팅 방법론 포함)
- **using-superpowers** - 스킬 시스템 소개

## 철학

- **테스트 주도 개발** - 항상 테스트를 먼저 작성
- **체계적 > 임시적** - 추측이 아닌 프로세스
- **복잡도 감소** - 단순함이 주요 목표
- **주장보다 증거** - 성공 선언 전에 검증

더 읽기: [Superpowers for Claude Code](https://blog.fsck.com/2025/10/09/superpowers/)

## 기여하기

스킬은 이 저장소에 직접 있습니다. 기여하려면:

1. 저장소를 포크하세요
2. 스킬용 브랜치를 만드세요
3. 새 스킬을 만들고 테스트하려면 `writing-skills` 스킬을 따르세요
4. PR을 제출하세요

완전한 가이드는 `skills/writing-skills/SKILL.md`를 참고하세요.

## 업데이트

플러그인을 업데이트하면 스킬이 자동으로 업데이트됩니다:

```bash
/plugin update superpowers
```

## 라이선스

MIT 라이선스 - 자세한 내용은 LICENSE 파일을 참고하세요

## 커뮤니티

Superpowers는 [Jesse Vincent](https://blog.fsck.com)과 [Prime Radiant](https://primeradiant.com)의 팀이 만들었습니다.

커뮤니티 지원, 질문, Superpowers로 만드는 것을 공유하려면 [Discord](https://discord.gg/Jd8Vphy9jq)에 참여하세요.

## 지원

- **Discord**: [Discord 참여](https://discord.gg/Jd8Vphy9jq)
- **이슈**: https://github.com/obra/superpowers/issues
- **마켓플레이스**: https://github.com/obra/superpowers-marketplace

---

## 스킬별 한글 트리거 가이드

각 스킬은 사용자가 한글로 대화할 때도 자동으로 활성화됩니다. 아래는 각 스킬의 한글 트리거 키워드와 활성화 조건입니다.

### 1. brainstorming (브레인스토밍)
**한글 트리거:** `브레인스토밍`, `아이디어 구상`, `기능 설계`, `기능 만들기`, `새 기능`, `설계 논의`, `요구사항 분석`

**활성화 조건:** 새로운 기능 생성, 컴포넌트 빌드, 기능 추가 또는 동작 수정 등 모든 창작 작업 전에 반드시 사용합니다.

**사용 예시:**
- "새 기능을 만들어보자"
- "이 컴포넌트 설계를 논의하자"
- "요구사항 분석부터 시작하자"

---

### 2. dispatching-parallel-agents (병렬 에이전트 분배)
**한글 트리거:** `병렬 에이전트`, `동시 작업`, `병렬 처리`, `독립 작업 분배`, `동시에 여러 작업`

**활성화 조건:** 공유 상태나 순차적 의존성 없이 작업할 수 있는 2개 이상의 독립적인 작업이 있을 때 사용합니다.

**사용 예시:**
- "이 세 가지 문제를 동시에 해결하자"
- "독립적인 작업을 병렬로 처리하자"

---

### 3. executing-plans (계획 실행)
**한글 트리거:** `계획 실행`, `구현 계획 실행`, `플랜 실행`, `작업 실행`, `구현 시작`

**활성화 조건:** 작성된 구현 계획이 있고, 별도의 세션에서 리뷰 체크포인트와 함께 실행할 때 사용합니다.

**사용 예시:**
- "작성한 계획을 실행하자"
- "구현을 시작하자"

---

### 4. finishing-a-development-branch (개발 브랜치 마무리)
**한글 트리거:** `개발 브랜치 마무리`, `브랜치 완료`, `작업 완료`, `머지`, `PR 생성`, `병합 준비`

**활성화 조건:** 구현이 완료되고 모든 테스트가 통과하여 작업을 통합하는 방법을 결정해야 할 때 사용합니다.

**사용 예시:**
- "작업이 완료됐으니 머지하자"
- "PR을 생성하자"
- "이 브랜치 마무리하자"

---

### 5. receiving-code-review (코드 리뷰 받기)
**한글 트리거:** `코드 리뷰 받기`, `리뷰 피드백 처리`, `리뷰 의견 반영`, `코드 리뷰 대응`

**활성화 조건:** 코드 리뷰 피드백을 받았을 때, 제안을 구현하기 전에 사용합니다. 특히 피드백이 불명확하거나 기술적으로 의문스러울 때 사용합니다.

**사용 예시:**
- "리뷰 피드백이 왔는데 처리하자"
- "코드 리뷰 의견을 반영하자"

---

### 6. requesting-code-review (코드 리뷰 요청)
**한글 트리거:** `코드 리뷰 요청`, `리뷰 요청`, `코드 검토 요청`, `리뷰해줘`, `코드 확인`

**활성화 조건:** 작업 완료, 주요 기능 구현, 또는 머지 전에 작업이 요구사항을 충족하는지 확인할 때 사용합니다.

**사용 예시:**
- "코드 리뷰 요청하자"
- "이 코드 좀 확인해줘"

---

### 7. subagent-driven-development (서브에이전트 기반 개발)
**한글 트리거:** `서브에이전트 개발`, `에이전트 기반 개발`, `하위 에이전트`, `작업 위임`, `에이전트 분배 개발`

**활성화 조건:** 현재 세션에서 독립적인 작업이 포함된 구현 계획을 실행할 때 사용합니다.

**사용 예시:**
- "에이전트에게 작업을 위임하자"
- "서브에이전트로 개발을 진행하자"

---

### 8. systematic-debugging (체계적 디버깅)
**한글 트리거:** `체계적 디버깅`, `버그 수정`, `버그 찾기`, `오류 해결`, `테스트 실패`, `디버깅`, `문제 해결`

**활성화 조건:** 버그, 테스트 실패, 또는 예상치 못한 동작이 발생했을 때, 수정을 제안하기 전에 사용합니다.

**사용 예시:**
- "이 버그 좀 수정하자"
- "테스트가 실패하는데 디버깅하자"
- "이 오류를 해결해줘"

---

### 9. test-driven-development (테스트 주도 개발)
**한글 트리거:** `테스트 주도 개발`, `TDD`, `테스트 먼저`, `테스트 작성`, `기능 구현`, `버그 수정 구현`

**활성화 조건:** 기능이나 버그 수정을 구현할 때, 구현 코드를 작성하기 전에 사용합니다.

**사용 예시:**
- "TDD로 개발하자"
- "테스트부터 먼저 작성하자"
- "이 기능을 구현하자"

---

### 10. using-git-worktrees (깃 워크트리 사용)
**한글 트리거:** `깃 워크트리`, `워크트리 생성`, `작업 공간 분리`, `브랜치 격리`, `독립 작업 환경`

**활성화 조건:** 현재 작업 공간에서 격리가 필요한 기능 작업을 시작하거나, 구현 계획을 실행하기 전에 사용합니다.

**사용 예시:**
- "새 워크트리를 만들자"
- "작업 공간을 분리하자"

---

### 11. using-superpowers (슈퍼파워 사용)
**한글 트리거:** `슈퍼파워 사용`, `스킬 사용법`, `스킬 시스템`, `대화 시작`, `스킬 활성화`

**활성화 조건:** 모든 대화 시작 시 사용됩니다. 명확화 질문을 포함하여 모든 응답 전에 스킬 도구 호출을 요구합니다.

**사용 예시:**
- "스킬 시스템에 대해 알려줘"
- "어떤 스킬을 사용할 수 있어?"

---

### 12. verification-before-completion (완료 전 검증)
**한글 트리거:** `완료 전 검증`, `작업 검증`, `완료 확인`, `테스트 확인`, `커밋 전 확인`, `결과 검증`

**활성화 조건:** 작업이 완료되었다고 주장하거나, 수정되었다거나, 통과했다고 주장하기 전에, 커밋이나 PR 생성 전에 사용합니다.

**사용 예시:**
- "커밋하기 전에 확인하자"
- "결과를 검증하자"
- "완료된 건지 확인해줘"

---

### 13. writing-plans (계획 작성)
**한글 트리거:** `계획 작성`, `구현 계획`, `플랜 작성`, `작업 계획`, `구현 설계`, `단계별 계획`

**활성화 조건:** 다단계 작업에 대한 스펙이나 요구사항이 있고, 코드를 작성하기 전에 사용합니다.

**사용 예시:**
- "구현 계획을 세우자"
- "단계별 계획을 작성하자"

---

### 14. writing-skills (스킬 작성)
**한글 트리거:** `스킬 작성`, `스킬 만들기`, `스킬 편집`, `새 스킬 생성`, `스킬 검증`

**활성화 조건:** 새 스킬을 만들거나, 기존 스킬을 편집하거나, 배포 전에 스킬이 제대로 작동하는지 확인할 때 사용합니다.

**사용 예시:**
- "새 스킬을 만들어보자"
- "이 스킬을 편집하자"
