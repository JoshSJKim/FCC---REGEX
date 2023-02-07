# FCC---REGEX

Regular Expressions

- Regular expressions (regex) are used in programming languages to match parts of strings.
- It is a sequence of characters that define a search pattern.
- It is used to check if a string contains specified patters, or to find and replace parts of a string that match the pattern.
- Regex can be used in various programming languages to perform pattern matching and manipulation

## Using the Test Method

- If you want to find the word 'the' in this current sentence, ````/the/``` can be used as the regular expression.
- ```""``` quotation marks are not required within the regular expression.

- One way of testing the regex is the ```.test()``` method.
  - It applies the regex to a string variable (passed in the parentheses).
  - It then returns ```true``` or ```false``` based on the test results.

```js
let myString = "Hello, World!";
let myRegex = /Hello/;
let result = myRegex.test(myString);    // This is the .text() method

console.log(myRegex.test(myString));    // console will display 'true'
```

## Match Literal Strings

- ```.test()``` method uses strict equality
- /Hello/ does not match /hello/ or /HELLO/
- There is another method to match other forms of regex. It will be covered later.

```js
let waldoIsHiding = "Somewhere Waldo is hiding in this text.";

let wrongRegex = /WALDO/;
let waldoRegex = /Waldo/;

wrongRegex.test(waldoIsHiding);
waldoRegex.test(waldoIsHiding);

console.log(wrongRegex.test(waldoIsHiding));    // console will display 'false'
console.log(waldoRegex.test(waldoIsHiding));    // console will display 'true'
```

## Match a Literal String with Different (multiple) Possibilities

- You can search for multiple patterns using regex to match literal strings.
- This is done by using the 'alteration' or the ```OR(|)``` operator.

```js
let petString = "James has a pet cat.";
let petRegex = /dog|cat|bird|fish/;     // This is the 'alteration'
let result = petRegex.test(petString);

console.log(petRegex.test(petString));  // console will display 'true'
```

## Ignore Case While Matching (i)

- Case, referring to upper or lower case letters.
- Previously, ```.test()``` method example used strict equality when matching.
- Regex can be matched, regardless of its letter case using what is called a 'flag'.
- There are other flags, but this example uses a flag that ignores cases.
- The ```i``` flag. It is used by adding it to the end of the regex.
- For example ```/ignorecase/i```
- Using this method matches strings, regardless of its letter casing.

```js
let myString = "freeCodeCamp";
let fccRegex = /FreECoDecAmP/i;         // This is the ignore case flag
let result = fccRegex.test(myString);

console.log(fccRegex.test(myString));   // console will display 'true'
```

## Extract Matches

- Now, to extract the matches identified using the test method.
- I find the terminology slightly confusing. But not a problem.
  - ```.test()``` method is used to 'match' or identify the existence of patterns/strings
  - ```.match()``` method is used to 'extract' the string.

- To use the ```.match()``` method, apply the method on (after) a string and pass the regex in the parentheses.

```js
"Hello, World!".match(/Hello/); // This would return "Hello"
```

or to break it down by assigning variables,

```js
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);         // This would return "expressions
```

The .match syntax exactly the opposite of the .test syntax

```js
'string'.match(/regex/);
/regex/.test('string');
```

## Find more than the first match (g)

So far, the .test and .match method allows for only a single search pattern.

```js
let twinkleStar = "Twinkle, twinkle, little star";
let starRegex = /twinkle/;
twinkleStar.match(starRegex);        // .match would return the second ["twinkle"] because it uses strict equality
```

Use the global search flag (g) to extract a pattern multiple times.
NOTE: Multiple flags may be applied on the regex. For example ```/search/gi```

```js
let twinkleStar = "Twinkle, twinkle, little star";
let starRegex = /twinkle/ig;
twinkleStar.match(starRegex);     // .match would return ["Twinkle", "twinkle"]
```

## Match anything with Wildcard Period (.)

The wildcard character ```.``` will match any one character in a pattern.
It is also called 'dot' or 'period'.
It can be used to represent any character in a pattern, or a word in a string.

For example,

```js
let exampleStr = "Let's have fun with regular expressions!";
let unRegex = /.un/;                       // the '.' represents any character. It will match any words or patterns ending in 'un'
let result = unRegex.test(exampleStr);     // console would display 'true'
```

## Match Single Character with Multiple Possibilities ([])

- The module covered literal patterns (/literal/) and wildcard character (.), which are the extremes of regular expressions.
- literal pattern method finds exact matches and the wildcard method matches everything.
- Add some flexibility in the search with 'character classes'.
- It allows you do define a group of characters you wish to match by placing the specific characters inside square brackets ([]).

```js
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);      // ["big"]
bagStr.match(bgRegex);      // ["bag"]
bugStr.match(bgRegex);      // ["bug"]
bogStr.match(bgRegex);      // null
```

### Exercise ([])

Use a character class with vowels (a, e, i, o, u) in your regex vowelRegex to find all the vowels in the string quoteSample.
Note: Be sure to match both upper- and lowercase vowels.

```js
let quoteSample = "Beware of bugs in teh above code; I have only proved it correct, not tried it";
/* Include all vowels wrapped in '[]' in the regex. The vowels do not need to be separated with commas.
Also, it should include the global search flag to find repeating vowels, 
as well as the ignore letter casing flag to find both upper and lower case vowels.*/
let vowelRegex = /[aeiou]gi/;
// Apply the .match method on the 'quoteSample' and pass 'vowelRegex' in the parentheses
let result = quoteSample.match(vowelRegex);

