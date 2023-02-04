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
'string.match(/regex/);
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
let exampleStr = "Let's have fund with regular expressions!";
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
