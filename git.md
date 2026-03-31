# Advanced git commands

If we want to use more than 15% of **git** features we have to master these commands.

## Commands

**Undoing / Rewriting History**
- `git rebase` – reapply commits on top of another base
- `git revert` – create a new commit that undoes a previous one
- `git reset` – move HEAD and optionally unstage/discard changes
- `git restore` – restore working tree or index files
- `git commit -v --amend` – rewrite the last commit
- `git filter-branch` – rewrite history in bulk

**Inspection / Diff / Patch**
- `git diff` – show unstaged or staged changes
- `git diff-tree` – compare tree objects (low-level)
- `git apply` – apply a patch to the working tree
- `git format-patch` – generate patch files from commits

**Recovery / History Navigation**
- `git reflog` – log of where HEAD has been

**Environment / Config Inspection**
- `git var -l` – list git logical variables

**Selective Changes**
- `git cherry-pick` – apply specific commits
- `git stash` – shelve and restore uncommitted changes

**Branch Navigation**
- `git switch` – switch branches (modern replacement for `checkout`)

**Commit / Revision Lookup**
- `git name-rev` – find symbolic name for a given rev
- `git rev-parse` – parse revision expressions to hashes
- `git rev-list` – list commit objects
- `git shortlog` – summarise commit log by author
- `git log --oneline --graph --decorate --all` – visual commit graph

**Tagging / Release**
- `git tag` – create or list tags
- `git describe` – describe a commit using the nearest tag
- `git archive --format=zip --output=archive.zip HEAD` – export a snapshot

**Parallel Workspaces**
- `git worktree` – manage multiple working trees
- `git flow` – high-level branching workflow (extension)

**Authorship / Line History**
- `git blame` – show who last modified each line
- `git annotate` – alias for blame with slightly different output

**Search / Debug**
- `git grep` – search working tree or history
- `git bisect` – binary search to find a bug-introducing commit

**Tree / Index Inspection**
- `git ls-tree` – list contents of a tree object
- `git ls-files` – list tracked files in the index

**Documentation / Help**
- `git help -g` – list concept guides
- `git help everyday` – common commands for daily use

## Extensions

hooks... (preCommit etc)
plugins ... (e.g. https://github.com/tj/git-extras)

## Integrations

- All the AI tools (can) use git
- Composer on PHP can use git repositories to manage packages and versions
- Online paas, CI/CD tools etc use git
- Learning curve is simpler and a ton of tutorials etc exist our there