console.log(quoteSample.match(vowelRegex)); 
// Console will display all 25 vowels identified in the string
```

## Match Letters of the Alphabet (range of characters)

- Instead of having to specify each character you wish to match as shown in the previous exercise, a range of characters can be specified using the hyphen (-).

```js
let catStr = "cat";
let batStr = "bat";
let matStr = "mat";
let bgRegex = /[a-e]at/;    
catStr.match(bgRegex);      // ["cat"]
batStr.match(bgRegex);      // ["bat"]
matStr.match(bgRegex);      // null
```

### Exercise ([-])

Match all the letters in the string quoteSample.

```js
let quoteSample = "The quick brown fox jumps over the lazy dog.";
/* Use '-' to cover the entire range of the alphabet.
Also, include global search flag to include repeating characters, 
as well the ignore letter casing flag to include upper and lowercase characters */
let alphabetRegex = /[a-z]/ig;
// Apply the .match method on the 'quoteSample' and pass 'alphabetRegex' in the parentheses
let result = quoteSample.match(alphabetRegex);

console.log(quoteSample.match(alphabetRegex)); //Console will display all the characters present in the string in sequence
```

## Match Letters and Numbers of the Alphabet

- Using the hyphen ```-``` works not only with matching a range of characters; it also works with range of numbers.
- Range of numbers specified are inclusive of the numbers entered, i.e /[0-9]/ includes the number '0' and '9'.
- It is also possible to combine both a range of number and characters in a single character class/set.

```js
let jennyStr = "Jenny8675309";
let myRegex = /[a-z0-9]ig;      // The flags will match all upper and lowercase alphabets as well as repeating numbers and characters
jennyStr.match(myRegex);        // Notice that the character range and number range are not separated with a comma
```

### Exercise ([a-z0-9])

Create a single regex that matches a range of letters between h and s, and a range of numbers between 2 and 6. Remember to include the appropriate flags in the regex.

```js
let quoteSample = "Blueberry 3.141592653s are delicious."
// Specify character range from 'h' to 's' and numbers '2' to '6'
// Remember to include appropriate flags
let myRegex = /[h-s2-6]/ig;
let result = quoteSample.match(myRegex);

console.log(quoteSample.match(myRegex));
// console will display all (repeating, upper and lowercase) characters and numbers applicable to the range specified
```

## Match Single Characters Not Specified (Negated Character Sets)

- It is also possible to create a character set to exclude the specified characters from the result.
- This is called 'Negated Character Set'
- To create a negated character set, enter a caret (^) after the opening bracket and before the characters you want excluded.

### Exercise (/[^]/)

Create a single regex that matches all characters that are not a number or a vowel. Remember to include the appropriate flags in the regex.

```js
let quoteSample = "3 blind mice.";
// Create a negated character set using (^) to specify vowels and numbers to exclude from the result.
// Remember to include appropriate flags
let myRegex = /[^aeiou0-9]/ig;    // Again, note that the range of characters and range of numbers do not need to be separated.
let result = quoteSample.match(myRegex);

