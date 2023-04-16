# Regular expressions

A regular expression is a sequence of characters that defines a search pattern in a text.

## Literal characters

In regular expression, literal characters are characters which when used in the regex they will literally search for the exact character in the text.

For example this regex `/abc/` will search for literally `a` literally followed by `b` and literally followed by `c`. In this case `'abcdedf'` will match but `'fdecba'` will not.

## Meta characters

The meta characters are used to match a pattern of characters for instance, instead of matching the literal character `'a'` you can match all alphabetic characters instead, and that's where the meta character comes

### Single character

- **\d** : match `0-9`, will only match digits from 0 to 9.
- **\D** : `not 0-9`, will only match everything which is not a digit from 0 to 9.
- **\w** : mathes `A-Za-z0-9`, will only match any uppercase letter, lowercase letter or a digit from 0 to 9.
- **\W** : matches `not A-Za-z0-9`, will only match anything which is not an uppercase or lowercase letter and not digit from 0 to 9.
- **\s** : matches `' '`, will match any whitespace (empty spaces)
- **\S** : matches anything which is not a whitespace.
- **.** : will match any character whatsover. anything like white space, letter, digit or special character. Will not match empty string though there have to be at least one character

### Quantifiers

Quantifiers are meta characters that modifies that previous character in the regex and says how many of that characters you want to match in a row. like when you want 3 digits after a letter, or wherever there is two consecutive whitespaces.

- **\*** : matches `0 or more` of characters, for example `/d*/` will match wherever we have 0 or more `'d'` characters.
- **+** : matches `1 or more` it will match where we have at least one or more of the previous character
- **?** : match zero or one which means it can be optional
- **{min, max}**: used to specify how the minimum and maximum characters to consider
  For example `/n{2,5}at`: this regex will match the text that has two or more (but not more than 5) followed by text `at`.

```js
/n{2,5}at/.test('nnak') // false because even if the n are two the text sequence after is not "at"
/n{2,5}}at/.test('nnnatomic') // true because it matches the test.
```

- **{n}** : matches number of times the character has to occur.

### Position

Position are meta characters that specifies the position of the character in the string itself.

- **^**: matches from the begining of the string. The whole provided regex has to be at the begining for geting a match.

```js
/^abc/.test('abcdefg') // true as 'abc' is at the start of the string
/^abc/.test('hello abc') // false as 'abc' is not at the start
```

- **$**: matches at the end of the string. The whole provided regex has to be at the end for geting a match.

```js
/abc$/.test('abcdefg') // false as 'abc' is not at end of the string
/abc$/.test('hello abc') // true as 'abc' is at the end of the string
```

- **\b**: matches the word boundary which means to get a match the provided regex has to be not in the middle of the characters
  `/\bat/`will match `'atmosphere'` but will not match `'cat'` because there is no word boundary at the front.

- **\B**: matches something which is not a word boundary which means it will match characters that are in middle of the word
  for example `/\Bon/` will match `'money'` because `'on'` is in middle of the word but will not match `'onwards'` as on is not in middle.

### Characters classes '[abc]'

Character classes will allow to match one of the enclosed characters and they are enclosed in brackets `[]`
One thing to note about character classes (also known as character sets) is that most metacharacters does not work as they do in normal regex.
for instance `[.]` the dot in the character class will be a literal dot instead of being a meta character

special characters in character classes are only `-` and `^`

```js
/gr[ae]y/ // will math either 'grey' or 'gray'
/[a-c]/ // will match character from a to c means a or b or c  notice how - is being a special character
/[-ac]/ // will match '-' or 'a' or 'c' because now the - is not in the middle it will not be special
/[^a-c]/ //will match anything which is NOT from 'a' to 'c' because '^' is at the front it will be a special character
/[a^c]/ // will match 'a' or '^' or 'c' because now the '^' is not at the front it will be treated as the literal character
```

### Alternation '(first|second)'

Provide the or alternation for patterns instead of single character.

```js
/(.net|.com|.org)$/; // will match either '.net' or 'com' or 'org' which is at the end of the string.
```

### Capturing groups

### Look around

**Positive lookahead (?=...)** : Matches the mentioned pattern (pattern on the left) only if it is ahead of (or immediately followed) by pattern on the right.

```js
/foo(?=bar)/ // will match foo when it is immediately followed by bar
/foo(?=bar)/.test('foobaz') // false because even if foo is there is not followed by bar
```

**Negative lookahead (?!...)**: Matches the mentioned pattern (pattern on the left) only if it is NOT ahead of (or NOT immediately followed) by pattern on the right.

```js
/foo(?!bar)/ // will match foo when it is NOT immediately followed by bar
/foo(?!bar)/.test('foobaz') // true because foo is there and is not followed by bar
```
