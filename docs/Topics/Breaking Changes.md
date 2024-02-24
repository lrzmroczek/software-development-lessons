## Scenario

- Someone ...
	- updated a development system
	- changed required software versions
	- updated their code
- ... and now ...
	- I can't build my code
	- my tests fail
	- nothing is working

## Key Takeaways

- Work on branches (see [[Workflow]]) to limit changes to the rest of the team until they can be verified
- Don't break the build environment
- Let teammates know if a breaking change is required
- Provide guidance on how to adapt to the breaking change

## What is a Breaking Change?

A change to functionality that intentionally OR unintentionally stops something else from working.

## How to Identify a Breaking Change

- Understand the impact of your changes
	- Who is working on something related?
	- Where will my changes be seen?

## How to Minimize Impact of Breaking Changes

[[Workflow]] takeaways:

- Keep work on a branch
- Merge the main branch into yours before merging back
- Synchronize breaking changes with teammates
- Wait for the CI to finish to verify it all works!

- If you don't have time to resolve problems after a merge, don't merge!
	- Merging at the end of the day, right before a weekend, or right before a major test is not a great idea
- Rushing through development to meet a deadline is not an excuse to skip the process - this is when mistakes happen!!

## What to Do If There Is a Breaking Change

- Identify the scope of changes
- Try to foresee what is required to adapt to the change
- Communicate the required changes to teammates at meetings, provide support and [[Documentation]], and justification on why the break needs to happen

## Breaking Software Updates

### Example Scenario
- Someone finds new version of software to get shiny, cool, new (unnecessary) feature
	- Then dependencies for the software increase
	- OS or other software does not support the increased dependencies
	- Everything breaks
- Resolution
	- Spend (lots of) time fixing problems (*me*)
	- Revert to original version