console.log(quoteSample.match(myRegex));
// Console will display [ ' ', 'b', 'l', 'n', 'd', ' ', 'm', 'c', '.' ]
// Notice that the result returns white spaces, as well as special characters.
```

## Match Consecutive Characters

- Sometimes it is necessary to match a character (or a group of characters) that appear one or more times consecutively.
- Use the '+' character to check for such cases. Note that it only looks for consecutive characters.
  
- The syntax is ```/a+/g```
- Note that it has the global search flag to look for repeating characters.
- Also note that the pattern inside the forward slash are not enclosed in square brackets.

```js
let testStr1 = "abcd";
let testStr2 = "aabc";
let testStr3 = "abac";
let testStr4 = "bcde";
let testRegex = /a+/g;      // This is the syntax.
                            // Ignore letter casing flag (i) can also be added to look for consecutive upper and lowercase characters
testStr1.match(testRegex);  // ["a"]    Note that it also matches single instances of 'a'
testStr2.match(testRegex);  // ["aa"]
testStr3.match(testRegex);  // ["a", "a"] It also looks for repeating instances of single 'a'
testStr4.match(testRegex);  // null
```

### Exercise (/a+/g)

You want to find matches when the letter s occurs one or more times in Mississippi. Write a regex that uses the + sign.

```js
let difficultSpelling = "Mississippi";
// Use the '+' method to match match consecutive 's' in the string.
// Remember to include the global search flag.
let myRegex = /s+/g;
let result = difficultSpelling.match(myRegex);

console.log(difficultSpelling.match(myRegex));
// console will display ["ss", "ss"]
```

## Match Characters that Occur Zero or More Times

- There is a way to match characters that occur zero or times.
- Similar to the use of '+' in the previous exercise, use the asterisk '*' to look for specified character that repeat zero or more times.

```js
let soccerWord = "gooooooooal!";
let gPhrase = "gut feeling";
let oPhrase = "over the moon";
let goRegex = /go*/;        // Notice the pattern is not enclosed in square brackets

soccerWord.match(goRegex);  // ["goooooooo"]
gPhrase.match(goRegex);     // ["g"]
oPhrase.match(goRegex);     // null
```

### Exercise (/Aa*/)

Create a regex chewieRegex that uses the * character to match an uppercase A character immediately followed by zero or more lowercase a characters in chewieQuote.

```js
let chewieQuote = "Aaaaaaaaaaaaaaaarrrgh!";
// Use the '*' method to find one uppercase 'A' and repeating lowercase 'a'
// Do not use any flags
let chewieRegex = /Aa*/;
// I think '/A*/i;' or '/a*/i;' would achieve the same result, but I guess that's not the point of this exercise.
let result = chewieQuote.match(chewieRegex);

console.log(chewieQuote.match(chewieRegex));
//console will display ["Aaaaaaaaaaaaaaaa"]
```

## Greedy Matching and Lazy Matching

- Regular expressions are by default 'greedy'.
- It means that it finds the longest possible part of a string that fits the specified regex pattern.
- The opposite of 'greedy' is 'lazy'.
- It means that if finds the smallest possible part of the string that satisfies the specified regex pattern.

### Greedy (Includes all possible matches)

```/t[a-z]*i/;```

The above regex pattern looks for a string that begins with 't' and ends with 'i'.
In between the 't' and 'i' can be zero or more lowercase letters between 'a' and 'z'.

If the above regex pattern is applied to a variable defined as "titanic", it would return the following

```js
let myStr = "titanic";
let myRegex = /t[a-z]*i/;
let result = myStr.match(myRegex); 
// it would return ["titani"]. It finds the longest possible sub-string that matches against the original string.
```

### Lazy (Excludes all possible matches)

Lazy matching can be achieved by using the '?' character.

```/t[a-z]*?i/;```

The above regex pattern is the exact opposite of the 'greedy' regex pattern.
It will look for a string that begins with 't' and ends with 'i'.
In between 't' and 'i' can be zero or more lowercase letters between 'a' and 'z',
and by adding '?', it will exclude all matched patterns.

So, if the above regex pattern is applied to a variable defined as "titanic", it would return the following

```js
let myStr = "titanic";
let myRegex = /t[a-z]*?i/
let result = myStr.match(myRegex);
/* The above would return ["ti"]. 
It looks for all of the lowercase letters from 'a' to 'z' found between the first 't' and last 'i' of the given string "titanic".
Then the '?' will exclude all matched patterns and return the result.*/
```

### Exercise (Lazy Matching ```*?```)

Fix the regex /<.*>/ to return the HTML tag ```<h1>``` and not the text ```"<h1>Winter is coming</h1>"```.
Remember the wildcard . in a regular expression matches any character.

```js
let text = "<h1>Winter is coming</h1>";
let myRegex = /<.*>/;
let result = text.match(myRegex);
```

- Let's see what's happening in the above snippet.
  - Variable 'text' is assigned with an HTML string ```"<h1>Winter is coming</h1>";```
  - The regex pattern is defined as ```/<.*>/;
    - This means that the result string should begin with a '<' and end with a '>'
    - The '.' is a wildcard and could represent anything.
    - the '*' behind the wildcard specifies zero or more number of any characters.
  - Therefore, the result should return a string that begins with '<' and end with '>' with any characters in between that are found in the original string.
