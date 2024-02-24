Some tips for being careful when developing code:

- Read complier errors AND warnings
- Check return values for errors
- Check pointers for NULL
- Initialize pointers to NULL
- Free memory when it is no longer needed
- Max sizes on strings, containers
- Compare variables of different sizes/signedness

## [The Power of 10](https://en.wikipedia.org/wiki/The_Power_of_10:_Rules_for_Developing_Safety-Critical_Code?useskin=vector)

The ten rules are[^1]:

1. Avoid complex flow constructs, such as [goto](https://en.wikipedia.org/wiki/Goto "Goto") and [recursion](https://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)").
2. All loops must have fixed bounds. This prevents runaway code.
3. Avoid [heap memory allocation](https://en.wikipedia.org/wiki/Memory_management#DYNAMIC).
4. Restrict functions to a single printed page.
5. Use a minimum of two [runtime assertions](https://en.wikipedia.org/wiki/Assertion_(software_development)#Assertions_for_run-time_checking "Assertion (software development)") per function.
6. Restrict the scope of data to the smallest possible.
7. Check the return value of all non-void functions, or cast to void to indicate the return value is useless.
8. Use the [preprocessor](https://en.wikipedia.org/wiki/Preprocessor "Preprocessor") sparingly.
9. Limit pointer use to a single [dereference](https://en.wikipedia.org/wiki/Dereference_operator "Dereference operator"), and do not use [function pointers](https://en.wikipedia.org/wiki/Function_pointer "Function pointer").
10. Compile with all possible warnings active; all warnings should then be addressed before release of the software.

[^1]: https://en.wikipedia.org/wiki/The_Power_of_10:_Rules_for_Developing_Safety-Critical_Code?useskin=vector