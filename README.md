# git-tools

A few shell scripts for interacting with Git that I find useful.

Copyright 2018 Earl C. Ruby III

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## rebase-branch

`rebase-branch [branchname] [main]` -- Rebase branch with `<branchname>` against
`main` or another branch.

`[branchname]` defaults to the name of the current branch you're working on. `[main]`
defaults to "main".

## force-push

`force-push [branchname]` -- Force-push your rebased branch to origin.

`[branchname]` defaults to the name of the current branch you're working on.

## refresh-fork

`refresh-fork` -- When executed inside of a forked repository, updates the forked repository
based on the upstream repo's main branch.

## rename-branch

`rename-branch [old branch name] [new branch name]` -- Renames a branch locally
and on the remote origin.

# Rebasing and fixing conflicts

If you haven't done a lot of rebasing and fixing conflicts in Git I recommend that you make a
backup copy of your work directory first. If anything goes seriously wrong during this process
just restore your backup and start over, or pull a fresh copy from Github with:

```
git reset origin/$branchname --hard
```

That will wipe out any local changes you made and replace them with a copy from Github.

If you have a development branch that has conflicts due to changes in the main branch first
rebase your code against the current main branch:

```
rebase-branch $branchname $main
```

At this point you'll get a warning that there are merge conflicts. Use `git status` to find out
which files are affected. Fix the conflicts, then:

```
git rebase --continue
```

You may get more warnings about merge conflicts. Repeat the cycle of `git status`, fix conflicts,
`git rebase --continue` until all of the conflicts are fixed.

At this point your local copy of the `$branchname` branch will have all of the changes you made
and all of the latest changes from $main. To update your PR:

```
force-push $branchname
```

This will force-push your changes to Github and the Github copy of your branch will match the local,
rebased copy of your branch.

