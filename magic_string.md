## Magic String
### A String that has some special meaning in our code.

we should avoid to use them, because:

1. In a language that compiles, a magic string's value is not checked at compile time. If the string must match a particular pattern, you have to run the program to guarantee it fits that pattern. If you used something such as an enum, the value is at least valid at compile-time, even if it might be the wrong value.

2. If a magic string is being written in multiple places you have to change all of them without any safety (such as compile-time error). This can be countered by only declaring it in one place and reusing the variable, though.

3. Typos can become serious bugs. If you have a function:
    ```js
    func(string foo) {
        if (foo == "bar") {
            // do something
        }
    }
    ```
    and someone accidentally types:
    ```js
    func("barr");
    ```
    This is worse the rarer or more complex the string is, especially if you have programmers that are unfamiliar with the project's native language.

4. Magic strings are rarely self-documenting. If you see one string, that tells you nothing of what else the string could / should be. You will probably have to look into the implementation to be sure you've picked the right string.

    That sort of implementation is leaky, needing either external documentation or access to the code to understand what should be written, especially since it has to be character-perfect (as in point 3).

5.  Short of "find string" functions in IDEs, there are a small number of tools that support the pattern.

6. You may coincidentally use the same magic string in two places, when really they are different things, so if you did a Find & Replace, and changed both, one of them could break while the other worked.


reference: https://softwareengineering.stackexchange.com/questions/365339/what-is-wrong-with-magic-strings
