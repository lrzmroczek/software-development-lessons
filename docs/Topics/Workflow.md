---
aliases: 
tags:
  - git
  - workflow
  - merge
  - merge-request
  - "#branch"
  - "#branching"
  - branches
---
## Scenario

- Everyone on the team is working on the same code and constantly stomping on each other's toes
- Everyone's has been working for a while and finally puts everything together - and nothing works!
	- "It worked on my machine"
	- "**You** broke something" - Should be "**WE**" broke something
- You only have a small change to make, so you commit straight to `main` branch - but I made a mistake and it broke everything!
- I want to experiment, but I'm not sure the code will work

## Key Takeaways

- ALWAYS do your work on a branch, even if it's a small change
- Branches let everyone work independently
- Branches are free - make new branches to experiment and merge if they work
- Smaller branches make [[Code Reviews]] easier to review
- Always merge target branch into your branch **BEFORE** merging back - **then retest**!
	- Example: When I want to merge my `feat-offset` branch into `develop`, I should merge `develop` into `feat-offset` first and resolve any problems
- No merge conflicts != no problems
- Commit and push code regularly
	- If working on a branch, it shouldn't harm anyone else
	- Shows your team you are making progress
	- Provides a backup in case something happens to your computer and you lose your work
- Make sure code compiles and tests pass before merging
	- I try to avoid broken code even on my branches, but if I have to check in something that doesn't work, I mark it as "DRAFT" or "WIP" (Work in Progress)
- Use merge rules can be set up in GitHub/GitLab to protect branches from accidental merges
- Design and planning makes the development easier


[[Code Reviews]]

[[Merge Requests]]

## Git Workflow Walkthrough

### Process

- Create branch from the main (`main`, `develop`, etc) branch
- Do work, committing and pushing often on your branch
- When done, merge main branch updates back into your branch
- Make sure tests still work
- Open up a Merge Request
- Get reviewed by teammates
- Address comments, but be careful to stay focused on issue the branch is addressing
	- Any additional work can be put into a new issue to be worked in another branch
- Merge into main branch
- Notify team/anyone working on code that may be affected by your change (see [[Breaking Changes]])
	- Changes to how existing functionality works, what a function does
	- Changes to APIs or interfaces

