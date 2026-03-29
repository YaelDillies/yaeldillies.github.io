---
layout: page
title: Git cheatsheet
---

Some git commands and workflows that are particularly helpful alongside VSCode and GitHub.

## Committing, navigation

Committing, pushing, pulling and switching branches is best done through the VSCode interface,
at the exception of a handful of commands.

`git push -f` updates the remote branch to your local branch, regardless of how they have diverged.
If you are collaborating with others and want to avoid losing their work,
use `git push --force-with-lease` instead.

## Editing history

`git merge <commit>` creates a merge commit on the current branch
with parents the current commit and `<commit>`.

`git merge --squash <commit>` replays all the changes until `<commit>` without staging them.
This is particularly useful when rebasing a branch containing merge commits.

`git rebase <commit>` replays all the commits until `<commit>`.
This is useful to keep up a series of "stacked diffs" through github PRs.
Careful, merge commits will be dropped and the conflicts they solved will have to be resolved.

`git rebase -i <commit>` asks you to reorder and fuse commits,
then replays the changes until `<commit>`.
The possible options for each commit are:
* `p` (pick, keeps the commit as it is),
* `f` (fixup, fuses the commit with the nearest picked commit above it),
* `d` (drop, drops the commit, same as deleting its line entirely),
* `e` (edit, lets you make further changes to the commit),
* `r` (reword, lets you edit the commit title/message).

`git reset <commit>` changes the head to `<commit>`
while preserving the current content of the files, eg `git reset HEAD^` "uncommits" the last commit.

`git reset --hard <commit>` changes the head to `<commit>` and the current content of the files
to their state at `<commit>`, eg `git reset --hard HEAD^` "undoes" the last commit.

`git cherry-pick <commit>` replays `<commit>`.

`git restore --source=<commit> <file>` changes the current content of `<file>`
to its content at `<commit>`.

## Git remotes

`git fetch <remote>` updates what your local git thinks of `<remote>` (except branch deletions).

`git fetch --all` updates what your local git thinks of all remotes (except branch deletions).
VSCode can run this command every five minutes if you set `autofetch` to `all`.

`git remote prune <remote>` makes your local git aware of what branches of `<remote>` were deleted.

`git remote add <name> <url>` creates a remote named `<name>` with URL `<url>`.

`git remote remove <name>` deletes the remote named `<name>`.

`git remote set-url <name> <url>` changes the URL of the remote named `<name>` to `<url>`.

## Commits

Commits can be referred to in many ways:
* `<branch>` is the latest commit of `<branch>`.
* `HEAD` is the head, the current commit.
* `<commit>^` is the parent commit of `<commit>`. Useful in combination with `HEAD`.
* `<commit>~<n>` is the `<n>`-th ancestor of `<commit>`,
  in particular `<commit>~0` = `<commit>` and `<commit>~1` = `<commit>^`.
