# RSML as a Language
!!! tip "Required Skills"
    RSML uses [Regex](https://en.wikipedia.org/wiki/Regular_expression) during logic path evaluations, so it's recommended you have at least a basic knowledge of it.
        
    RSML uses [MSBuild](https://en.wikipedia.org/wiki/MSBuild) [RIDs](https://learn.microsoft.com/en-us/dotnet/core/rid-catalog) to identify operating systems and CPU architectures, so it might be worth learning those.

<!-- Start with what's simpler, finish with what's tougher -->

## Files
The official standard file extension for **Red Sea Markup Language** files is `.rsea`, to avoid it being confused with other languages that also use the RSML abbreviation.

The `.rsml` file extension is also fine, but `.rsea` is preferred.

## Language Specification
!!! warning "Non-standardized"
    Red Sea is **not** a [standardized](standards/index.md) language. **For the sake of examplifying without getting too technical**, **we'll be using the [**official-25**](standards/official25.md) standard** in most of the documentation, as it's the closest to an official specification.

**Red Sea** is quite a simple language, **but the lack of an official specification** means behavior may vary across developer's implementations.

### Static Core Functionality (Standardized :green_circle:)

### Extensible Functionality (Partially Standardized :yellow_circle:)

### Implementation-specific Functionality (Non-Standardized :red_circle:)

## Operators

<!-- TODO: do this -->
<!-- wonderful comment -->

## Evaluation Process
??? info "Strictly markup"
    Despite the usage of wording such as _"return"_ and _"interpret"_, RSML is **purely declarative** - it can **not** execute, compile or transpile code.

RSML is evaluated from **start to finish**, meaning that the **very first** logic path that matches will be used and the evaluation ends there. All the logic beyond that point is ignored completely.

??? note "Return operator"
    Only the **primary operator** (`->` in the [`official-25`](standards/official25.md) standard) triggers the return of a logic path's value. The other operators, unless explicitly defined to do such, will never stop the evaluation.



## Syntax
RSML's syntax is quite simple and accessible, as there are _only_ **3** valid line syntaxes. This means RSML only considers three different syntaxes as valid ones.

Each logic path must be in a different line.

### Logic Path
A logic path is the _"interactive"_ part of RSML - it's what one would evaluate.

The syntax for this is quite simple.

Things worth mentioning:

* The operator **must** be one of the **3 defined in the standard you're using** ([*see Language Specification*](#language-specification)).
* The value **must** be enclosed in **double quotes** (`"`).

=== "Actual Syntax"
    ```rsea
    <regex-expression> <operator> <value>
    ```

=== "Example 1"
    ```py
    win.+ -> "This is a valid logic path syntax" # (1)!
    ```

    1. The line is valid, as long as the `->` operator is defined. This will match all hosts with the **Windows** operating system.

=== "Example 2"
    ```py
    (arch|ubuntu|debian)-x\d\d || "Linux is nice" # (1)!
    ```

    1. This will match **Debian**, **Ubuntu** and **Arch** **Linux** distributions, as long as the **CPU architecture** is `x86` based (`x86` or `x64`).

=== "Example 3"
    ```py
    osx.* || "An apple a day keeps the doctor away, I guess..." # (1)!
    ```

    1. Keep in mind **return values** must be enclosed in double quotes.

=== "Example 4"
    ```py
    win.* -> "I can smell windows.h" # (1)!
    osx.* || "An apple a day keeps the doctor away, I guess..." # (2)!
    .+-x64 -> "64-bits is standard nowadays" # (3)!
    ```

    1. In **`official-25`**, this operator ==**returns the logic path's value** and **ends evaluation**== (**only** if there's a match of course).
    2. In **`official-25`**, this operator ==**outputs the logic path's value** and does ***NOT* end evaluation**== (**only** if there's a match of course).
    3. If one is on 64-bit Windows, this line **wouldn't have been reached** since the **first line would have been a match** and **would've returned a value**.


### Special Actions
[Special Actions](behaviors.md) will be a matter of discussion later, but, as of right now, all you need to know is that their syntax is also quite simple.

=== "Actual Syntax"
    ```py
    @<special-action> [<argument>] # (1)!
    ```

    1. The argument is optional, being an empty string if not specified. The argument must not contain **any** spaces.

=== "Example 1"
    ```py
    @EndAll # (1)!
    ```

    1. This is the only built-in standardized special action available. It'll be discussed later.

=== "Example 2"
    ```py
    @MyAwesomeAction SomeValue # (1)!
    ```

    1. `SomeValue` does **not** need to be enclosed in double quotes.

=== "Example 3"
    ```py
    @@ technically valid # (1)!
    ```

    1. This line is valid, as there's no limitation to action names. Since the argument contains spaces, RSML will only use the first part of the argument (`technically`) as the whole argument.

### Comments
**Comments are quite simple in RSML.** If a `#!python #` character is at the start of a line, that line is now a comment.

However, every single line that's considered invalid is also a comment. Here are some examples with reasons as of why they're invalid.

=== "Actual Syntax"
    ```c
    # ... // (1)!
    ```

    1. Worth mentioning that a `#!python #` in any other location other than the start of a line is **not** a comment, unless the line is invalid.

=== "Example 1"
    ```py
    some random text # (1)!
    ```

    1. According to `official-25`, this line is invalid; therefore, a comment.

=== "Example 2"
    ```py
    // wrong type of comment # (1)!
    ```

    1. According to `official-25`, this line is invalid; therefore, a comment.

=== "Example 3"
    ```c
    # a comment // (1)!
    ```

    1. This line is a comment.

=== "Example 4"
    ```py
    win.+ || "Valid line" # (1)!
    ```

    1. This line is valid; therefore, **not** a comment.
