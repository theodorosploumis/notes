# AI tips

## Tips

- Keep each session results on a folder (what, how, history of, costs, time, tools, metadata).
- Make the AI tool think the way you think.
- Most of the times an AI tool needs data that are excluded (.gitignore).
- Too many mcp can break your LLM context and window limit. Lazy load tools when you need them.
- Inline comments in code should have a full description. Mentioning links to a 3rd party Doc or PM system is not useful.
- Make the AI generate automation tools (scripts) for the tasks.
- For business use of AI and LLM take care of these:
  - ZDR (no training, no telemetry)
  - Privacy of data storage
  - Observability
  - PII and guardrails
  - Vendor lock
- Benchmarks are the Oscar Awards equivalent for AI tools
- At the very it is all about an API request we do on an LLM provider. What we can improve is only what we send along with the request.
- We cannot avoid duplicate instructions on AI agents, skills, tools etc because otherwise we should make all these too complex and hard to manage.
- We can force a TDD on Drupal somehow by using file structure patterns (e.g. the config yml patterns and schemas) so no Drupal bootstrap or drush is required, just a file parse process.
- Stick with the giants for the hard tasks (claude, codex, gemini, grok etc)
- Use a gateway/middleware to unify calls, monitoring, usage overview and observability
- Markdown is the defacto way to instruct llm and AI tools. Organize your work, thoughts and notes in md
- Hard tasks may need a lot of experimentation (A/B tests, different tools etc)
- Open source or free to use models should only be allowed for specific, strictly defined (chore) tasks
- The only way to validate LLM or AI tools is by benchmarks on specific tasks that you can verify
- Create your LLM and AI vendor agnostic Skills, Agents, Rules, Prompts, MCP etc
- Use harness profiles to get better results per project
- At the end, every AI tools will use local (cli) tools to do the job. Try to install the best cli tools for each job so you can help the LLM use them.
- When you do the same task over and over again on an AI tool try to automate it with a Skill, a reusable cli command or a combination of these.
- Be careful with the MCP servers. They are not always safe to use.
- Context and specific knowledge is most important parameter for success. Invest on context.
- Drupal has already too many modules, tools and guides for LLM usage.
- Git is your friend. Most cli tools as also as all LLM are using git to do code-related tasks.
- Adapt the Specification Driven Development along with the Test Driven Development for success.
- Focus on the specs, permissions and automation and let the LLM do the iterations, parallel execution and proposals for code changes. Try commands like `/batch`, `/loop`,
- Using AI in Drupal is somehow simple because of the structure, APIs, standardization of the modules and tools (composer, drush, ddev, drupalorg) and the gitlab instance for code.

## Token reduction tools

- https://github.com/rtk-ai/rtk
- https://github.com/edouard-claude/snip
- https://github.com/toon-format/toon
- https://github.com/drona23/claude-token-efficient
- https://github.com/Opencode-DCP/opencode-dynamic-context-pruning
- https://github.com/JuliusBrussee/caveman

## Web search and LLMs

LLMs use web search to find current information. Help them get better results by:
- Providing specific search queries or URLs instead of vague requests
- Using web search MCP servers or browser automation tools for targeted lookups
- Asking the LLM to verify sources and cite URLs in responses
- Combining search with context files for accurate, grounded answers
- Using search tools for API docs, changelogs, and recent developments that may not be in the training data

## When not to use AI

- Automated tasks that can be done by scripts without AI (e.g. linting, code formatting, phpcs, phpstan, release generator etc).
- Tasks that spend too many tokens without a reason (e.g. find a PHP Class that does XXX. Better use an mcp with IDE integration for this).
- Tasks that are not well defined and seem abstract.
- Tasks that we have no clue how to monitor, evaluate, fix, update etc (because this rises the technical depth in our code).
- Tasks we already know that a (specific) LLM cannot still do a good job (e.g. getting the web UI of a Drupal site for a logged in User).
- Just because it is a trend.

## Guiding AI agents

> Several prompts to get better results with AI agents.

- `What information do you need that would let you implement this perfectly right now?`
- `What tools are available to you that you could use to discover that information systematically without guessing?`
- `Write a long, detailed report on what happened when a bug is fixed.`
- `When you keep notes about the work you do store them in folder X.`

## Challenges

- All the git repositories will get bigger due to the new AI md files added
- cli VS IDE use (e.g. claude code VS Claude Desktop)
- Context ... is a king (in the AI era)
- How to control the token usage and costs?
- How to run parallel, sandboxed, automated tasks on the same code/project? Is [git worktree](https://git-scm.com/docs/git-worktree) enough?
- Local only VS dual (local + online)
- RAG Vs VectorDB
- Should we use an Agents tool (e.g. Jules, Arcade etc)
- What AI related files should we track on VCS?
- Which LLM should we use? (gemini, sonnet, minimax etc)
- Which mcp should we install?
- Which md (guides) should I create?
- Which provider should we use for LLM API use (openrouter, together, official vendors etc)

## Important practices in the AI era

> Things that were not so "trendy" some years ago but now seem almost required.

- Documentation in md files (tracked by VCS)
- Code docs (docblock etc)
- Test-Driven Development (TDD)
- Spec-Driven Development (SDD)
- Scripting (all the things)
- Terminal knowledge
- Prompting knowledge

## Tasks to automate with AI ASAP

- Analyze repository (code, tools, how to, devops, infra, services etc)
- Automate tasks you already do now (convert to skills, commands, agents etc)
- Code review before commiting
- Generate docs for the AI agents (agents.md etc)
- Refactor suggestions
- Reports and evaluation of technical depth
- Review pull requests
- Security audit (e.g. on custom code, secrets, services)
- Testing (create, optimize, automate)
- Try new things with sandboxes
