# Claude

## Cheatsheet

> See also https://github.com/Njengah/claude-code-cheat-sheet

| Action | Command |
|--------|---------|
| Stop operation | ESC |
| View history | ESC ESC |
| Toggle thinking | Tab  |
| Cycle modes | Shift+Tab |
| Navigate chats | Up Arrow |
| Reference file | @filename |
| Add memory | # |
| Execute command | ! (context dependent) |
| Clear context | /clear |
| Compact context | /compact |
| Undo changes | /undo |
| Resume session | /resume |
| Show context | /context |
| Manage permissions | /permissions |
| Edit memories | /memory |
| Add folders to session | [/add-dir](https://claudelog.com/faqs/--add-dir) |
| Headless mode | claude -p "query" |
| Continue chat | claude --continue |
| Skip permissions | --dangerously-skip-permissions |
| Think options | "think", "think hard", "think harder", "ultrathink" |
| Plan mode | Shift+Tab x2 |
| List MCP servers | claude mcp list |
| Remove MCP | claude mcp remove <n> |
| Add MCP | claude mcp add <n> <cmd> |
| Install plugin | /plugin install <n> |
| Create worktree | git worktree add <path> <branch> |
| Auto-accept edits | --permission-mode acceptEdits |
| Specify tools | --allowedTools "Bash,Read,Edit" |
| Insights report | /insights |

## CLI basics

```bash
claude -p "query"        # Headless/print mode
claude --continue        # Continue last chat
claude --resume <id>     # Resume session
claude --dangerously-skip-permissions
```

## Keyboard controls

- **ESC**: Stop operation / **ESC ESC**: History
- **Tab**: Toggle thinking mode
- **Shift+Tab**: Cycle modes (Edit -> Auto-accept -> Plan)
- **Up Arrow**: Navigate past chats
- **Shift+Drag**: Reference files (also images)
- **Ctrl+V**: Paste images

## Memory and context

- **CLAUDE.md**: Auto-loaded project context (hierarchical)
- **AGENTS.md**: Symlink to CLAUDE.md for multi-agent setups
- **#**: Quick add memory to CLAUDE.md
- **@file**: Reference files
- **/clear**: Clear context (use often)
- **/compact**: Summarize conversation
- **/context**: Show token usage with details

## Parallel sub-agents

```bash
# git worktree add ../project-feature feature-branch
# cd ../project-feature && claude
git worktree add ../feat-auth feature/auth
git worktree add ../feat-api feature/api
git worktree add ../feat-ui feature/ui

# Then, run claude in each (separate terminals)
cd ../feat-auth && claude
cd ../feat-api && claude
cd ../feat-ui && claude

# Or ask: "Use subagents to do this"
```

## Context management

- Clear between tasks with `/clear`
- Use `@imports` for large docs
- Save plans to markdown files
- Watch status bar: tokens (percentage)
- Auto-compact at ~200k tokens (avoid by clearing)

## Hooks and plugins

- **Hooks**: .claude/hooks/ (PreThink, PostThink, PreToolUse, PostToolUse, Stop, Start etc)
- **Commands**: .claude/commands/ (custom slash commands)
- **Agents**: .claude/agents/ (custom agents)
- **Skills**: .claude/skills/ (custom skills)
- **Plugins**: /plugin install for marketplace extensions

## Effective prompting

- Be specific with file paths
- Use `@references` to related files
- Ask for plan first (with the words "think hard") or `/plan` command
- Break large tasks into steps
- Save plans to docs for reference
- Small diffs, short prompts
- Keep `.claude/` folder clean and versioned

## Companion tools

- https://github.com/musistudio/claude-code-router (`ccr`)
- https://github.com/kbwo/ccmanager (`ccmanager`)
- https://github.com/foreveryh/claude-code-switch (`ccm`)
- https://github.com/GWUDCAP/cc-sessions (`npx cc-sessions`)
- https://github.com/ruvnet/claude-flow (`npx claude-flow@alpha`)
- https://opcode.sh (GUI for Claude cli, `opcode`)

## Documentation

- https://docs.claude.com/en/docs/claude-code
- https://www.anthropic.com/engineering/claude-code-best-practices
- https://github.com/hesreallyhim/awesome-claude-code

## CLAUDE.md template for Drupal projects

> Example template to use under `~/.claude/CLAUDE.md` or project-level `CLAUDE.md`.

### Rules

- Do not add claude as co-author on git commits.
- Do not create md files to add notes and task progress. The only folder you can use is @docs (if any).
- Identify a project as "Drupal project" if it contains a composer.json on root.
- When returning a full file path, make it relative to the project root.

### Tools

- When running inside a "Drupal project":
  - Execute drush with `ddev drush`
  - Execute composer with `ddev composer`
  - Use the Drupal linting, coding standards, and rules
  - When you find @vendor/bin/phpstan use this for static analysis before returning code changes
  - When you find @vendor/bin/phpcs use this for coding standards analysis before returning code changes
  - When you find @vendor/bin/phpcbf use this to fix coding standards errors before returning code changes

### Contexts

- Folders @web/modules/contrib and @web/core should be included in contexts even if excluded in .gitignore
- When debugging include packages in @vendor/ folder even if excluded in .gitignore

### Patches

- When you need to alter files under @web/modules/contrib or @web/core, only do this by applying a patch
- Add custom patches to @patches and include them in @composer.json
- We use https://github.com/cweagans/composer-patches
- Docs: https://docs.cweagans.net/composer-patches/usage/defining-patches

### Linting

- Advise the Drupal linting files below when writing code in JS, CSS, SASS or SCSS:
  - @.editorconfig
  - @.gitattributes
  - @web/.csslintrc
  - @web/.eslintrc.json
  - @web/core/.eslintrc.json
  - @web/core/.prettierrc.json
  - @web/core/.stylelintrc.json

### Using LSP

- When a task is related to searching inside PHP files or LSP is mentioned, use these tools before `mgrep` or `grep`:
  - The `php-lsp` plugin by Anthropic
  - The SSE from PHPStorm IDE on `http://localhost:64342/sse`
  - The MCP of cclsp package with `npx cclsp@latest setup --user`
  - The `intelephense` plugin
- Use LSP for:
  - Resolving PHP symbols (classes, interfaces, traits, methods, constants)
  - Finding PHP implementations, overrides, or inheritance chains
  - Locating PHP references, call sites, or usages across the codebase
  - Navigating large or unfamiliar codebases where guessing is unsafe
  - Verifying whether code is used, overridden, or dead
  - Any analysis that depends on what the code actually contains

---

## Alternative LLM providers

> Use several LLM providers (inferences) with Claude so you can save some $.
> See https://code.claude.com/docs/en/llm-gateway#llm-gateway-configuration

### Z.AI

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.z.ai/api/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "XXXXXX",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "glm-4.5-turbo",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "glm-5.2",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "glm-5.2"
  }
}
```

### DeepSeek

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.deepseek.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "XXXXXX",
    "ANTHROPIC_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "deepseek-v4-flash[1m]",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1",
    "CLAUDE_CODE_EFFORT_LEVEL": "max"
  }
}
```