- In this case, it would return ```"<h1>Winter is coming</h1>"```

In order to return only the opening tag ```"<h1>"```, the regex pattern needs alteration.

I am having a bit of trouble understanding the logic behind this.

I know the answer to this exercise so let's unpack that first.

```js
let text = "<h1>Winter is coming</h1>;
let myRegex = /<.*?>/;
let result = text.match(myRegex);       // It would return ["<h1>"]
```

So the above is the correct answer.

BUT

If ```/<.*>/``` provided in the original challenge includes all characters between the first '<' and last '>',
shouldn't ```/<.*?>/``` EXCLUDE all characters between the first '<' and last '>' to return ["<>"]?
(It is in fact the shortest possible string to be returned when compared to the original string)

OR

Does ```/<.*?>/``` terminate the iteration at the first sight of the character '>'?
Meaning that it doesn't even bother iterating through the entire string. Hence, LAZY matching.
If this is the case, it makes sense.

I even tried the following and the challenge passed.

```js
let myRegex = /<..>[a-z]*?/;
```

- ```<..>``` matches any two characters inside the opening tag, which would return ```"<h1>"```
- ```[a-z]*?``` matches any text inside the HTML tag and excludes it from the return value.
- Since the '<' is not a part of the alphabet character, it will stop iteration and terminate matching the pattern.
- So, the result return value would be ```"<h1>"```
- But, this seems inefficient.

It looks like there are many ways to make this challenge pass

Even this works

```js
let myRegex = /<..>>*?/;
```

But passing the challenge and understanding the logic is a different thing.

### Greedy vs. Lazy

Now I understand why it's called greedy and lazy.

Greedy, being greedy, will iterate through as much of the given string as possible to satisfy the regex pattern.

Whereas

Lazy, being lazy, will iterate through as little of the given string as possible to return the shortest possible string that still satisfies the regex pattern.

So, ```/<.*?>/``` will stop matching the regex pattern at the first sight of '>'. Which will return ```<h1>```

## Find the Criminals challenge

Write a greedy regex that finds one or more criminals within a group of other people.
A criminal is represented by the capital letter C.

- Remember, it's a greedy regex pattern. Regex is greedy by default, unless specified 'lazy'.
- One or more criminals 'C' within a group of other people (other characters)
- Ignore letter casing flag shouldn't be used since we're looking for capital 'C'
- However, global search flag should be applied since we want to find all recurring 'C'
- We want to find consecutive 'C' in a group, as well as single 'C' in a group. So use the '+'

- ```let reCriminals = /./;``` This is the original challenge

```js
let reCriminals = /C+/g; // The solution
```

## Match Beginning String Patterns (/^/)

Previously, the caret (^) character was used within a character set (/[^aeiou0-9]/) to create a negated character set, which are characters that are specified to be excluded from the match pattern.
It serves a different purpose when it is used without a character set.
It is used to search for patterns at the beginning of strings.

Use the caret character in a regex to find Cal only in the beginning of the string rickyAndCal.

```js
let rickyAndCal = "Cal and Ricky both like racing";
// If you use the syntax below to search for Ricky (/^Ricky/), it will return 'false' because 'Ricky' is not at the beginning of the string
let calRegex = /^Cal/;
let result = calRegex.test(rickyAndCal);
// The result will return 'true'
```