> [!info] Example Project
> The workflow below is set up in an [example repository](https://github.com/lrzmroczek/sw-dev-lessons-example-project). Feel free to follow along on GitHub, or make a copy and play with it yourself!


### Example Scenario

In the example scenario below:

- I am a developer working on a team of **multiple people**
- Each person is working on something different

#### Project Setup

- After defining requirements (`define requirements` commit):
	- Where do we start?
	- How can people work without conflicting?
	- Create a stub so work can be separated
		- Separate functions allow
			- each team member to work independently
			- testing of small chunks of functionality
- `feat-stub` branch
	- One person can set up the project
	- Adds onboarding instructions, so anyone can pick up the repo and get started quickly
	- Adds some basic functionality (combined step for simplicity)
	- Merge branch back into `develop` branch
- Developers can now work independently and in parallel
	- Developer A (someone else) - Fix a bug - `fix-ave` branch
	- Developer B (me) - Add new feature - `feat-offset` branch
	- **However, both developer's work affects each other's!**

> [!example]+ Process
> 1. [Merge `feat-stub` branch into `develop` branch](https://github.com/lrzmroczek/sw-dev-lessons-example-project/pull/1)
> 1. [Merge `develop` branch into `main` branch`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/pull/2)
> 1. [Tag `main` branch as `v0.0`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/releases/tag/v0.0)
> 1. [Merge `fix-ave` branch into `develop` branch](https://github.com/lrzmroczek/sw-dev-lessons-example-project/pull/3)

#### Combining Work

- I am working on a new feature in the `feat-offset` branch
- Another developer is simultaneously fixing a bug in the  `fix-ave` branch
- The bug fix was finished first and merged into the `develop` branch
- I finished my new feature and am ready to merge it into `develop`

```mermaid
gitGraph
    commit id: "initial commit"
    branch develop
    commit id: "define requirements"

    branch feat-stub
    checkout feat-stub
    commit id: "create stub"
    checkout develop
    merge feat-stub id: "working stub"
    checkout main
    merge develop id: "working release" tag: "v0.0"
    checkout develop
  
    branch fix-ave
    branch feat-offset
  
    checkout fix-ave
    commit id: "adjust tests for median"
    commit id: "switch mean to median"
    commit id: "udpate documentation"
    checkout develop
    merge fix-ave id: "still working" tag: "workflow-branch-point-develop"
  
    checkout feat-offset
    commit id: "add failing offset tests"
    commit id: "implement offset"
    commit id: "integrate and test offset" tag: "workflow-branch-point-feat-offset"
  
    %% This is the branching point between the BAD and GOOD workflows
```

> [!question]- "What do I do next?"
> See [[Workflow#Good Workflow]]

> [!info]- Workflow branch point
> The Bad and Good workflows deviate these commits in the [`develop` branch](https://github.com/lrzmroczek/sw-dev-lessons-example-project/releases/tag/workflow-branch-point-develop) and [`feat-offset` branch](https://github.com/lrzmroczek/sw-dev-lessons-example-project/releases/tag/workflow-branch-point-feat-offset).


#### Bad Workflow

``` mermaid
gitGraph
    commit id: "initial commit"
    branch develop
    commit id: "define requirements"
  
    branch feat-stub
    checkout feat-stub
    commit id: "create stub"
    checkout develop
    merge feat-stub id: "working stub"
    checkout main
    merge develop id: "working release" tag: "v0.0"
    checkout develop
  
    branch fix-ave
    branch feat-offset
  
    checkout fix-ave
    commit id: "adjust tests for median"
    commit id: "switch mean to median"
    commit id: "udpate documentation"
    checkout develop
    merge fix-ave id: "still working" tag: "workflow-branch-point-develop"
  
    checkout feat-offset
    commit id: "add failing offset tests"
    commit id: "implement offset"
    commit id: "integrate and test offset" tag: "workflow-branch-point-feat-offset"
  
    %% This is the branching point between the BAD and GOOD workflows
    %% BAD workflow
  
    checkout develop
    merge feat-offset type: reverse id: "broken!"
  
    checkout main
    merge develop id: "Still broken!" type: reverse tag: "v1.0"
```

> [!info]- Branch names
> Copies of the branches were created in the [example repo](https://github.com/lrzmroczek/sw-dev-lessons-example-project) to illustrate this workflow:
> - [`develop-bad`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/develop-bad) is a copy of [`develop`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/develop)
> - [`feat-offset-bad`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/feat-offset-bad) is a copy of [`feat-offset`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/feat-offset), starting from the [`integrate and test offset` commit](https://github.com/lrzmroczek/sw-dev-lessons-example-project/releases/tag/workflow-branch-point-feat-offset)

> [!example]+ Process
> 1. [Merge `feat-offset` branch into `develop` branch](https://github.com/lrzmroczek/sw-dev-lessons-example-project/pull/4)
> 1. Test [`develop`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/develop-bad)  branch
>   	- **Branch is now broken (tests fail)!**

> [!failure] Why this is bad
> - Does not verify merged changes actually work
> - Relies exclusively on git's merge to solve all problems
> - Introduces problems into the target branch (`develop`)

#### Good Workflow

```mermaid
gitGraph
    commit id: "initial commit"
    branch develop
    commit id: "define requirements"

    branch feat-stub
    checkout feat-stub
    commit id: "create stub"
    checkout develop
    merge feat-stub id: "working stub"
    checkout main
    merge develop id: "working release" tag: "v0.0"
    checkout develop
  
    branch fix-ave
    branch feat-offset
  
    checkout fix-ave
    commit id: "adjust tests for median"
    commit id: "switch mean to median"
    commit id: "udpate documentation"
    checkout develop
    merge fix-ave id: "still working" tag: "workflow-branch-point-develop"
  
    checkout feat-offset
    commit id: "add failing offset tests"
    commit id: "implement offset"
    commit id: "integrate and test offset" tag: "workflow-branch-point-feat-offset"
  
    %% This is the branching point between the BAD and GOOD workflows
    %% GOOD workflow
    merge develop id: "resolve merge conflicts"
    commit id: "fix all tests"
  
    checkout develop
    merge feat-offset type: highlight id: "all still working!"

    checkout main
    merge develop id: "Still working" tag: "v1.0"
```

> [!info]- Branch names
> Copies of the branches were created in the [example repo](https://github.com/lrzmroczek/sw-dev-lessons-example-project) to illustrate this workflow:
> - [`develop-good`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/develop-good) is a copy of [`develop`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/develop)
> - [`feat-offset-good`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/feat-offset-good) is a copy of [`feat-offset`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/feat-offset), starting from the [`integrate and test offset` commit](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/feat-offset)

> [!example]+ Process
> 1. [Merge `develop` branch into `feat-offset` branch](https://github.com/lrzmroczek/sw-dev-lessons-example-project/pull/5)
> 1. Test [`feat-offset`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/feat-offset-good) branch
>      - **Branch is now broken (tests fail)!**
> 1. [Fix everything in the `feat-offset` branch](https://github.com/lrzmroczek/sw-dev-lessons-example-project/commit/2c2cdaefd9da21c527570b2b0a83440161bf8bcd)
> 2. [Merge `feat-offset` branch into `develop` branch](https://github.com/lrzmroczek/sw-dev-lessons-example-project/pull/6)
> 4. Test [`develop`](https://github.com/lrzmroczek/sw-dev-lessons-example-project/tree/develop-good) branch
>      - **Branch works (tests pass)!**

> [!success] Why this is good
> - Incorporates changes on the target branch (`develop`) before merging
> - Tests to make sure the result of the merge is still correct
> - Allows for fixing of problems before merging into the target branch (`develop`)

## Other Workflows

There are many different workflows. The example above is just one. 

Here are some examples from [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow#:~:text=What%20is%20Gitflow%3F,lived%20branches%20and%20larger%20commits)[^1]:

> [!info]+ Feature branch
> ![[02 Feature branches.svg]] [^1]

> [!info]+ Release branch
> ![[03 Release branches.svg]]  [^1]

> [!info]+ Hotfix branch
> ![[04 Hotfix branches.svg]]  [^1]


[^1]: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow#:~:text=What%20is%20Gitflow%3F,lived%20branches%20and%20larger%20commits