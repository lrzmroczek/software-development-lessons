---
aliases:
  - Lessons Learned
---
These are my top lessons learned, along with additional info on related topics.

## What would make your job easier if everyone else did it?  Do THAT!

> [!related] Relevant Topics
> [[Feedback]]
> [[Documentation]]

Software development is a team sport.

## Write documentation in preparation for the next person

> [!related] Relevant Topics
> [[Documentation]]

- Make it so people (**including yourself**) can use your work without relying on your help or memory
- Be clear and explicit - you won't remember!
- Act like every day is your last day - don't wait until the end to write it down

## Don't make big changes on Friday afternoons

> [!related] Relevant Topics
> [[Workflow]]
> [[Breaking Changes]]

You don't want to break everyone's code on a Friday afternoon and stay late fixing it, do you??

- Keep work on a branch
- Merge the main branch into yours before merging back
- Synchronize breaking changes with teammates

- Understand the impact of your changes
	- Who is working on something related?
	- Where will my changes be seen?

- Wait for the CI to finish to verify it all works ([example CI pipeline](https://github.com/lrzmroczek/software-development/-/pipelines/876846))!
	
![[gitlab_ci_pipeline.png]] [^1]
[^1]: https://gitlab.com/

- If you don't have time to resolve problems after a merge, don't merge!
	- Merging at the end of the day, right before a weekend, or right before a major test is not a great idea
- Rushing through development to meet a deadline is not an excuse to skip the process - this is when mistakes happen!!

## Commit and push code OFTEN

> [!related] Relevant Topics
> [[Workflow]]

Commit and push regularly (if you don't push in git, your work stays local and isn't backup up on the server):
- Lets leads see progress
- Saves your work in case something happens to your machine
- Runs and tests code through the CI pipeline


## Define requirements and make a design BEFORE coding

> [!related] Relevant Topics
> [[Requirements & Design]]

- Defining requirements ahead of time dictates what the code should do and determines how it should be tested and designed.
- Doing this work up front saves a lot of headache later when trying to make sure the thing you built is suited for the task.

## Write tests - and write them FIRST

> [!related] Relevant Topics
> [[Testable Code]]
> [[Test Driven Development]]

- Define the behavior you want **FIRST** - It makes developing much easier!
- Tests should be driven by requirements and expected behavior

## Learn the tools to become more effective

> [!related] Relevant Topics
> [[Tools]]

- Try the tutorials on common tools (git, VSCode, Gitlab CI, debuggers) - they will give tips on features and shortcuts you may not have known about
- Use the tools available, within reason
- Don't use every tool you can find - it makes unnecessary dependencies for others

## Use debuggers

> [!related] Relevant Topics
> [[Debugging]]

## Use logging and appropriate log levels

> [!related] Relevant Topics
> [[Logging]]

## Ask about expectations for code (style, deployment, classification, etc)

> [!related] Relevant Topics
> [[Coding Guidelines]]

Each project is different. Ask the team or lead for their opinion and any relevant documentation - feel free to create it if it doesn't exist!

If documentation doesn't exist, create it yourself! Putting a draft in front of the lead or team and asking for buy-in is a lot easier than asking for someone to produce it themselves.  Plus, if you make the document, you can recommend styles that work for you.

## Provide feedback on the code AND process

> [!related] Relevant Topics
> [[Code Reviews]]
> [[Feedback]]

Be comfortable providing feedback up the chain on what is/isn't working. Everyone wants things to go smoothly.

Some common process problems:

- Challenges with project onboarding
	- What would make things easier?
- Process bottlenecks (code review backups)
- Single points of failure

If the problems are identified, solutions can be tried - it doesn't have to be perfect the first time.

Request a forum for feedback if one does not exist. Some examples include

- 1-on-1 (request these if you do not have them)
- Retrospective meetings

## Ask for help (within team and outside team)

> [!related] Relevant Topics
> [[Feedback]]

Don't be afraid to ask questions!

## Add maintenance into the schedule

The demands from sponsors is high, but there is often a pending "we should fix this when we have time..." That time never comes unless it is scheduled in.

Taking time to improve process, testing, documentation (non-feature adding stuff) is important and should be scheduled - it saves time in long run.

## Update software versions when there is a reason to do so

> [!related] Relevant Topics
> [[Breaking Changes]]

- Updates can introduce breaking changes unnecessarily.
- Try to understand the implications of an update beyond the scope of the component(s) for which you are responsible.

## Check results for errors

> [!related] Relevant Topics
> [[Secure Coding]]

Many functions will set a code or indicator when something goes wrong. Make sure you check to see what they say.

## Use issue trackers to break up work and track progress

Issue trackers like GitLab and Jira are useful for Project Manager, but can also be helpful in splitting up a task into managable chunks. A branch for each issue also helps keep work separated and reviewable.

- Create tickets to keep focused, track progress, add notes
	- If there were problems you encountered and solved (or not), add info to the ticket, in case the problem is encountered later - so someone else can use what you learned
