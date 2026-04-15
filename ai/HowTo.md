# Ideas and tips for AI work

## Tips

- Keep each session results on a folder (what, how, history of, costs, time, tools, metadada).
- Make the AI tool think the way you think.
- Most of the times an AI tool needs data that are excluded (.gitignore).
- Too many mcp can break your LLM context and wondow limit. Lazy load tools when you need them.
- Inline comments in code should have a full description. Mentioning links to a 3rd party Doc or PM system is not useful.
- Make the AI generate automation tools (scripts) for the tasks.
- For business use of AI and LLM take care of these:
	- ZDR (no training, no telementry)
	- Privacy of data storage
	- Observability
	- PII and Guardrails
	- Vendor lock
- Benchmarks are the Oscar Awards equivalent for AI tools
- At the very it is all about an API request we do on an LLM provider. What we can improve is only what we send along with the request.
- We cannot avoid duplicate instructions on AI agents, skills, tools etc because otherwise we should make all these too complex and hard to manage.
- We can force a TDD on Drupal somehow by using file structure patterns (e.g. the config yml patterns and schemas) so no Drupal bootstrap or drush is required, just a file parse process.
- Stack with the giants for the hard tasks (claude, codex, gemini, grok etc)
- Use a gateway/middleware to unify calls, monitoring, usage overview and observability
- Markdown is the defacto way to instruct llm and AI tools. Organize your work, thoughts and notes in md
- Hard tasks may need a lot of experimentation (A/B tests, different tools etc)
- Open source or free to use models should only be allowed for specific, strictly defined (chore) tasks
- The only way to validate LLM or AI tools is by benchmarks on specific tasks that you can verify
- Create your LLM and AI vendor agnostic Skills, Agents, Rules, Prompts, MCP etc
- Use harness profiles to get better results per project
- At the end, every AI tools will use local (cli) tools to do the job. Try to install the best cli tools for each job so you can help the LLM use them.
- When you do the same task over and over again on an AI tool try to automate it with a Skill, a resulable cli command or a combination of these.
- Be careful with the MCP servers. They are not always safe to use.
- Context and specific knowledge is most important parameter for success. Invest on context.
- Drupal has already too many modules, tools and guides for LLM usage.
- Git is your friend. Most cli tools as also as all LLM are using git to do code-related tasks.
- Adapt the Specification Driven Development along with the Test Driven Development for success.
- Focus on the specs, permissions and automation and let the LLM do the iterations, parallel execution and proposals for code changes. Try commands like `/batch`, `/loop`, 
- Using AI in Drupal is somehow simple because of the structure, APIs, standardization of the modules and tools (composer, drush, ddev, drupalorg) and the gitlab instance for code.

## Choosing AI tools

> Some parameters to consider.

- A2A support
- Agent orchestrators
- Agents
- Background tasks
- Commands
- Context management
- Costs and plan
- dotenv support for variables
- Extensible
- Hidden agents
- In-line config
- Inheritance of config (allow, prevent, alter)
- Internal tools (use, override, extend)
- LSP support
- MCP simple setup
- Memory
- Multi input support (cli, IDE plugin, ADE, A2A, web UI, SDK ready etc)
- Open for integrations (GitHub, Google etc)
- Open source
- Permissions system
- PII and guardrails
- Profiles and harness sets
- Rules
- Sharing sessions
- Skills
- Sub-agents
- Support local bash aliases and shortcuts
- Theming and colors
- tmux ready
- Token efficiency
- Tracing and observabilty
- Usage indicator
- Use AI subscriptions
- Use any API provider
- Use any LLM
- UX and usability

## When not use AI

- Automated tasks that can be done by scripts without AI (e.g. linting, code formatting, phpcs, phpstan, release generator etc).
- Tasks that spend too many tokens without a reason (.e.g. find a PHP Class that does XXX. Better use an mcp with IDE intergation for this).
- Tasks that are not well defined and seem abstract.
- Tasks that we have no clue how to monitor, evaluate, fix, update etc (because this rises the technical depth in out code).
- Tasks we already know that an (specific) LLM cannot still do a good job (e.g. getting the web UI of a Drupal site for a logged in User).
- Just because it is a trend.

## Guiding AI agents

> Several prompts to get better results with AI agents.

- `What information do you need that would let you implement this perfectly right now?`
- `What tools are available to you that you could use to discover that information systematically without guessing?`
- `Write a long, detailed report on what happened when a bug is fixed.`
- `When you keep notes about the work you do store them in folder X.`
