# Claude Code

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
| Headless mode | claude -p "query" |
| Continue chat | claude --continue |
| Skip permissions | --dangerously-skip-permissions |
| Think opptions | "think", "think hard", "think harder", "ultrathink" |
| Plan mode | Shift+Tab x2 |
| List MCP servers | claude mcp list |
| Remove MCP | claude mcp remove <n> |
| Add MCP | claude mcp add <n> <cmd> |
| Install plugin | /plugin install <n> |
| Create worktree | git worktree add <path> <branch> |
| Auto-accept edits | --permission-mode acceptEdits |
| Specify tools | --allowedTools "Bash,Read,Edit" |

## CLI Basics

```bash
claude -p "query"        # Headless/print mode
claude --continue        # Continue last chat
claude --resume <id>     # Resume session
claude --dangerously-skip-permissions
```

## Keyboard Controls

- **ESC**: Stop operation / **ESC ESC**: History
- **Tab**: Toggle thinking mode
- **Shift+Tab**: Cycle modes (Edit → Auto-accept → Plan)
- **Up Arrow**: Navigate past chats
- **Shift+Drag**: Reference files (also images)
- **Ctrl+V**: Paste images

## Memory & Context

- **CLAUDE.md**: Auto-loaded project context (hierarchical)
- **AGENTS.md**: Symlink to CLAUDE.md for multi-agent setups
- **#**: Quick add memory to CLAUDE.md
- **@file**: Reference files
- **/clear**: Clear context (use often)
- **/compact**: Summarize conversation
- **/context**: Show token usage with details

## Parallel Sub-agents

```bash
git worktree add ../project-feature feature-branch
cd ../project-feature && claude
# Or ask: "Use subagents to refactor this"
```

## Context Management

- Clear between tasks with `/clear`
- Use `@imports` for large docs
- Save plans to markdown files
- Watch status bar: tokens (percentage)
- Auto-compact at ~200k tokens (avoid by clearing)

## Hooks & Plugins

- **Hooks**: .claude/hooks/ (PreThink, PostThink, PreToolUse, PostToolUse, Stop, Start etc)
- **Commands**: .claude/commands/ (custom slash commands)
- **Agents**: .claude/agents/ (custom agents)
- **Skills**: .claude/skills/ (custom skills)
- **Plugins**: /plugin install for marketplace extensions

## Effective Prompting

- Be specific with file paths
- Use `@references` to related files
- Ask for plan first with "think hard"
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
