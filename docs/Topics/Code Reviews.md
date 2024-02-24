## Scenario

- I am new or don't know enough about the code to do a code review
- I don't know what to even look for when reviewing code
- Do I have to fix everything people comment on in my code?
- Code reviews are a stupid process that wastes time

## Key Takeaways

- Don't be afraid to review code - Even if you don't understand the code, code reviews are useful for everyone
- The person writing the code to be reviewed may not be confident either, so any review is great
- Use [conventional comments](https://conventionalcomments.org/) to help clarify your intentions.
- Read other people's comments - You may learn something!
- Be kind as a reviewer and open as a reviewee

## What to Look for?

- Bugs/Logic problems
- Efficiency improvements
- Documentation/comments
- Consistency
	- Naming conventions
	- Formatting
- Tests
- Magic numbers
	- Where did they come from?
	- Could they change?
	- What are the units?
- ["Bad smells"](http://www.laputan.org/pub/patterns/fowler/smells.pdf)

### For Reviewer

- Help identify potential issues
- Aim to learn why things were done a certain way
	- Learn new techniques or skills
	- If something's confusing, ask for clarification (maybe it should be in the comments)
- Gain an understanding of teammate's work
	- The reviewed code may be your responsibility one day!

### For Reviewee

- Nitpicks don't always have to be implemented
- Learn from teammate's suggestions
- Find potential coding errors
- Learn new ways of looking at a problem
- If people are struggling to understand something, it likely needs clarification
	- May need to split into clearer functions (see [[Testable Code]])
	- May need to add more comments or [[Documentation]]

## Conventional Comments

See [conventional comments](https://conventionalcomments.org/)[^1] for more information

> ![[conventional_comments_examples.png]] [^1]

|Label|Description|
|---|---|
|**praise:**|Praises highlight something positive. Try to leave at least one of these comments per review. _Do not_ leave false praise (which can actually be damaging). _Do_ look for something to sincerely praise.|
|**nitpick:**|Nitpicks are trivial preference-based requests. These should be non-blocking by nature.|
|**suggestion:**|Suggestions propose improvements to the current subject. It's important to be explicit and clear on _what_ is being suggested and _why_ it is an improvement. Consider using patches and the _blocking_ or _non-blocking_ [decorations](https://conventionalcomments.org/#decorations) to further communicate your intent.|
|**issue:**|Issues highlight specific problems with the subject under review. These problems can be user-facing or behind the scenes. It is strongly recommended to pair this comment with a `suggestion`. If you are not sure if a problem exists or not, consider leaving a `question`.|
|**todo:**|TODO's are small, trivial, but necessary changes. Distinguishing todo comments from issues: or suggestions: helps direct the reader's attention to comments requiring more involvement.|
|**question:**|Questions are appropriate if you have a potential concern but are not quite sure if it's relevant or not. Asking the author for clarification or investigation can lead to a quick resolution.|
|**thought:**|Thoughts represent an idea that popped up from reviewing. These comments are non-blocking by nature, but they are extremely valuable and can lead to more focused initiatives and mentoring opportunities.|
|**chore:**|Chores are simple tasks that must be done before the subject can be “officially” accepted. Usually, these comments reference some common process. Try to leave a link to the process description so that the reader knows how to resolve the chore.|
|**note:**|Notes are always non-blocking and simply highlight something the reader should take note of.|

[^1]


[^1]: https://conventionalcomments.org/
