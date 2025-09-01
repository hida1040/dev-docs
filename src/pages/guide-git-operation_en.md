# Version Control Policy

This section defines the version control policy and recommendations for source code.

## Basic Policy

- Use AWS CodeCommit for source code version control.  
- Store and manage source code for each application in a single repository per domain (see [Monorepo](https://en.wikipedia.org/wiki/Monorepo)).  
- Direct changes or pushes to the main branch are prohibited. All changes must be merged via Pull Request (review).  
- Working branches should be created from the main branch. However, if conflicts with related or other tasks are expected, it is permitted to branch off from a working branch equivalent to the develop branch.  

## Branch Operation Rules

![worklow](../static/img/git.workflow_pr.png)

### Create PR (Pull Request)
After development is completed, create a Pull Request from the working branch to the main branch.  
Once the Pull Request is created, notify the reviewers to request a review.

### Review
At least one reviewer must conduct a code review.  
The review method (e.g., In-person Review, Desk Review) can be chosen as needed.  

#### Example Review Points
As shown below, code reviews should consider correctness, readability, safety, efficiency, and other aspects:

1. Does the implementation meet the requirements and design specifications?
2. Are there any bugs or logical inconsistencies? Is the code free of redundancy?
3. Is the structure designed with reusability in mind?
4. Are variables, functions, and classes consistently named according to conventions?
5. Are there any unused code or leftover debug statements?
6. Are comments provided appropriately for complex processes, without being excessive or insufficient?
7. Are performance and security considerations addressed?

Based on feedback, fixes should be pushed to the working branch as needed, ensuring that the changes are always up to date.  

### Rebase and Push to PR
Rebase the working branch onto the latest main branch (resolve any conflicts if they occur).  
Push the updated working branch to the Pull Request.

### Merge
Once the review and code updates are complete, merge into the main branch.  
The merge method should be fast-forward.  

To avoid merging multiple fixes for a single task into the main branch multiple times,  
merges into the main branch should be performed after review by the Japan side (internal acceptance) is complete.  
Any fixes arising during customer acceptance after the Japan side review (internal acceptance) should be made in a newly created separate working branch.

### Delete Branch
Delete the working branch once the merge into the main branch is complete.

## Note: commit
When writing commit messages, it is recommended to follow the style described in [Semantic Commit Messages](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716).

Format: `<type>: <program id> <subject> #<issue number>`

| Item              | Description                                                                 |
| ----------------- | --------------------------------------------------------------------------- |
| `<type>`          | Prefix to concisely indicate the nature of the commit                       |
| `<program id>`    | The target program ID                                                       |
| `<subject>`       | A brief title summarizing the commit                                        |
| `#<issue number>` | Issue number or date. Strongly recommended if it clearly identifies the commit target. |


Examples of `<type>`  
- `feat`    : New feature for users (not a new feature for build scripts)  
- `fix`     : Bug fix for users (not a fix for build scripts)  
- `docs`    : Documentation changes  
- `style`   : Format fixes, missing semicolons, etc. (no changes to production code)  
- `refactor`: Refactoring of production code (e.g., variable name changes)  
- `test`    : Addition of missing tests or test refactoring (no changes to production code)  
- `chore`   : Updates to tasks such as Grunt (no changes to production code)  



e.g.
```
feat: ZXXR000 update search form #0000
fix: ZXXR000 registration bug fix #0000
```

Filling in the Description field is optional.  
Also, if you frequently use Git commands, it is recommended to use GUI tools like the following to help prevent mistakes:

- [Fork](https://git-fork.com/)  
- [GitHub Desktop](https://desktop.github.com/download/)  
- [SourceTree](https://www.sourcetreeapp.com/)


## Note: GitHub flow

To promote effective collaboration among developers, the branch strategy will be based on [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow).

GitHub flow is a simple workflow composed of only two branch types, **main** and **feature**, in contrast to more complex strategies such as Git-flow or GitLab flow.  
When necessary, the creation of a **develop** branch is permitted for the purpose of integration.

![deploy](../static/img/git.github_flow.png)

| Branch        | Purpose                                                                 | Example              |
| ------------- | ----------------------------------------------------------------------- | -------------------- |
| main          | Stable branch containing release-ready or the latest project source code | -                    |
| develop       | Optional integration branch for ongoing development                     | -                    |
| feature/xxx   | Development branch for individual features or fixes                     | feature/login-form   |

In this application development, deployments to the development environment from feature branches are permitted for testing and review purposes.  
※ In general operations, deployments to environments are allowed only from integration branches such as **main** or **develop**.

![deploy](../static/img/git.github_flow_deploy.png)
