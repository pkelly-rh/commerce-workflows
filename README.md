# commerce-workflows
For housing reusable CI/CD config, GitHub Actions, etc


# Usage:
### How to use the Console Log Guard workflow
To use this work flow add a file called {any-name}.yml to a folder called `.github/workflows` in your repo. Cerate the folder if it doesn't exist.

```yml
name: Check Pull Requests
on:
  pull_request:
    types: [opened, reopened, synchronize, closed, ready_for_review]
jobs:
  consoleLogGuard:
    uses: RHCommerceDev/commerce-workflows/.github/workflows/console-log-guard.yml@develop
```
So now each pull_request will run this action on github ... and check for console.logs. It counts the lines and throws an error that can be seen on the PR page.

Note. `@develop` is the required ref for reusable workflows. It could be changed to another branch name like "release" or sha. 

# Development:
Run actions locally with a cli tool called `act`
Not really working for `console-log-guard` because of the github base sha variables. Maybe someone knows how to make it work.

Try
```bash
act workflow_call
```
[get the ACT CLI](https://github.com/nektos/act)
TLDR for mac users:
```
brew install act
```