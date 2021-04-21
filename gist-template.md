# regex-tutorial

Introductory paragraph (replace this with your text)

## Summary

I'm going to be talking about the email regex.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
* Anchors have their own meaning in Regex(regular expressions). Anchors identify/match what comes before or after characters:

   * ^ - The caret makes sure that the match starts at the beginning of the string.
   * $ - While the dollar sign makes sure that the match stops at the end of the string.

* Example:

``` 
^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$
```

* This reads as follows:

* Starting from ^ find the following until $ then stop.
### Quantifiers
* Quantifiers modify characters to find more specific numbers/lengths:

    * '*'(Asterisk) will find 0 or more.
    * '+'(Plus Sign) will find 1 or more.
    * '?'(Question Mark) will find 0 or 1.
    * '{}'(Curly Braces) will either find the minimum, maximum or equal amount of the length. 

    Ex.: {4, 6} will find everything with a minimum length of 4 and a maximum length of 6.
    while {4} will find everything with a length of 4.

* Let's take a look at this:

``` 
^([a-z\.]{2,6})$
```

* In this string we have {2, 6} next to a \. 
* Meaning it will find literally a dot followed by any letter with a minimum length of 2 and a maximum of 6.


### OR Operator
* OR Operator works in a way that allows you to have multiple (values|words|numbers) giving you multiple search criteria.

* |(vertical slash) - Acts as the OR when within parenthesis'. Only being used when there's 2 or more words.

* Example:
* ^I love (cats|dogs) but I always seem more interested in (snakes|spiders)\.$

* Will try to find the following:

```
I love cats but I always seem more interested in snakes.
I love cats but I always seem more interested in spiders.
I love dogs but I always seem more interested in snakes.
I love dogs but I always seem more interested in spiders.
```
### Character Classes
* Character Classes will try to find everything within [].

* Example:

   * l[yi (]nk will try to find any of the following:
```
l nk, lynk, link and l(nk
```
   * \d will find all digits.
   * \w will find all words.
   * \s will find any spaces.
   * . will find any/all digits, words AND spaces.

* Example:

* /^([a-z0-9_\.-]+) translates to: 
* Find 1 or more letters through a and z, with 1 or more numbers through 0 and 9 followed by either an underscore, a dot or a dash.

* @([\da-z\.-]+) translates to:
* Find the literal character @. Then find 1 or more digits followed by 1 or more characters through a and z. Followed by literally a dot or a dash.
### Flags
* Flags will try to make an expression find all of its matches rather than stop at the first one.

* Example:

```
regexp = new RegExp("pattern", "flags"); this is considered a 'long' syntax while:

regexp = /pattern/; // no flags
regexp = /pattern/gmi; // with flags g,m and i is considered a 'short' syntax.
```
### Grouping and Capturing
* Grouping allows specific matching parameters, Capturing is grabbing a specific part of a group and setting it apart from every other one.

* Example:

```
regex - \(? (\d{3}) [-.)]\d{3}[-.]\d{4}
replace - $1-XXX-XXXX
```
* The $1-XXX-XXXX will replace everything with XXX-XXXX except for the first (\d{3}) because we captured that group.

### Greedy and Lazy Match
* Greedy Matching will always try to match as many input characters as possible.

* Example:

```
\[.*\] will look for any line starting with '[' and ending with ']'

The problem with this is that it will would match this:

[Google](http://google.com), [Bing]

As if it were:

[Google(http://google.com), Bing]

Since it only wants to find the first Opening '[' and the last Closing ']'
```

* Lazy Matching will always try to match as few input characters as possible

* Example:

```
\[.*?\] will look for 0 or 1 input characters starting with '[' and ending with ']'

So the previous problem is fixed because it will match this:

[Google](http://google.com), [Bing]
```

### Boundaries
* Word Boundary or \b defines the position between \w and \W(non-word char), or at the beginning or the end of a string, if it begins or ends with a word character.
### Back-references
* Back-referencing identifies a previously matched group and looks for exactly the same text again.

* Example:

```
using \b(\w+)\s\1\b

will match the [is is, text text, double double, I I, not not, why why, rainbow rainbow, unicorn unicorn] inside the following:

This is is some text text with 
double double words some where I I I am
not not sure why why I am typing ok?
rainbow rainbow unicorn unicorn.
```
### Look-ahead and Look-behind
* Look-ahead determines that what's immediately following the current position is one or more word characters
* Look-behind determines that what's immediately prior to the current position is one or more word characters

* Example:

```
let str = "1 turkey costs 30€";

alert( str.match(/\d+(?=€)/) ); // 30, the number 1 is ignored, as it's not followed by €
```
## Author

* Thanks for reading, catch you next time. -taylor124
[My Github](https://github.com/taylor124)