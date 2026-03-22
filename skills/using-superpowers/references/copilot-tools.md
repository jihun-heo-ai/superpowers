# GitHub Copilot Tool Mapping

Skills use Claude Code tool names. When you encounter these in a skill, use your platform equivalent:

| Skill references | GitHub Copilot equivalent |
|-----------------|--------------------------|
| `Read` (file reading) | `readFile` |
| `Write` (file creation) | `createFile` |
| `Edit` (file editing) | `editFile` |
| `Bash` (run commands) | `runInTerminal` |
| `Grep` (search file content) | `getFileTextSearch` |
| `Glob` (search files by name) | `getFileTextSearch` |
| `TodoWrite` (task tracking) | No equivalent — track tasks manually |
| `Skill` tool (invoke a skill) | Skills load natively — just follow the instructions |
| `Task` tool (dispatch subagent) | No equivalent — GitHub Copilot does not support subagents |

## Asking user questions

GitHub Copilot provides the `askQuestions` tool for requesting structured input from the user.

When a skill instructs you to ask the user a question, present options, or wait for user input — **use the `askQuestions` tool** instead of just outputting text. This ensures the user sees a clear, structured prompt and the agent properly waits for their response.

**Examples:**

| Skill says | Use `askQuestions` with |
|------------|----------------------|
| "Which option?" (after presenting choices) | The full question with numbered options |
| "Which approach?" (after presenting alternatives) | The question with each approach described |
| "Which would you prefer?" (after presenting options) | The question with available choices |
| "Please review it and let me know" | A request to review with clear next-step options |

## No subagent support

GitHub Copilot has no equivalent to Claude Code's `Task` tool. Skills that rely on subagent dispatch (`subagent-driven-development`, `dispatching-parallel-agents`) will fall back to single-session execution via `executing-plans`.