### OpenRouter

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://openrouter.ai/api",
    "ANTHROPIC_AUTH_TOKEN": "XXXXXX",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "openrouter/free",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "openrouter/free",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "openrouter/free"
  }
}
```

### Chutes

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://claude.chutes.ai",
    "ANTHROPIC_AUTH_TOKEN": "xxxxxx",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "zai-org/GLM-5-Turbo",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "moonshotai/Kimi-K2.5-TEE",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "MiniMaxAI/MiniMax-M2.5-TEE",
    "backup_model": "unsloth/Mistral-Nemo-Instruct-2407-TEE"
  }
}
```

### Lightning.ai (Openai compatible only)

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://lightning.ai/api",
    "ANTHROPIC_AUTH_TOKEN": "xxxxxx",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "google/gemini-2.5-flash-lite-preview-06-17",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "openai/gpt-5.4-mini-2026-03-17",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "google/gemini-3.5-flash"
  }
}
```

### TokenFlux

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://tokenflux.ai/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "xxxxxx",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "openai/gpt-5-nano",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "openai/gpt-5-mini",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "openai/gpt-5"
  }
}
```

### Ollama (local)

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "http://localhost:11434",
    "ANTHROPIC_AUTH_TOKEN": "ollama",
    "ANTHROPIC_MODEL": "qwen2.5-coder",
  }
}

```

### APIpie (Codex, openai)

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://apipie.ai/v1",
    "ANTHROPIC_AUTH_TOKEN": "XXXXXX",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "anthropic/claude-haiku-4.5",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "anthropic/claude-sonnet-4.6",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "anthropic/claude-opus-4.6"
  }
}
```

### piapi.ai (Codex, openai)

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.piapi.ai/v1/",
    "ANTHROPIC_AUTH_TOKEN": "XXXXXXX",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_MODEL": "claude-sonnet-4-6",
  }
}
```

### AImlAPI.ai

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.aimlapi.com",
    "ANTHROPIC_AUTH_TOKEN": "XXXXXXX",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "anthropic/claude-haiku-4-5",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "anthropic/claude-sonnet-4.6",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "anthropic/claude-opus-4-8"
  }
}
```

### LiteLLM (local)

```json
{
  "env": {
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_BASE_URL": "http://localhost:4077",
    "ANTHROPIC_AUTH_TOKEN": "XXXXXX",
    "ANTHROPIC_MODEL": "sonnet",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "haiku",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "sonnet",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "opus",
  }
}
```

Can also use API endpoints from OpenCode Zen/Go, Kilo Gateway etc.
