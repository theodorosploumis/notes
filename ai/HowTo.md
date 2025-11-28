# Ideas and tips for AI work

## Tips

- Keep each session results on a folder (what, how, history of, costs, time, tools, metadada).
- Make the AI tool think the way you think.
- Most of the times an AI tool needs data that are excluded (.gitignore).
- Too many mcp can break your LLM context and wondow limit. Lazy load tools when you need them.
- Inline comments in code should have a full description. Mentioning links to a 3rd party Doc or PM system is not useful.
- Make the AI generate automation tools (scripts) for the tasks.

## When not use AI

- Automated tasks that can be done by scripts without AI (e.g. linting, code formatting, phpcs, phpstan, release generator etc).
- Tasks that spend too many tokens without a reason (.e.g. find a PHP Class that does XXX. Better use an mcp with IDE intergation for this).
- Tasks that are not well defined and seem abstract.
- Tasks that we have no clue how to monitor, evaluate, fix, update etc (because this rises the technical depth in out code).
- Tasks we already know that an (specific) LLM cannot still do a good job (e.g. getting the web UI of a Drupal site for a logged in User).
- Just because it is a trend.