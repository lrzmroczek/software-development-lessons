## Scenario

- I implemented my feature and I *think* it works...
- I'm not super confident my changes didn't break something else

## Key Takeaways

- Follow the process:
	- Requirements/design
		- Define what it is supposed to do
	- Write tests
		- Verify code does what it should do (should fail first)
		- Helps to enforce [[Testable Code]]
	- Implement
		- Write code to pass tests
	- When passing, clean up and optimize
		- Tests will continue to verify functionality
		- **Optimization comes at the end**


> [!quote] Excerpt from *Modern C++ Programming with Test-Driven Development*, Section **3.3 The TDD Cycle**[^1]
> At each point in the TDD cycle, you must be able to answer many questions.
> 
> - *Write a small test​.* What’s the smallest possible piece of behavior you can increment the system by (​What’s the Next Test?​, offers a few ideas)? Does the system already have that behavior? How can you concisely describe the behavior in the test’s name? Does the interface expressed in the test represent the best possible way for client code to use the behavior?
> - *Ensure the new test fails​.* If it doesn’t, why not? Does the behavior already exist? Did you forget to compile? Did you take too large a step in the prior test? Is its assertion valid?
>  - ​*Write the code you think makes the test pass​.* Are you writing no more code than needed to meet the current set of behaviors specified by the tests? Are you recognizing where the code you just wrote will need to be cleaned up? Are you following your team’s standards?
> - ​*Ensure all the tests pass​.* If not, did you code things incorrectly, or is your specification incorrect?
> - *​Clean up the code changes you just made​.* What do you need to do in order to get your code to follow team standards? Does your new code duplicate other code in the system that you should clean up, too? Does the code exhibit questionable smells? Are you following good design principles? What else do you know about design and clean code that you should apply here? Otherwise, is the design evolving in a good direction? Does your code change impact the design of other code areas that you should also change?
> - *​Ensure the tests all still pass​.* Do you trust that you have adequate unit test coverage? Should you run a slower set of tests to have the confidence to move on? What’s the next test?

[^1]: [*Modern C++ Programming with Test-Driven Development*](https://learning.oreilly.com/library/view/modern-c-programming/9781941222423/f_0053.html#c3thinking.xref) by [Jeff Langr](https://learning.oreilly.com/search/?query=author%3A%22Jeff%20Langr%22&sort=relevance&highlight=true)
