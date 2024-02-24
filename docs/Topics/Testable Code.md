## Scenario

- You have to fix or update an existing code base, but you don't want to break any existing functionality
	- Case 1: There are minimal or no unit tests. It's not clear how any of the code works...or does it?
	- Case 2: There are lots of unit tests that all pass when you first run it.
	- **Which of the above situations is better?**
- You want to test the code, but all the functionality is in one giant function or requires complicated setup to exercise different cases.

## Key Takeaways

- A unit tested code base is MUCH easier to learn and contribute to
- Unit tests are a great way to be confident you didn't accidentally break something that used to work
- Break functionality into functions to allow for them to be tested independently
- Requirements should define tests, not the other way around - [[Test Driven Development]]
- Make code testable
- Functions and unit tests make showing incremental progress obvious
- If code is taken from a reference or example, make sure it actually does what you need it to do - test it!

## Functions

- Keep functions focused on a single thing
	- Return something or perform a task
- Avoid using state in functions unless required
- Make functions independent and deterministic
- Functions should be easily testable
	- If there is a lot of setup involved just to test a particular case, is there a more straightforward approach?
- Lambda functions can be challenging to unit test

### Example Code

> [!note]
> The example code can be found in the [Example Project](https://github.com/lrzmroczek/example-project/-/blob/testable-code/testable_code.py) repository.

Consider the following example code snippets:

> [!example]+ Example 1
> ```python
> y = [xx for xx in range(100) if ((xx // 10) + (xx % 10)) % 7 == 0]
> ```

> [!example]- Example 2
> ```python
> def tens(x):
>     return x // 10
> 
> def ones(x):
>     return x % 10
> 
> def sum_digits(x):
>     return tens(x) + ones(x)
>
> def is_divisible(x, divisor):
>     return x % divisor == 0
>
> z = [xx for xx in range(100) if is_divisible(sum_digits(xx), 7)]
> ```

> [!question]- What is this code doing?
> Finding all numbers less than 100 where the sum of the digits is divisible by 7

Which is easier to understand? Which is easier to test?

> [!bug]- Are there any potential bugs?
> - `tens()` and `sum_digits()` do not account for numbers >= 100

Some additional things to consider:

- How would you verify the results?
- How would the code change if the requirements changed?
- How much effort would it be to verify everything still works?

### Example Tests

These tests are using [pytest](https://docs.pytest.org/en/7.4.x/) as an example.

```python
def test_tens():
    assert tens(0) == 0
    assert tens(5) == 0
    assert tens(10) == 1
    assert tens(42) == 4
    assert tens(123) == 2
  
def test_ones():
    assert ones(0) == 0
    assert ones(5) == 5
    assert ones(10) == 0
    assert ones(42) == 2
    assert ones(123) == 3
  
def test_sum_digits():
    assert sum_digits(0) == 0
    assert sum_digits(5) == 5
    assert sum_digits(10) == 1
    assert sum_digits(42) == 6
    assert sum_digits(123) == 6
```


