
## Javascript Algorithms and Data Structure > [Reqular Expressions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions)

### - Using The Test Method

```
let myString = "Hello, World!";
let myRegex = /Hello/;
let result = myRegex.test(myString);
```

### - Match Literal Strings

```
let waldoIsHiding = "Somewhere Waldo is hiding in this text.";
let waldoRegex = /Waldo/; // Change this line
let result = waldoRegex.test(waldoIsHiding);
```

### - Match a Literal String with Diffrent Possibilities

Using alertnation of OR operator : |

```
let petString = "James has a pet cat.";
let petRegex = /dog|cat|bird|fish/; // Change this line
let result = petRegex.test(petString);
```

### - Ignore Case While Matching

Case is the difference between uppercase letters and lowercase letters. Example uppercase are A, B, C and lowercase are a, b, c. To ignore this case while matching, we can use **i** flag (*/i*)

```
let myString = "freeCodeCamp";
let fccRegex = /freecodecamp/i; // Change this line
let result = fccRegex.test(myString);
```

### - Extract Matches

we can extract the actual matches we found with the .match() method.

Note that the .match syntax is the "opposite" of the .test method you have been using thus far:

```
'string'.match(/regex/);
/regex/.test('string');
```

```
let extractStr = "Extract the word 'coding' from this string.";
let codingRegex = /coding/; // Change this line
let result = extractStr.match(codingRegex); // Change this line
```

### - Find More Than The First Match

To search or extract pattern more than once, we can use */g* flag. 

Note: we can have multiple flag on our regex */search/gi*

```
let twinkleStar = "Twinkle, twinkle, little star";
let starRegex = /Twinkle/gi; // Change this line
let result = twinkleStar.match(starRegex); // Change this line
```

### - Match Anything with Wildcard period

The wildcard character (.) will match any one character. The wildcard is also called *dot* or *period*. We can use the wildcard just like any other character in a regex. For example, if we want to seacrh hug, huh, huj, huk, we can use regex */hu./* to match all four words.

### - Match Single Character with Multiple Possibilities

You can search for a literal pattern with some flexibility with character classes. Character classes allow you to define a group of characters you wish to match by placing them inside square (\[and\]) brackets.

For example, you want to match bag, big, and bug but not bog. You can create the regex /b\[aiu\]/g to do this. The \[aiu\] is the character class that will only match the characters a, i, or u.

```
let quoteSample = "Beware of bugs in the above code; I have only proved it correct, not tried it.";
let vowelRegex = /[aeiou]/gi; // Change this line
let result = quoteSample.match(vowelRegex); // Change this line
```

### - Match Letters of Alphabet

Inside a character set, you can define a range or characters to match using a hyphen character: -.

For example, to match lowercase letters a through e you would use \[a-e\].

```
let quoteSample = "The quick brown fox jumps over the lazy dog.";
let alphabetRegex = /[a-z]/gi; // Change this line
let result = quoteSample.match(alphabetRegex); // Change this line
```

### - Match Numbers and Letters of The Alphabet

Using the hypen (-) to match a range of character is not limited to letter but also works to numbers.

```
let quoteSample = "Blueberry 3.141592653s are delicious.";
let myRegex = /[h-z2-6]/gi; // Change this line
let result = quoteSample.match(myRegex); // Change this line
```
### - Match Single Characters not Specified

We can create set of character that we don't want to match. These types of character sets are called *negated character sets*

To create a negated character set, we place a caret character(^) after the opening bracket(`[`) and after the character we don't to match.

For example, `/[^aeiou]/gi` matches all characters that are not a vowel. Note that characters like `., !, [, @, /` and white space are matched - the negated vowel character set only excludes the vowel characters.


**Instruction**
Create a single regex that matches all characters that are not a number or a vowel. Remember to include the appropriate flags in the regex.

**Code**
```
let quoteSample = "3 blind mice.";
let myRegex = /[^0-9^aeiou]/gi; // Change this line
let result = quoteSample.match(myRegex); // Change this line
```

### Match characters that occur one or more times

We can match a character (or group of characters) that appears one or more times in a row using the plus character(+).

For example, /a+/g would find one match in abc and return \["a"]. Because of the +, it would also find a single match in aabc and return \["aa"]

**Instruction**
You want to find matches when the letters occurs one or more times in Mississippi. Write a regex that uses the + sign.

**Code**
```
let difficultSpelling = "Mississippi";
let myRegex = /s+/g; // Change this line
let result = difficultSpelling.match(myRegex);
```

### Match characters that occur zero or more times

To match characters that occur zero or more times, we can use the asterik or star(*)

**Instruction**
For this challenge, chewieQuote has been initialized as the string Aaaaaaaaaaaaaaaarrrgh! behind the scenes. Create a regex chewieRegex that uses the * character to match an uppercase A character immediately followed by zero or more lowercase a characters in chewieQuote. Your regex does not need flags or character classes, and it should not match any of the other quotes.

**Code**
```
// Only change code below this line
let chewieRegex = /Aa*/; // Change this line
// Only change code above this line

