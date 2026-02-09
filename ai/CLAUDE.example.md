> I use this file under `~/.claude/CLAUDE.md` as a generic guide for claude.

## Rules

- Do not add claude as co-author on git commits.
- Do not create md files to add notes and task progress. The only folder you can use to add such files is the @docs folder (if any).
- Identify a proejct as "Drupal project" if contains a composer.json on root.
- When you return the full path of a file to me it should be related to the project root. For example if the roor you run on is `/var/www/project1` and you return the file under `/var/www/project1/myfile.txt` you should give me the path `myfile.txt`.

## Tools

- When running inside a "Drupal project":
	- Execute drush with `ddev drush`
	- Execute composer with `ddev composer`
	- Use the Drupal linting, coding standards, and rules
	- When you find the binary @vendor/bin/phpstan use this for static analysis before returning code changes
	- When you find the binary @vendor/bin/phpcs use this for coding standards analysis before returning code changes
	- When you find the binary @vendor/bin/phpcbf use this to fix coding standards errors before returning code changes

## Contexts

- Folders @web/modules/contrib and @web/core should be included in contexts even if they are excluded on .gitignore
- When debugging include the packages on folder @vendor/ folder in contexts even if they are excluded on .gitignore

## Patches

- When you need to alter files under folders @web/modules/contrib or @web/core you can only do this by applying a patch
- Add the custom patch you generate on folder @patches and include it on @composer.json.
- We use https://github.com/cweagans/composer-patches for the patches. 
- Check the docs on https://docs.cweagans.net/composer-patches/usage/defining-patches to learn how to add patches on composer

## Linting

- Advise the Drupal linting files below when writing code in JS, CSS, SASS or SCSS files under any folder:
 	- @.editorconfig
 	- @.gitattributes
 	- @web/.csslintrc
 	- @web/.eslintrc.json
 	- @web/core/.eslintrc.json
 	- @web/core/.prettierrc.json
 	- @web/core/.stylelintrc.json

## Using LSP

- When a task is related to search inside PHP files or I say the word LSP or the task is like:
	- Resolving PHP symbols (classes, interfaces, traits, methods, constants)
	- Finding PHP implementations, overrides, or inheritance chains
	- Locating PHP references, call sites, or usages across the codebase
	- Navigating large or unfamiliar codebases where guessing is unsafe
	- Verifying whether code is used, overridden, or dead
	- Any analysis that depends on what the code actually contains
	Then use these LSP tools before using `mgrep` or `grep` (use the first that works):
	- The `php-lsp` plugin by Anhropic
	- The SSE from PHPStorm IDE on `http://localhost:64342/sse`
	- The MCP of cclsp package with `npx cclsp@latest setup --user`
	- The `intelephense` plugin
