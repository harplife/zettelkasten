---
alias: [Regular Expression, Regex, What is Regex, What is Regular Expression]
tags: [natural_language_processing, computer_science, WHAT-IS]
status: ongoing
edited: 2022-01-18
---

# Regular Expression
According to [wiki](https://en.wikipedia.org/wiki/Regular_expression), a __Regular Expression__ is a sequence of characters that specifies a _search pattern_ in text.

Stephen Cole Kleene #todo introduced the concept in 1950s.

FYI, this [answer](https://stackoverflow.com/a/50634830/10570582) gives an amazing explanation on what _word boundary_ (`\b`) does.

## Learning Resources
- [W3School Python Regex Tutorial](https://www.w3schools.com/python/python_regex.asp)
- [Mozilla JS Regex Tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)

## Testing Resources
- [Regex101](https://regex101.com/) has features like syntax highlighting, error message, list of matches, and explanation. Also has a quick reference.
- [Regexper.com](https://regexper.com/) is not a testing tool, per se, but it shows a nice diagram of the regex string. It also has nice detailed errors, which helps with fixing regex.

## Examples
- [[link_filter_regex|Link Filter Regex]]
- [[email_filter_regex|E-mail Filter Regex]]

## Ideas
### Regex Match Example Generator
Seems like [someone has done it](https://tom-lord.github.io/Reverse-Engineering-Regular-Expressions/) already, but it's a Ruby version. I'd like to make a [[python|Python]] version of it.

Of course, this would also require the program to have a _Regex Validator_, which I need to find sometime. #todo

To extend this project, I could make a Regex Testing Website - just like any other testing tools out there, but the main difference would be that it generates match examples. It would be a good way to find if there are _unintentional_ matches.

### Reverse Regular Expression
I was thinking maybe there could be a program that reverses the process of regex, where the input are the matched strings and its output is the regex string. Basically, it is a program that produces a _simplest_ regex that matches the given strings.

For example, if inputs are like these,
1. Text: `How is the show, Howard?`, Matches: `[How, show, Howard]`
2. Text: `Howl's moving castle`, Matches: `[Howl]`
3. Text: `It's chow time!`, Matches: `[chow]`

Its output could be (but not limited to):
`(?:\w?)+(?:h|H)ow(?:\w?)+`

I looked up if this is theoretically possible, and what I'm mostly getting is _"No, it's not possible"_. The reasons are that there could be infinitely many regex patterns which matches any given finite number of match strings. Like so,

- `(?:[a-z]?)+(?:h|H)ow(?:[a-z]?)+`
- `(?:[a-zA-Z]?)+(?:h|H)ow(?:[a-zA-Z]?)+`

These regex strings will have the same matched strings. There are also unforeseen effects, like how `\w` allows for much more than `[a-z]`.

The program will not account for the user's intention, like how the example I used above finds any _word_ that include the word "how". What if I meant to find words that include "ow", or "w"?

The only way to deliver the user's intention properly would be to have _a lot_ of match strings. That's _a lot_ of work.

This [answer on mathoverflow](https://mathoverflow.net/a/98022) says this might be possible with the use of [[machine_learning|Machine Learning]].

I think this might be possible even without the use of Machine Learning, as long as certain assumptions/limitations are set (although I don't know which).

The main reason why I think it is possible is because I came across this [website that generates a math expression with a given integer between 0 and 1000](https://enjeck.com/num2math/). It seems to generate seemingly infinite number of output for a given finite input.