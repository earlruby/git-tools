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

`rebase-branch [branchname] [master]` -- Rebase branch with `<branchname>` against
`master` or another branch.

`[branchname]` defaults to the name of the current branch you're working on. `[master]`
defaults to "master".

## force-push

`force-push [branchname]` -- Force-push your rebased branch to origin.

`[branchname]` defaults to the name of the current branch you're working on.

## refresh-fork

`refresh-fork` -- When executed inside of a forked repository, updates the forked repository
based on the upstream repo's master branch.

