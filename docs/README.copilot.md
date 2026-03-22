# Superpowers for GitHub Copilot

Guide for using Superpowers with GitHub Copilot (VS Code) and GitHub Copilot CLI.

## Quick Install

### GitHub Copilot CLI

```bash
copilot plugin install obra/superpowers
```

### VS Code (GitHub Copilot Agent Mode)

In VS Code with Copilot agent mode, install the plugin:

```
copilot plugin install obra/superpowers
```

Or search for "superpowers" in the Copilot plugin marketplace.

## Manual Installation

### Prerequisites

- [GitHub Copilot](https://github.com/features/copilot) subscription
- Git
- One of the following:
  - VS Code with GitHub Copilot extension
  - GitHub Copilot CLI

### Method 1: Plugin Install (Recommended)

Install directly from the GitHub repository:

```bash
copilot plugin install obra/superpowers
```

Verify installation:

```bash
copilot plugin list
```

You should see `superpowers` in the list of installed plugins.

### Method 2: Local Install (For Development)

1. Clone the repo:
   ```bash
   git clone https://github.com/obra/superpowers.git ~/.copilot/superpowers
   ```

2. Install from the local path:
   ```bash
   copilot plugin install ~/.copilot/superpowers
   ```

### Method 3: Repository-Level Skills

To add superpowers skills directly to a specific repository:

1. Copy the skills directory into your project:
   ```bash
   cp -r path/to/superpowers/skills .github/skills/superpowers
   ```

2. Copilot will automatically discover skills in `.github/skills/` when working in the repository.

**Note:** This method makes skills available only within that repository. Use the plugin install method for system-wide availability.

## How It Works

GitHub Copilot discovers skills and plugins through:

1. **Plugin system** — Installed plugins are registered globally and available across all projects.
2. **Repository skills** — Skills in `.github/skills/` are discovered per-repository.
3. **Custom instructions** — `.github/copilot-instructions.md` provides always-on guidance.

Superpowers uses the plugin system to register all available skills. When Copilot encounters a task matching a skill's description, it loads and applies that skill automatically.

## Usage

Skills are discovered automatically after plugin installation. Copilot activates them when:

- You mention a skill by name (e.g., "use brainstorming")
- The task matches a skill's description
- The `using-superpowers` skill directs Copilot to use one

### Example Prompts

- "Help me plan this feature" → triggers **brainstorming** and **writing-plans**
- "Let's debug this issue" → triggers **systematic-debugging**
- "Write tests for this module" → triggers **test-driven-development**
- "Review this code" → triggers **requesting-code-review**

### Personal Skills

Create your own skills alongside superpowers:

```bash
mkdir -p ~/.copilot/skills/my-skill
```

Create `~/.copilot/skills/my-skill/SKILL.md`:

```markdown
---
name: my-skill
description: Use when [condition] - [what it does]
---

# My Skill

[Your skill content here]
```

The `description` field is how Copilot decides when to activate a skill automatically — write it as a clear trigger condition.

## Updating

```bash
copilot plugin update superpowers
```

## Uninstalling

```bash
copilot plugin remove superpowers
```

## Troubleshooting

### Plugin not loading

1. Check installed plugins: `copilot plugin list`
2. Reinstall: `copilot plugin remove superpowers && copilot plugin install obra/superpowers`
3. Restart VS Code or the Copilot CLI session

### Skills not activating

1. Verify the plugin is installed: `copilot plugin list`
2. Try mentioning a skill by name: "use brainstorming to design this feature"
3. Check that your Copilot subscription supports agent mode

### VS Code specific

1. Ensure you have the latest GitHub Copilot extension
2. Enable agent mode in VS Code settings if not already enabled
3. Use the Copilot chat panel (not inline completions) for skill-based workflows

## Getting Help

- Report issues: https://github.com/obra/superpowers/issues
- Main documentation: https://github.com/obra/superpowers
- Discord: https://discord.gg/Jd8Vphy9jq

---

# Superpowers for GitHub Copilot (한국어)

GitHub Copilot (VS Code) 및 GitHub Copilot CLI에서 Superpowers를 사용하기 위한 가이드입니다.

## 빠른 설치

### GitHub Copilot CLI

```bash
copilot plugin install obra/superpowers
```

### VS Code (GitHub Copilot Agent 모드)

VS Code에서 Copilot agent 모드로 플러그인을 설치하세요:

```
copilot plugin install obra/superpowers
```

또는 Copilot 플러그인 마켓플레이스에서 "superpowers"를 검색하세요.

## 수동 설치

### 사전 요구 사항

- [GitHub Copilot](https://github.com/features/copilot) 구독
- Git
- 다음 중 하나:
  - GitHub Copilot 확장이 설치된 VS Code
  - GitHub Copilot CLI

### 방법 1: 플러그인 설치 (권장)

GitHub 저장소에서 직접 설치하세요:

```bash
copilot plugin install obra/superpowers
```

설치 확인:

```bash
copilot plugin list
```

설치된 플러그인 목록에 `superpowers`가 표시되어야 합니다.

### 방법 2: 로컬 설치 (개발용)

1. 저장소를 클론하세요:
   ```bash
   git clone https://github.com/obra/superpowers.git ~/.copilot/superpowers
   ```

2. 로컬 경로에서 설치하세요:
   ```bash
   copilot plugin install ~/.copilot/superpowers
   ```

### 방법 3: 저장소 수준 스킬

특정 저장소에 superpowers 스킬을 직접 추가하려면:

1. 프로젝트에 스킬 디렉토리를 복사하세요:
   ```bash
   cp -r path/to/superpowers/skills .github/skills/superpowers
   ```

2. Copilot이 저장소에서 작업할 때 `.github/skills/` 디렉토리의 스킬을 자동으로 발견합니다.

**참고:** 이 방법은 해당 저장소 내에서만 스킬을 사용할 수 있습니다. 시스템 전체에서 사용하려면 플러그인 설치 방법을 사용하세요.

## 작동 방식

GitHub Copilot은 다음을 통해 스킬과 플러그인을 발견합니다:

1. **플러그인 시스템** — 설치된 플러그인은 전역으로 등록되어 모든 프로젝트에서 사용 가능합니다.
2. **저장소 스킬** — `.github/skills/` 디렉토리의 스킬은 저장소별로 발견됩니다.
3. **커스텀 지시사항** — `.github/copilot-instructions.md`는 항상 적용되는 가이드를 제공합니다.

Superpowers는 플러그인 시스템을 통해 모든 스킬을 등록합니다. Copilot이 스킬의 설명과 일치하는 작업을 만나면, 해당 스킬을 자동으로 로드하고 적용합니다.

## 사용법

플러그인 설치 후 스킬은 자동으로 발견됩니다. 다음과 같은 경우 Copilot이 스킬을 활성화합니다:

- 스킬 이름을 직접 언급할 때 (예: "brainstorming 사용해줘")
- 작업이 스킬의 설명과 일치할 때
- `using-superpowers` 스킬이 Copilot에게 스킬 사용을 지시할 때

### 예시 프롬프트

- "이 기능 설계를 도와줘" → **brainstorming** 및 **writing-plans** 트리거
- "이 이슈를 디버깅하자" → **systematic-debugging** 트리거
- "이 모듈의 테스트를 작성하자" → **test-driven-development** 트리거
- "이 코드를 리뷰해줘" → **requesting-code-review** 트리거

### 개인 스킬 만들기

Superpowers와 함께 자신만의 스킬을 만들 수 있습니다:

```bash
mkdir -p ~/.copilot/skills/my-skill
```

`~/.copilot/skills/my-skill/SKILL.md` 파일을 생성하세요:

```markdown
---
name: my-skill
description: Use when [condition] - [what it does]
---

# My Skill

[스킬 내용을 여기에 작성하세요]
```

`description` 필드는 Copilot이 스킬을 자동으로 활성화할 시점을 결정하는 기준입니다 — 명확한 트리거 조건으로 작성하세요.

## 업데이트

```bash
copilot plugin update superpowers
```

## 삭제

```bash
copilot plugin remove superpowers
```

## 문제 해결

### 플러그인이 로드되지 않을 때

1. 설치된 플러그인 확인: `copilot plugin list`
2. 재설치: `copilot plugin remove superpowers && copilot plugin install obra/superpowers`
3. VS Code 또는 Copilot CLI 세션 재시작

### 스킬이 활성화되지 않을 때

1. 플러그인이 설치되어 있는지 확인: `copilot plugin list`
2. 스킬 이름을 직접 사용해보세요: "brainstorming을 사용해서 이 기능을 설계하자"
3. Copilot 구독이 agent 모드를 지원하는지 확인

### VS Code 관련

1. 최신 GitHub Copilot 확장이 설치되어 있는지 확인
2. VS Code 설정에서 agent 모드가 활성화되어 있는지 확인
3. 스킬 기반 워크플로우에는 Copilot 채팅 패널을 사용하세요 (인라인 완성이 아님)

## 도움 받기

- 이슈 보고: https://github.com/obra/superpowers/issues
- 메인 문서: https://github.com/obra/superpowers
- Discord: https://discord.gg/Jd8Vphy9jq