let result = chewieQuote.match(chewieRegex);
```

### Find Character with Lazy Matching

In regular expressions, a *greedy* match finds the longest possible part of the string that fits the regex pattern and returns it as a match. The alternative is called a *lazy* match, which find the smallest possible part of the string that satisfies the regex pattern.

To make the *lazy* match, we can use the ? character

example
```
"titanic"

greedy match 
/t[a-z]*i/ // return 'titani'

lazy match
/t[a-z]*?i/ // return 'ti'
```

**Instruction**
```
Fix the regex /<.*>/ to return the HTML tag <h1> and not the text "<h1>Winter is coming</h1>". Remember the wildcard . in a regular expression matches any character.
```
**Code**
```
let text = "<h1>Winter is coming</h1>";
let myRegex = /<h.*?1>/; // Change this line
let result = text.match(myRegex);
```

### Find One or More Criminals in a Hunt

**Instruction**
Write a greedy regex that finds one or more criminals within a group of other people. A criminal is represented by the capital letter C.

**Code**
```
let reCriminals = /C+/; // Change this line
```
### Match Beginning String Patterns

To search or match patterns at the beginning of strings, we can use the caret character (^).

In the prior lesson, we have learned the caret character inside the character set(\[]), to create a negated character set in the form \[^thingsThatWillNotMatched]. Outside of the character set, the caret character is used to search for patterns at the beginning of strings

**Instructions**
Use the caret character in a regex to find Cal only in the beginning of the string rickyAndCal.

**Code**
```
let rickyAndCal = "Cal and Ricky both like racing.";
let calRegex = /^Cal/; // Change this line
let result = calRegex.test(rickyAndCal);
```

### Match Ending String Patterns

We can search the end of strings using the dollar sign character $ at the end of the regex

**Instruction**
Use the anchor character ($) to match the string caboose at the end of the string caboose.

**Code**
```
let caboose = "The last car on a train is the caboose";
let lastRegex = /caboose$/; // Change this line
let result = lastRegex.test(caboose);
```

### Match All Letters and Numbers

The closest character class in JavaScript to match the alphabet is \w. This shortcut is equal to \[A-Za-z0-9_]. This character class matches upper and lowercase letters plus numbers. Note, this character class also includes the underscore character (_).

**Instruction**
Use the shorthand character class \\w to count the number of alphanumeric characters in various quotes and strings.

**Code**
```
let quoteSample = "The five boxing wizards jump quickly.";
let alphabetRegexV2 = /\w/g; // Change this line
let result = quoteSample.match(alphabetRegexV2).length;
```

### Match Everything but Numbers and Letters

You've learned that you can use a shortcut to match alphanumerics `[A-Za-z0-9_]` using \w. A natural pattern you might want to search for is the opposite of alphanumerics.

You can search for the opposite of the `\w` with `\W`. Note, the opposite pattern uses a capital letter. This shortcut is the same as `[^A-Za-z0-9_]`.

**Instruction**

Use the shorthand character class \W to count the number of non-alphanumeric characters in various quotes and strings.

**Code**
```
let quoteSample = "The five boxing wizards jump quickly.";
let nonAlphabetRegex = /\W/g; // Change this line
let result = quoteSample.match(nonAlphabetRegex).length;
```

### Match All Numbers

The shortcut to look for digit characters is `\d`, with a lowercase d. This is equal to the character class `[0-9]`, which looks for a single character of any number between zero and nine.

**Instruction**
Use the shorthand character class `\d` to count how many digits are in movie titles. Written out numbers ("six" instead of 6) do not count.

**Code**

```
let movieName = "2001: A Space Odyssey";
let numRegex = /\d/g; // Change this line
let result = movieName.match(numRegex).length;
```

### Match All Non-Numbers

Using `\D`

**Instruction**
Use the shorthand character class for non-digits \D to count how many non-digits are in movie titles.

**Code**
```
let movieName = "2001: A Space Odyssey";
let noNumRegex = /\D/g; // Change this line
let result = movieName.match(noNumRegex).length;
```

### Restrict Possible Usernames

It is a tough step so far

**Instruction*

- Usernames can only use alpha-numeric characters.
- The only numbers in the username have to be at the end. There can be zero or more of them at the end. Username cannot start with the number.
- Username letters can be lowercase and uppercase.
- Usernames have to be at least two characters long. A two-character username can only use alphabet letters as characters.

**Code**

```
let username = "BadUs3rmr5";
let userCheck = /^[a-z][a-z]+\d*$|^[a-z]\d\d+$/i; // Change this line
let result = userCheck.test(username);

**Code Explanation**

