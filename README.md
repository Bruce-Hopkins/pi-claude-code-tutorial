# How to Setup Pi like Claude Code

## Installation

First make sure Pi is installed on the machine. [Install pi through the official page.](https://pi.dev/docs/latest/quickstart)

Then, you can install each of the Pi packages.

### MCP adapter

[Add MCP capabilities.](https://pi.dev/packages/pi-mcp-adapter)

```bash
pi install npm:pi-mcp-adapter
```

### Sub agents

[Add sub agents of different kinds.](https://pi.dev/packages/pi-subagents?name=agents) Read the documentation to find out which sub agents are allowed.

You can also [make custom subagents](https://pi.dev/packages/pi-subagents?name=agents).

```bash
pi install npm:pi-subagents
```

### Web Access

[Web access and video processing.](https://pi.dev/packages/pi-web-access)

```bash
pi install npm:pi-web-access
```

### Asking user questions

[Asking the user questions before assuming.](https://pi.dev/packages/@juicesharp/rpiv-ask-user-question)

```bash
pi install npm:@juicesharp/rpiv-ask-user-question
```

### TODO

[TODO list to keep track of the progress the agent is making.](https://pi.dev/packages/@juicesharp/rpiv-todo?name=todo)

```bash
pi install npm:@juicesharp/rpiv-todo
```

### Plan mode

[You can install the plan mode most similar to Claude Code's](https://pi.dev/packages/@narumitw/pi-plan-mode?name=plan)

```bash
pi install npm:@narumitw/pi-plan-mode
```

[Or you can install a web browser based package.](https://pi.dev/packages/@plannotator/pi-extension)

```bash
pi install npm:@plannotator/pi-extension
```

## System prompts

I created a [general system prompt that is useful as a starting point.](./APPEND_SYSTEM.md)

```
# Rules

When referencing files in your response, make sure to include the relevant start line and always follow the below rules:

- NEVER revert existing changes you did not make unless explicitly requested, since these changes were made by the user.
- Offer logical next steps (tests, commits, build) briefly; add verify steps if you couldn't do something.
- Do what was asked — no less, no more, and nothing different. Goals the user states explicitly count as part of the ask, even when they pull in files beyond the change you had in mind. Leave out anything the ask does not call for.
- When you have evidence the user is wrong, say so and show the evidence. Defer once they have decided.
- Use specialized tools instead of bash commands when possible, as this provides a better user experience.
- NEVER use bash echo or other command-line tools to communicate thoughts, explanations, or instructions to the user. Output all communication directly in your response text instead.
- Let test coverage scale with risk and blast radius: keep it focused for narrow changes, and broaden it when the implementation touches shared behavior, cross-module contracts, or user-facing workflows.
- Keep every explicit requirement of the request in view until it is completed, superseded by the user, or genuinely blocked. If something is blocked, say so plainly rather than quietly dropping it.

```

The system prompt took inspiration from various open-source system prompts. The system prompt was designed to be short, and generally useful for any coding situation. To make a more specific and robust system prompt, here are the links to the open-source prompts:

### 1. OpenAI Codex CLI

- JSON, containing more recent model prompts: https://github.com/openai/codex/blob/main/codex-rs/models-manager/models.json
- gpt-5.2-codex: https://github.com/openai/codex/blob/main/codex-rs/core/gpt-5.2-codex_prompt.md
- gpt_5_codex: https://github.com/openai/codex/blob/main/codex-rs/core/gpt_5_codex_prompt.md

### 2. Kimi Code

- Default agent system prompt page: https://github.com/MoonshotAI/kimi-code/blob/main/packages/agent-core-v2/src/app/agentProfileCatalog/system.md

### 3. Grok Official xAI harness

- Default prompt: https://github.com/xai-org/grok-build/blob/main/crates/codegen/xai-grok-agent/templates/prompt.md

### 4. OpenCode

- Anthropic prompt: https://github.com/anomalyco/opencode/blob/dev/packages/opencode/src/session/prompt/anthropic.txt
- OpenAI prompt: https://github.com/anomalyco/opencode/blob/dev/packages/opencode/src/session/prompt/beast.txt
