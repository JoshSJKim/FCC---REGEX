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

## Ignore Case While Matching

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