^ - start of input
[a-z] - first character is a letter
[a-z]+ - following characters are letters
\d*$ - input ends with 0 or more digits
| - or
^[a-z] - first character is a letter
\d\d+ - following characters are 2 or more digits
$ - end of input
```

### Match Whitespace

You can search for whitespace using `\s`, which is a lowercase s. This pattern not only matches whitespace, but also carriage return, tab, form feed, and new line characters. You can think of it as similar to the character class `[ \r\t\f\n\v]`.

**Instruction**

Change the regex countWhiteSpace to look for multiple whitespace characters in a string.

**Code**
```
let sample = "Whitespace is important in separating words";
let countWhiteSpace = /\s/g; // Change this line
let result = sample.match(countWhiteSpace);
```

### Match Non-Whitespace characters

We can match non-whitespace characters using `\S`, s uppercase. This pattern will not match whitespace, carriage return, tab, form feed and new line characters. You can think of it being similar to the character class `[^ \r\t\f\n\v]`.

**Instruction**

Change the regex countNonWhiteSpace to look for multiple non-whitespace characters in a string.

**Code**
```
let sample = "Whitespace is important in separating words";
let countNonWhiteSpace = /\S/g; // Change this line
let result = sample.match(countNonWhiteSpace);
```

### Specify Upper and Lower Number of Matches

Recall the `+` sign is used to look for one or more characters adn the `*` sign to look for zero and more characters. These are convinient but sometimes we want to **match a certain range of pattern**.

Patterns: Quantity Specifier `{lower, upper}`

Example
```
\a{3, 5}h\

* To match only the letter a appearing between 3 and 5 times in a string ah
'aaah' true
'aah' false
'aaaaah' true
```

**Instruction**

Change the regex ohRegex to match the entire phrase Oh no only when it has 3 to 6 letter h's.

**Code**

```
let ohStr = "Ohhhhhhh no";
let ohRegex = /Oh{3,6} no/; // Change this line
let result = ohRegex.test(ohStr);

console.log({result})
```
----

### Specify Only The Lower Number of Matches

Patterns: Quantity Specifier `{lowerNumber,}`

Example
```
\ha{3,}h\

* To match only the letter a appering at least 3 times in a string hah
'haaah' true
'haah' false
'haaaah' true
```
**Instruction**

Change the regex haRegex to match the word Hazzah only when it has four or more letter z's.

**Code**
```
let haStr = "Hazzzzah";
let haRegex = /Haz{4,}ah/; // Change this line
let result = haRegex.test(haStr);
```

### Specify Exact Number of Matches

Patterns: Quantity Specifier `{number}`

Example
```
\ha{3}h\

*Match only the word hah with the letter a appears 3 times
'haaah' true
'haaaah' false
```

**Instruction**

Change the regex timRegex to match the word Timber only when it has four letter m's.

**Code**
```
let timStr = "Timmmmber";
let timRegex = /Tim{4}ber/; // Change this line
let result = timRegex.test(timStr);
```

### Check for All or None

Pattern: `?`

Example
```
\colou?r\

*Match the string color or colour (letter u can be appear after letter o or not)
'color' true
'colour' true
'coloar' false
```

**Instructions**

Change the regex favRegex to match both the American English (favorite) and the British English (favourite) version of the word.

**Code**
```
let favWord = "favorite";
let favRegex = /favou?rite/; // Change this line
let result = favRegex.test(favWord);

console.log({result})
```

### Positive and Negative Lookhead

There are two kinds of lookaheads: positive lookahead and negative lookahead.

A positive lookahead will look to make sure the element in the search pattern is there, but **won't actually match it**. A positive lookahead is used as (?=...) where the ... is the required part that is not matched.

On the other hand, a negative lookahead will look to make sure the element in the search pattern is not there. A negative lookahead is used as (?!...) where the ... is the pattern that you do not want to be there. The rest of the pattern is returned if the negative lookahead part is not present.

**Instruction**

Use lookaheads in the pwRegex to match passwords that are greater than 5 characters long, and have two consecutive digits.

**Code**
```
let sampleWord = "astronaut";
let pwRegex = /(?=\w{5,})(?=\D+\d\d)/; // Change this line
let result = pwRegex.test(sampleWord);
```

### Check For Mixed Grouping of Characters

Sometimes we want to check for groups of characters using a Regular Expression and to achieve that we use parentheses ().

If you want to find either Penguin or Pumpkin in a string, you can use the following Regular Expression: /P(engu|umpk)in/g

**Instruction**

Fix the regex so that it checks for the names of Franklin Roosevelt or Eleanor Roosevelt in a case sensitive manner and it should make concessions for middle names.

Then fix the code so that the regex that you have created is checked against myString and either true or false is returned depending on whether the regex matches.

**Code**
```
let myString = "Franklin Roosevelt";
let myRegex = /(Franklin|Eleanor)\s\w*\W*\s*Roosevelt$/; // Change this line
let result = myRegex.test(myString); // Change this line
// After passing the challenge experiment with myString and see how the grouping works

console.log({result, match: myString.match(myRegex)})
```
### Reuse Patterns Using Capture Groups

==Need to be relearn==

Reference
https://www.regular-expressions.info/anchors.html

### Use Capture Groups to Search and Replace

```
let wrongText = "The sky is silver.";
let silverRegex = /silver/;
wrongText.replace(silverRegex, "blue");
```

### Remove Whitespace from Start and End

```
let hello = "   Hello, World!  ";
let wsRegex = /^\s+|\s+$/g; // Change this line
let result = hello.replace(wsRegex, ''); // Change this line

console.log({result})
```

