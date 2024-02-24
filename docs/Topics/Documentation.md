## Scenario

Imagine the situation:

- You start a new job or project
- The senior developer (only other person on the team) knows how everything works. It's just them, so they didn't write it down.
- They start training you on how the code works. It's making some sense, but it's complicated.
- After 2 weeks of training and onboarding, the senior developer goes on vacation. "Nothing ever goes wrong, you should be fine."
- While they are on vacation, something goes wrong...
	- The customer calls you up asking for support on their production system.
- You don't know enough to solve the problem, but they need this fixed.  There is no one else.
- You are on the phone with them from 11:00 AM to 11:00 PM trying to understand how things work and find the bug that broke everything.

This situation is awful (speaking from personal experience).

> [!question]- How could this have gone better?
> Documentation!

> [!cite] My Mantra
> Write documentation so the next person can do your job (the next person may be you!).


## Key Takeaways

- Act like every day is your last day (one day will be) - don't wait until the end to write it down
- Be clear and explicit - you won't remember!
- Make it so people (including yourself) can use your work without your help
- Is this something that you would find useful?
- What is missing that would be useful to you?
- If you pick up the code in a year, will you remember how it works and how to use it?
- Write it like you are preparing for your last day
	- What would your replacement need to know if you weren't there? Could they get it to work? How long would it take to set up? To figure out how to use it?
- Adds notes in comments saying where code was taken from (links to StackOverflow, reference documentation, etc).
	- If someone (including you) is trying to read your code later, they can follow the link and learn why it was done this way or how to modify.
- Documentation applies to commit and merge messages too
	- You may need to find that commit with your important fix later

## Documentation Types

![[documentation_overview.png]][^1]
[^1]: https://documentation.divio.com/