## Match Ending String Patterns (/$/)

Opposite to the previous exercise, there is a way to search for ending string patterns.
The caret (^) was place prior to the regex to search for the beginning string patterns.
Use the anchor character ($) after the regex to search for ending string patterns.

Use the anchor character ($) to match the string caboose at the end of the string caboose.

```js
let caboose = "The last car on a train is the caboose";
/* Same rule applied on the previous exercise applies here as well. 
The '$' method will only search for the specified pattern at the end of the string*/
let lastRegex = /caboose$/;
let result = lastRegex.test(caboose);
// The result will return 'true'
```

## Match All Letters and Numbers

- There is a regex pattern shortcut to match all letters (upper and lowercase), as well as numbers and the underscore (_)
- This is referred to as the 'alphanumeric characters'.
- The shorthand syntax and its longhand equivalent is shown below

```/\w/; = /[A-Za-z0-9_];```

### Exercise (/\w/)

Use the shorthand character class \w to count the number of alphanumeric characters in various quotes and strings.

```js
let quoteSample = "The five boxing wizards jump quickly";
/* Use the 'match-all' shorthand (/\w/) to match all alphanumeric characters.
Apply the global search flag to match recurring characters.*/
let alphabetRegexV2 = /\w/g;
let result = quoteSample.match(alphabetRegexV2).length; // It will return '31'
```

## Match Everything but Letters and numbers

The previous exercise used the shorthand ```/\w/``` to search for alphanumeric characters.
The opposite is ```/\W/``` (notice the capital 'W') which is used to search for everything EXCEPT alphanumeric characters.
The longhand for the above shorthand is ```[^A-Za-z0-9_]```

```js
let shortHand = /\W/;
let numbers = "42%";
let sentence = "Coding!";
numbers.match(shortHand);   // Result would return '%'
sentence.match(shortHand);  // Result would return '!'
```

### Exercise (/\W/)

Use the shorthand character class \W to count the number of non-alphanumeric characters in various quotes and strings.

```js
let quoteSample = "The five boxing wizards jump quickly.";
// Use the shorthand (/\W/) to search for all non-alphanumeric characters
// Remember to use the global search flag (g) to match all recurring characters.
let nonAlphabetRegex = /\W/g;
let result = quoteSample.match(nonAlphabetRegex).length;  // Result would return '6'

// Note that spaces between words are counted as non-alphanumeric character
console.log(quoteSample.match(nonAlphabetRegex));
// console will display [ ' ', ' ', ' ', ' ', ' ', '.' ]
```

## Match All Numbers

Another common shortcut for string pattern is digits or numbers.
The shorthand is \d with a lowercase 'd'
The longhand, or character class is [0-9], which looks for a single character of any number between zero and nine.

### Exercise (/\d/)

Use the shorthand character class \d to count how many digits are in movie titles.
Written out numbers ("six" instead of 6) do not count.

```js
let movieName = "2001: A Space Odyssey";
// Apply the same logic as the previous exercises.
// Remember to include the global search flag.
let numRegex = /\d/g;
let result = movieName.match(numRegex).length;
// Result would return '4'
```

## Match All Non-Numbers

To search for all non-numbers as opposed to the previous exercise,
use \D with an uppercase D. The longhand equivalent is ```[^0-9]```,
which looks for a single character that is not a number between zero and nine.

### Exercise (/\D/)

Use the shorthand character class for non-digits \D to count how many non-digits are in movie titles.

```js
let movieName = "2001: A Space Odyssey";
// I shouldn't have to explain this again
let noNumRegex = /\D/g;
let result = movieName.match(noNumRegex).length;
// Result would return '17'.
// Note that spaces between characters are also counted.
```

## Restrict Possible Usernames (Challenge)

NOTE: Do not confuse negated character sets with matching beginning of character sets
``` /^/ !== /[^]/ ```

Usernames can only use alpha-numeric characters.
The only numbers in the username have to be at the end.
There can be zero or more of them at the end.
Username cannot start with the number.
Username letters can be lowercase and uppercase.
Usernames have to be at least two characters long.
A two-character username can only use alphabet letters as characters.

Break it down

