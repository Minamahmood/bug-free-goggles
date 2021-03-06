# Regex Tutorial Starter Code

## Summary

This is a tutorial breakdown on how Regex is used to match a Hex Value in a body of text. /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ is the syntax that I will be using.

Hex Code is a way to identify color. It is always in a 6-digit alphanumeric sequence.

The regex string I am using will return a # Number sign character followed by either a 6 or 3 character length code with only lowercase letters a,b,c,d,e,or f or numbers 0,1,2,3,4,5,6,7,8, or 9.

## TABLE OF CONTENTS:

## Regex Components

### Anchors

### Quantifiers

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

- [github](#GITHUB)
- [email](#EMAIL)
- [LICENSE](#LICENSE)

## GITHUB: Minamahmood

## EMAIL: minamahmood83@gmail.com

## LICENSE: MIT

![MIT License](https://img.shields.io/badge/License-MIT-Green)

## Regex Components

## email regex:

([\w\.\-_]+)?\w+@[\w-_]+(\.\w+){1,}

## anchors:

this dosenot content any anchos Anchors belong to the family of regex tokens that don't match any characters,
but that assert something about the string or the matching process. Anchors assert that the engine's current position in the string
matches a well-determined location: for instance, the beginning of the string, or the end of a line.
The ^ and $ in the regex are Anchors, as seen in the beginning and end of the expression: /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/ n our regex above,
the beginning ^ and ending $ anchors indicate that the search must match characters defined by the piece of the expression located between the anchors: ([a-z0-9_.-]+)@([\da-z.-]+).
([a-z.]{2,6}) We will explain each of these components in their respective sections below.

## quantifier:

Quantifiers are used to quantify how many times a part of your regular expression should be repeated.
If users want to repeat a part in a regular expression such as an individual character, a character class or a sub-expression,
they can write a quantifier after it to specify how many times it should be repeated. For example, the regular expression /\d{4}/ matches a four-digit number.
It is the same as /\d\d\d\d/. The following list shows some examples of the most common quantifiers: ? (Repeated from 0 to 1 times),

- (Repeated from 0 to Infinity times), + (Repeated from 1 to Infinity times), {N} (Repeated from N to N times), {,N} (Repeated from 0 to N times),
  {N,} (Repeated from N to Infinity times), and {N,M} (Repeated from N to M times).
  A quantifire can be greedy or lazy-As Many/Few As Possible that is explained below.
  a*a+a? -0 or more, 1 or more, 0 or 1
  "+" Matches 1 or more of the preceding token. "*" Matches 0 or more of the preceding token.
  "?" Matches 0 or 1 of the preceding token, effectively making it optional.
  "?" Makes the preceding quantifier lazy, causing it to match as few characters as possible. By default, quantifiers are greedy,
  and will match as many characters as possible. a{5}a{2,} -Looks for exactly five, two or more
  {2,6} -forces the input of characters between two & six characters long.
  a+?a{2,}? -match as few as possible
  ab|cd -match ab or cd
  Possessive Quantifiers Disable Backtracking.
  There are occasionally situations where you'd like a quantifier to try and greedily match as many times as possible,
  but also to never give up any of the characters it has already matched, and instead fail the overall match
  instead of trying to backtrack. For example, consider the process of trying to match this regex: a{1,10}aaaaaaaaaaX.
  In this case, the '{1,10}' quantifier is 'greedy', so it will go ahead and try to consume as many 'a' characters as it's allowed
  to before moving on to the next pattern. It just so happens, that the pattern after this quantifier also consists of a long string
  of 'a's, and there aren't enough 'a' to share between both parts of the pattern! In fact, the regex engine will first try the entire
  search by choosing 10 'a's, only realizing at the 'Z' character that it made a mistake. Then it tries again with 9, then with 8 and
  so on until it tries to consume 1, and only then does it realize that the entire pattern won't match and fail.
  In this case, a 'possessive' quantifier can be used to speed up the process of failure. It does this by disabling
  the ability to 'backtrack' and re-attempt the rest of the match with one less repetition. For this use case of possessive quantifiers,
  we're only concerned with speeding up failing matches rather than matching something different.

## OR Operator:

The Alternation Operator ( | or | )
Alternatives match one of a choice of regular expressions: if you put the character(s) representing the alternation operator
between any two regular expressions a and b , the result matches the union of the strings that a and b match.
Character Classes: this contain Character Classes .the squer brackets alow the pattern to inclode what is in betwen them

## Flags:

Flags are the forward slashes // that begin and end the regex:
/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/
Regular expressions, including our regex above, are generally contained within slashes // that simply delimit the search pattern.
Some expressions have specific flags that modify the search parameters, such as making the seach case-insensitive,
but our regex just includes standard flags.

## Grouping and Capturing:

Parentheses () are used in regular expressions to group together pieces of the search.
In our regex, our expression is grouped into 3 sections:
/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/
As defined in previous sections above, the first group ([a-z0-9_.-]+) consists of the characters before the @ sign in an email address
(coder123, firstname.lastname, etc). The second group ([\da-z.-]+) consists of the characters just after the @ sign in an email address
(gmail, hotmail, etc). The third group ([a-z.]{2,6}) consists of the domain after the dot . at the end of the email address (com, net, co.jp, etc).

Greedy and Lazy Match:
Greedy Match is created when a regex includes a + as we can see twice in our regex below:
/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/ The + basically means "as many as possible" of the previous character(s),
For example, A+ would match "A", "AA", "AAA", and so on because it will match as many "A"s that may exist in the location.

In our regex above, the characters directly before the @ sign [a-z0-9_.-] and directly after the @ sign [\da-z.-]
are both followed by a +. In the context of this regex, it means there is not a limit to how many characters may exist before and after
the @ sign.

## Boundaries:

Boundaries work by matching strings and their positioning within words and phrases.
For instance, "\b" matches a word boundary between a word character and a non-word character or position,
and "\B" matches any position that is not a word boundary.

## Back-references:

Back-references allow the user to repeat a capturing group. It's used inside a regex by inlining its group number preceded
by a single backslash.

Look-ahead and Look-behind:
Look-ahead and look-behind matches fall under the "look-around" patterns.
Look-around lets you match a group before (look-behind) or after (look-ahead) your main pattern without including it in the result.
Negative look-arounds specify a group that can NOT match before or after the pattern

## Author:

This tutorial was made by Mina Mahmood a current student at the Berkely's coding bootcamp.
My work can be found here: https://github.com/Minamahmood/bug-free-goggles Thank you for taking the time to read this tutorial.
I hope it was helpful.

## links

https://gist.github.com/Minamahmood/bac7b29467c9ffa0d01585a5dcb12f5e

# Repo

https://github.com/Minamahmood/bug-free-goggles
