# AI tools

> See also https://artificialanalysis.ai/agents/coding and https://codingplans.com.
> Items on ~~strikethrough~~ mean that I was using them at some point but not anymore.

## Comparison table

| Name      | URL                                                                                | Open source | IDE dedicated  | IDE plugins                              | Online PaaS | GUI (local) | BYOK   | Pricing                 | Notes                                             |
| --------- | ---------------------------------------------------------------------------------- | ----------- | -------------- | ---------------------------------------- | ----------- | ----------- | ------ | ----------------------- | ------------------------------------------------- |
| claude    | [https://www.anthropic.com](https://www.anthropic.com)                             | No          | No             | Yes (VS Code, JetBrains)                 | Yes         | No          | No     | Subscription + API      | Strong reasoning, Claude Code CLI agent           |
| cline     | [https://github.com/cline/cline](https://github.com/cline/cline)                   | Yes         | No             | Yes (VS Code)                            | No          | No          | Yes    | Free + API keys         | Open-source coding agent extension                |
| codex     | [https://platform.openai.com](https://platform.openai.com)                         | No          | No             | Yes (VS Code, JetBrains via Copilot/API) | Yes         | No          | No     | API usage               | Model/API layer for coding agents                 |
| copilot   | [https://github.com/features/copilot](https://github.com/features/copilot)         | No          | No             | Yes (VS Code, JetBrains)                 | Yes         | No          | No     | Subscription            | Inline autocomplete, GitHub-native                |
| cursor    | [https://cursor.sh](https://cursor.sh)                                             | No          | Yes            | No                                       | No          | Yes         | No     | Subscription            | AI-native IDE (VS Code fork)                      |
| gemini    | [https://ai.google.dev](https://ai.google.dev)                                     | No          | No             | Yes (VS Code, JetBrains)                 | Yes         | No          | No     | Free + API              | Google AI ecosystem                               |
| goose     | [https://github.com/block/goose](https://github.com/block/goose)                   | Yes         | No             | No                                       | No          | Yes         | Yes    | Free (BYO model)        | Local-first CLI agent                             |
| kilo code | [https://github.com/Kilo-Org/kilocode](https://github.com/Kilo-Org/kilocode)       | Yes         | No             | Yes (VS Code, JetBrains)                 | Yes         | Yes         | Yes    | Free + optional cloud   | Open-source agent platform, multi-model           |
| kiro      | [https://aws.amazon.com/kiro](https://aws.amazon.com/kiro)                         | No          | Yes            | No                                       | Yes         | Yes         | No     | Credit-based            | Spec-driven AI IDE                                |
| kimi      | [https://kimi.moonshot.cn](https://kimi.moonshot.cn)                               | No          | No             | Yes (VS Code)                            | Yes         | No          | No     | Freemium + API          | Long-context model                                |
| mistral   | [https://mistral.ai](https://mistral.ai)                                           | Partially   | No             | Yes (VS Code, JetBrains)                 | Yes         | No          | Yes    | API usage               | Open-weight models                                |
| opencode  | [https://github.com/opencode-ai/opencode](https://github.com/opencode-ai/opencode) | Yes         | No             | Yes (VS Code)                            | No          | Yes         | Yes    | Free + API              | CLI-first multi-model agent                       |
| qoder     | [https://qoder.com](https://qoder.com)                                             | No          | Yes            | Yes (JetBrains)                          | Yes         | Yes         | Likely | Subscription            | AI IDE + CLI + plugins                            |
| qodo      | [https://qodo.ai](https://qodo.ai)                                                 | No          | No             | Yes (VS Code, JetBrains)                 | Yes         | No          | No     | Subscription            | Code quality, testing focus                       |
| roocode   | [https://github.com/RooVetGit/Roo-Code](https://github.com/RooVetGit/Roo-Code)     | Yes         | No             | Yes (VS Code)                            | No          | No          | Yes    | Free + API              | Cline fork with extra modes                       |
| warp      | [https://warp.dev](https://warp.dev)                                               | No          | Yes (terminal) | No                                       | Yes         | Yes         | No     | Freemium                | AI terminal                                       |
| windsurf  | [https://windsurf.ai](https://windsurf.ai)                                         | No          | Yes            | No                                       | No          | Yes         | No     | Subscription            | AI-first IDE (Codeium)                            |
| zed       | [https://zed.dev](https://zed.dev)                                                 | Partially   | Yes            | No                                       | No          | Yes         | No     | Free + optional paid AI | High-performance editor with AI features          |

## Subscriptions

### LLM single vendor

- Claude code: https://claude.com/pricing
- Codex: https://developers.openai.com/codex/pricing
- Mistral Vibe CLI plan: https://chat.mistral.ai/upgrade/plans
- KwaiKAT_Coding Plan: https://www.streamlake.ai/marketing/coding-plan
- Minimax: https://platform.minimax.io/subscribe/token-plan
- Kimi Code: https://www.kimi.com/code
- Gemini: https://gemini.google/us/subscriptions
- Qwen coding plan: https://www.alibabacloud.com/en/campaign/ai-scene-coding
- z.AI: https://z.ai/subscribe
- Xiaomi Mimo: https://platform.xiaomimimo.com/#/token-plan
- StepFun: https://platform.stepfun.ai/step-plan

### LLM aggregators

- Kilo pass: https://kilo.ai/features/kilo-pass
- Opencode Zen: https://opencode.ai/docs/zen
- Opencode Go: https://opencode.ai/docs/go
- GitHub Copilot: https://github.com/features/copilot
- Fireworks Fire Pass: https://app.fireworks.ai/fire-pass
- Hugging Face Pro: https://huggingface.co/pro
- Cerebras: https://www.cerebras.ai/pricing
- Crof: https://crof.ai/pricing
- Amazon Q Developer: https://aws.amazon.com/q/developer/pricing
- Chutes: https://chutes.ai/pricing
- Ollama Cloud: https://ollama.com
- Groq: https://console.groq.com
- routing.run: https://routing.run/pricing
- BytePlus ModelArk Coding Plan: https://www.byteplus.com/en/activity/codingplan
- DevPass: https://code.llmgateway.io
- Alibaba AI Coding Plan: https://www.alibabacloud.com/en/campaign/ai-scene-coding

### ADE/IDE coding plans

- windsurf: https://windsurf.com/pricing
- cursor: https://cursor.com/pricing
- zed: https://zed.dev/pricing
- kiro: https://kiro.dev/pricing
- antigravity: https://antigravity.google/pricing
- warp: https://www.warp.dev/pricing
- qoder: https://qoder.com/pricing

## Favorite coding tools

- [**opencode**](https://github.com/anomalyco/opencode) (with https://ohmyopencode.org)
- [**claude**](https://github.com/anthropics/claude-code)
- [codex](https://github.com/openai/codex)
- [**task-master**](https://github.com/eyaltoledano/claude-task-master) (task and agents orchestrator)
- [**warp**](https://www.warp.dev)
- [crush](https://github.com/charmbracelet/crush)
- ~~[gemini](https://github.com/google-gemini/gemini-cli)~~
- ~~[openhands](https://github.com/OpenHands/OpenHands)~~
- ~~[qwen](https://github.com/QwenLM/qwen-code)~~
- ~~[kimi](https://github.com/MoonshotAI/kimi-cli)~~
- ~~[vtcode](https://github.com/vinhnx/vtcode)~~

## Favorite IDE plugins (PHPStorm)

- [AI Assistant](https://plugins.jetbrains.com/plugin/22282-jetbrains-ai-assistant) - I use this mostly with ACP agents, even with kilo
- [kilo code](https://kilo.ai)
- [Qodo - code reviewer](https://plugins.jetbrains.com/plugin/21206-qodo)
- [Qoder](https://qoder.com)
- [tabby](https://github.com/TabbyML/tabby)
- ~~[cline](https://cline.bot)~~

## IDEs to watch

- **windsurf**
- **cursor**
- zed
- goose
- [emdash](https://www.emdash.sh)
- ~~kiro~~
- ~~antigravity~~
- ~~droid~~

## Providers

- openrouter.ai
- apipie.ai

## Models

- Anthropic: Haiku, Sonnet, Opus
- OpenAI: GPT-X Codex
- xAI: Grok Code Fast X
- Google: Gemini X Pro
- Z.AI: GLM-X
- Kwaipilot: KAT-Coder-Pro V1
- MiniMax: MiniMax M2.X
- MoonshotAI: kimi-k2.5
- Qwen: Qwen3 Coder Plus
- Mistral: Codestral 2508
- Inception: Mercury Coder
- **Cognition: SWE-1.5** (available only on Windsurf IDE)
- Arcee AI: Coder Large
- Cohere: Command R+
- DeepSeek: DeepSeek-V3.2

## MCP

- https://github.com/modelcontextprotocol/servers
- https://github.com/mozilla-ai/mcpd-proxy
- https://ref.tools
- https://github.com/upstash/context7
- https://github.com/idosal/git-mcp

## Tracing and observability

- https://langfuse.com
- https://smith.langchain.com
- https://litellm.ai

## Zero data retention

Zero data retention (ZDR) means that a provider will not store or train your data for any period of time.

- https://openrouter.ai/docs/guides/features/zdr
- https://openrouter.ai/api/v1/endpoints/zdr
- https://opencode.ai/zen
- https://docs.windsurf.com/windsurf/ai-commit-message#privacy
- https://cursor.com/data-use
- https://developers.openai.com/api/docs/guides/your-data
- https://ai.google.dev/gemini-api/docs/zdr
- https://code.claude.com/docs/en/zero-data-retention (available only on Enterprise)

## Local GUI

- Claude GUI [official](https://claude.com/download), [Linux](https://github.com/aaddrick/claude-desktop-debian)
- https://anythingllm.com
- https://github.com/CherryHQ/cherry-studio
- https://chatboxai.app
- https://lmstudio.ai
- ~~gpt4all~~
- ~~ollama~~
- ~~jan~~
- ~~libreChat~~
- ~~brokk~~
- ~~deepchat~~
- ~~orchids~~
- ~~[localai](https://localai.io)~~

## Local image GUI

- https://invoke.ai
- https://www.comfy.org
- https://github.com/AUTOMATIC1111/stable-diffusion-webui

## Playgrounds

- https://openrouter.ai/chat
- https://huggingface.co/playground
- https://fal.ai/sandbox (Images)

## Other

- https://www.waveterm.dev
- https://www.browseros.com

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
- Tracing and observability
- Usage indicator
- Use AI subscriptions
- Use any API provider
- Use any LLM
- UX and usability