- It can only use alphanumeric characters. ``` /[a-zA-Z]\d/ ``` should cover that.
- Throw in a ignore letter casing flag (i) to make it case insensitive.
- Numbers in the username have to be at the end. ``` \d$ ```
- There can be zero or more numbers. ``` \d*$ ``` This means that the username and can, or may not end with numbers.
- It cannot start with a number. ``` /^[a-z]/i; ``` This ensures that it begins with a lower or uppercase letter.
- Username has to be at least two characters long. ``` /^[a-z][a-z]+/ ``` This ensures that the first character is a letter, followed by one or more letters.

Put it together

``` /^[a-z][a-z]+\d*$/i: ```

- The first character is a letter, case insensitive due to the (i) flag at the end.
- It is followed by one or more case insensitive letters.
- It ends with zero or more numbers at the end.
- Thus ensuring that if the username consists of two characters, it is both letters.

I ran this through the editor and it failed.
The second character can be a number if the username is longer than two characters. (ex. A74)

Looked through the notes and realized I could use the OR(|) operator to add another pattern.
I just need to come up with a pattern that satisfies something like 'A74'

- It still has to start with a case insensitive letter and may or may not end with a number.
- But if the second character is a number, ONE OR MORE number should follow.
  
  ``` /^[a-z][0-9]\d+$/i ```

- This ensures that the first character is a case insensitive letter
- The second character is a number.
- Which is followed by one or more numbers at the end.

So, put it together again.

```/^[a-z][a-z]+\d*$|^[a-z][0-9]\d+$/i;```

And the pattern passes.
Later I realized that '[0-9]` can be replaced with '\d'

```js
let username = "JackOfAllTrades";
let userCheck = /^[a-z][a-z]+\d*$|^[a-z]\d\d+$/i;
let result = userCheck.test(username);
```

## Match Whitespace

- You can use a regex pattern to search for white spaces in a string.
- White spaces include carriage return, tab, form feed, and new line characters [ \r\t\f\n\v]

The basic application of this regex is the same as the other shorthand regex patterns.
I won't bother explaining the details.

```js
let sample = "Whitespace is important in separating words";
let countWhiteSpace = /\s/g;
let result = sample.match(countWhiteSpace);
// Result would return [ ' ', ' ', ' ', ' ', ' ' ]
console.log(sample.match(countWhiteSpace).length);
// console will display '5'
```

## Match Non-Whitespace Characters

This should be self-explanatory now.
The syntax is '\S'
It will match anything other than white spaces.

```js
let sample = "Whitespace is important in separating words";
let countNonWhiteSpace = /\S/g;
let result = sample.match(countNonWhiteSpace).length;
// console will display '38'
```

## Specify Upper and Lower Number of Matches (Quantifier)

- '+' allows you to search for one or more characters
- '*' allows you to search for zero or more characters
- You can use '{}' specify a range of numbers. This is a 'Quantity Specifier'
- Specify two numbers in the braces to represent the lower and upper number of patterns

Example

```js
let A4 = "aaaah";
let A2 = "aah";
let multipleA = /a{3,5}h/; // This will test if the string has 3-5 'a's.
multipleA.test(A4);        // true
multipleA.test(A2);        // false
```

- The quantifier should be placed immediately after the character you wish to apply the quantifier to.
- NOTE: If there are multiple words with space in between the string, it is necessary to specify the white space in the regex pattern.

### Exercise (/{}/)

Change the regex ohRegex to match the entire phrase Oh no only when it has 3 to 6 letter h's.

```js
let ohStr = "Ohhh no";
let ohRegex = /Oh{3,6}\sno/;      // \s used to specify the white space between "Oh" and "no"
let result = ohRegex.test(ohStr); // Result would return 'true'
```

## Specify only Lower Number of Matches

You can specify only the lower number of patterns without an upper limit.
Keep the same syntax with the first number representing the lower limit followed by a comma.

For example

```js
let A4 = "haaaah";
let A2 = "haah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleA = /ha{3,}h/;    // This pattern will match strings with 3 or more 'a' without an upper limit.
multipleA.test(A4);           // true
multipleA.test(A2);           // false
multipleA.test(A100);         // true
```

### Exercise (/{x,}/)

Change the regex haRegex to match the word Hazzah only when it has four or more letter z's.

```js
let haStr = "Hazzzzah";
let haRegex = /Haz{4,}ah/;
let result = haRegex.test(haStr);
```
