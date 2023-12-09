# Demystifying Regular Expressions(RegEx): Understanding and Implementing with Examples


## what is regex?
Regular expressions or `RegEx` are patterns used to match specific strings of characters in text. In JavaScript, regex can be used to validate forms, parse strings, replace text, and much more.

## So now what is its use in js?
---
Here I see examples of its use in regex in JavaScript:
- **Validate an email:**
```js
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
- **Parse a string into tokens:**
```js
/\w+/g
```
- **Find and replace text:**
```js
replace(/(hello)/g, 'hi')
```

Regex has many uses, these are just a few examples!

## Regex prerequisites?
---
To learn regex, you only need to know one programming language, such as JavaScript. This article will explain regex and make it easy to understand in JS.


# Let’s write our first regex!
In JS, regex can be written in 2 ways:

## First method:
---
```js
const regex = /ab+c/
```
## Second method:
---
```js
const regex = new RegExp("ab+c)
```
It doesn’t matter which syntax you use. They will have the same functionality
.
### Well, let's check this code together, `it doesn't matter which one`:
The `/ab+c/` pattern means:
- **Find a string that starts with a**
- **Followed by at least one b (the + means 1 or more)**
- **Ending with c**

Here are some valid and invalid examples:

Valid:

- "abbbc"
- "abbbbbbbbc"
- "abc"
- "ac"

Invalid:
- "aabbbc"
- "a.c"
- "abbbccc"
- "aaaabbbcccc"

# Using special characters:

You can use characters when looking for one or more special characters or even empty space
For example :

## The Dot (.) - Matches Any Character:
---
The `.` dot metacharacter will match any single character. For example:

`/h.t/` will match `hot`, `hut`, `h@t`, `h*t`, etc. It will match any single character between `h `and `t`.
#### **Valid and invalid example**:

`/.at/`

Valid: `cat`, `bat`, `sat`, `mat`

Invalid: `ct`, `tat`, `pat`

## The Asterisk (*) - Matches 0 or More Characters:
---
The `*` asterisk metacharacter will match 0 or more of the previous token. For example:

`/a*/` will match `a`, `aa`, `aaa`, `aaaaa`, etc. It will match any number of a’s.

`/h.t*/` will match `ht`, `hattt`, `h@tttt`, `h*y`, etc. It will match `h` followed by any single character, followed by 0 or more `t` ’s.
#### **Valid and invalid example**:

`/ab*c/`

Valid: `ac`, `abc`, `abbc`, `abccc`

Invalid: `aabbc`, `abxxc`


## The Plus (+) - Matches 1 or More Characters:
---
The `+` plus metacharacter will match 1 or more of the previous token. For example:

`/a+/` will match `a`, `aa`, `aaa`, `aaaaa`, etc. It will match any number of a’s, but must be at least 1.

`h.+t` will match `hat`, `haaat`, `h@t`, `h*ttt`, etc. It will match `h` followed by at least one of any character, followed by t.
#### **Valid and invalid example**:

`/ab+c/`

Valid: `abc`, `abbc`, `abccc`

Invalid: `ac`, `abxxc`

## The Question Mark (?) - Makes a Token Optional:
---
The `?` question mark metacharacter will make the previous token optional. It will match 0 or 1 times. For example:

`/colou?r/` will match `color` and `colour`. The `u` is optional.

`h.?t` will match `ht` and `hat`, but not `haat`. The middle character is optional (`?`) so it will match once or not at all.
#### **Valid and invalid example**:

`/colou?r/`

Valid: `color`, `colour`

Invalid: `coloour`, `colur`

`/A?pple/`

Valid: `Apple`, `Aple`

Invalid: `Appple`, `Apple`

# Meta Characters in Regex
Meta characters are characters with a special meaning in regex. They help define patterns that are more complex than a basic string of letters.

## \w - Matches any word character (letters, numbers, underscores)
`/\w+/`
Valid: `hello, 123, c_a`
Invalid: `-ab, *&^`

Test text: `hello _there123`

Matches:
- `hello`
- `_there`
- `123`

## \W - Matches any non-word character
`/\W/`
Valid: `* , -, &`
Invalid: `a , 1, _`

Test text: `hello*_-there&123`

Matches:
- `*`
- `_`
- `-`
- `&`


## \d - Matches any digit
`/\d/`

Valid: `1, 5, 0`
Invalid: `a, x, #`

Test text: `hello123there45`
Matches:
- `1`
- `2`
- `3`
- `4`
- `5`

## \D - Matches any non-digit

`/\D/`
Valid:` a, b, *`
Invalid: `1, 3, 7`

Test text: `hello123there45`

Matches:
- `h`
- `e`
- `l`
- `l`
- `o`
- `t`
- `h`
- `e`
- `r`
- `e`
## \s - Matches any whitespace character (spaces, tabs, newlines)
`/\s/`
Valid:` , \t, \n`
Invalid:` a, *, 3`

Test text:` hello there how are you`

Matches:
- ` `
- ` `
- `\t`
- `\n`
- `\t`
- ` `

---
# Flags in Regex
Flags are optional parameters that modify the behavior of a regex. They are specified after the final slash. By default, regex has no flags.

## `g` - Global flag
---
The g flag finds all matches rather than stopping after the first match.
`/a/g`
Valid: `aa` - will match both a’s
Invalid: `b` - no matches

Test text: `aaaaa`

Matches:

- `a`
- `a`
- `a`
- `a`
- `a`
  
Without the g flag, it would only match the first a.

## `i` - Case insensitive flag
---
The i flag makes the regex case insensitive.

`/a/i`
Valid: `a, A`

Invalid: `b`

Test text: `aAbBcC`

Matches:
- `a`
- `A`
- `b`
- `B`
- `c`
- `C`

Without the i flag, it would only match a, b, and c.

## `m` - Multi-line flag
---
The m flag allows ^ and $ to match newline characters. Without it, they will only match the start and end of the string.

`/^a/m`

Valid: `a\nbb` - will match `a` followed by a newline

Invalid: `bb\na` - will not match

Test text:
`a bb a`

Matches:

- `a`

Without the m flag, `^a` would not match anything in this test text.

# Special Characters in Regex:
Here is an explanation of special characters in regex along with examples:

## ^ - Matches the beginning of a string
---
`/^a/`
Valid: `abc, a123`

Invalid: `bca, 123a`

Test text:`abc a123 bca 123a`

Matches: 

- `a`(only in `a123`)

## $ - Matches the end of a string
---
`/a$/`

Valid: `abc, 123a`

Invalid: `bca, a123`

Test text: `abc a123 bca 123a`

Matches:

- `a` (only in `abc`)

## - Either or
---

`/ab/`

Valid:` a, b`

Invalid: `c`

Test text: `acb`

Matches:

- `a`
- `b`
It will match either `a` or `b`.

## \ - Escape character
--- 
A backslash \ escapes special characters to match their literal meaning.
`/a\/b/`

Valid: `a/b`

Invalid: `ab, a\b`

Test text: `a/b a\b ab`

Matches:
- `a/b`
The backslash escapes the `/` so it is matched literally instead of indicating an alternation.

## . - Any single character
---
`/a.c/`
Valid: `abc, a1c, a@c`
Invalid: `ac, abbc`

Test text:` abc a1c a@c ac abbc`

Matches:

- `abc`
- `a1c`
- `a@c`
  
It will match any single character between `a` and `c`.

I hope this helps explain special characters in regex. Let me know if you have any other questions!


# Regex Methods

Regex methods allow you to perform powerful operations on strings using regular expressions. Here are some practical examples of using common regex methods:

## .test() 
---
The test() method checks for a match in a string. It is used to validate input.

Example: Validate an email
```js
const regex = /^[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$/;
regex.test('mahdimamashli1383@gmail.com'); // Returns true
regex.test('mahdimamashli1383@gmail.co'); // Returns false
```


## .exec()
---
The exec() method returns information about the first match. It is used to extract information from a string.

Example: Extract a phone number
```js
const regex = /09(1[0-93[1-92[0129[012])-[0-9]{3}-[0-9]{4}/g;
const result = regex.exec('Call me at 0912-345-6789 or 0983-123-456'); 
// Returns ["0912-345-6789"]

```

## .match()
The match() method finds all matches in a string and returns them in an array. It is used when you want to extract multiple matches from a string.

Example: Find all zip codes
```js
const regex = /[0-9]{5}/g;
'Zipcodes: 94122, 10010, 90210'.match(regex);
// Returns ["94122", "10010", "90210"]
```
## .search()
The search() method searches for a match and returns the index of the first match. It is used when you want to check if a pattern exists in a string.

Example: Check if a string contains a number
```js
'Hello1'.search(/[0-9]/); // Returns 6 
'Hello'.search(/[0-9]/); // Returns -1
```
## .replace()
The replace() method replaces matches with another string. It is used to perform find and replace operations on strings.

Example: Censor words
```js
'Hello World!'.replace(/World!/, '****');
// Returns 'Hello ****'
```
---
# Summary: 
We covered a lot of ground in this tutorial! Here are the key takeaways:

- Regex or regular expressions are patterns used to match sequences of characters in strings.
-  In JavaScript, regex can be used for validation, parsing strings, replacing text, and more.
-  Regex has its own meta language with special characters, quantifiers, anchors, flags, and groups.

### The methods used for regex in JS are:
- `.test()` - Tests for a match
- `.exec()` - Returns info on the first match
- `.match()` - Returns all matches
- `.search()` - Searches for a match and returns the index
- `.replace()` - Replaces matches with another string

### • Regex flags include:
- `g` - Global search
- `i` - Case insensitive search
- `m` - Multi-line search

• Practice and experiment with regex! It is a powerful tool once mastered.


Thank you for reading my comprehensive guide to regular expressions in JavaScript! If you have any feedback, questions, or want to improve the article, please [`email`](mediishn@gmail.com) me.

You can also find more regex examples and projects on my [`GitHub`](https://github.com/m-mdy-m) and contact me on [`Twitter`](https://twitter.com/m__mdy__m). I hope this tutorial was helpful! Regex can seem cryptic, but with use it will become second nature.

Examples of practice repositories with regex:
([`repository 1`](https://github.com/m-mdy-m/highlight-text)) ([`repository 2`](https://github.com/m-mdy-m/Math-Games)) ([`repository 3`](https://github.com/m-mdy-m/Check-Password-Value))

• `MAHDI`
