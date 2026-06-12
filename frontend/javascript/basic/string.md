<details>
  <summary><b>Hand Note</b></summary>

```js

JavaScript string

const country = 'bangladesh';
const div = "kushtia";
const post = `kuala`;
const city = new String('vapee');//htis is an object type

console.log(city);
//we can not do div[1]='B';  because string is immutable

const sub = "ChemisTRy";
const book = "chemisTry";

console.log(sub == book);//false
console.log(sub.toLowerCase() === book.toLowerCase());//true
console.log(sub.toUpperCase() == book.toUpperCase());//true
//for string comparims we should use toUpperCase or toLowerCase methode


const sub1 = "water   ";
const sub2 = "        water   ";
console.log(sub1 === sub2);  //true
console.log(sub1.trim() === sub2.trim());//false
//trim() removes the white space from front and back area


const word = "howareyou";
console.log(word.slice(2, 5)); //war

const sen = "i do not like coding";
console.log(sen.split(" "));//[ 'i', 'do', 'not', 'like', 'coding' ]
console.log(sen.split('o'));//[ 'i d', ' n', 't like c', 'ding' ]
//split the string using cutting point and put into an array

const newarr = ['i', 'do', 'not', 'like', 'coding'];
console.log(newarr.join('-'));//i-do-not-like-coding
////join the array using cutting point and put into an string


//reverse string in three different way

const name = "donaltrump"
let reverse = "";
for (const ele of name)
{
    reverse = ele + reverse;
}
console.log(reverse);

//take forloop but start from last and use decremental

//shortcut
const gret = "highhowareyou";
let rev = gret.split("").reverse().join("");//we can only use reverse in array not in string
console.log(rev);
//split give letter by letter and put in a array--> as array so we can use reverse-->now join joins it and put in a string

```
</details>



# JavaScript Strings

## Concept Overview

A string in JavaScript represents a sequence of characters. Strings are immutable, meaning their content cannot be changed after creation. JavaScript provides multiple ways to create and manipulate strings.

## Key Principles
- Strings can be created using:
  - Single quotes `' '` 
  - Double quotes `" "`
  - Backticks `` ` `` (template literals)
  - `new String()` (creates a String object, not recommended)
- Strings are immutable → you cannot modify characters directly.
- String comparison is case-sensitive by default.
- Many built-in methods exist for manipulation (e.g., `toLowerCase()`, `trim()`, `slice()`, `split()`).

## Explanation

### 1. String Creation
```javascript
const country = 'bangladesh';
const div = "kushtia";
const post = `kuala`;
const city = new String('vapee'); // object type (not recommended)
```
`new String()` creates an object instead of a primitive string. Prefer primitive strings for performance and simplicity.

### 2. Immutability
```javascript
const str = "hello";
// str[1] = 'a'; ❌ not allowed
```
Strings cannot be modified directly. Any operation returns a new string.

### 3. String Comparison
```javascript
const sub = "ChemisTRy";
const book = "chemisTry";
console.log(sub == book); // false
console.log(sub.toLowerCase() === book.toLowerCase()); // true
console.log(sub.toUpperCase() === book.toUpperCase()); // true
```
Comparisons are case-sensitive. Normalize case using:
toLowerCase()
toUpperCase()


# String Manipulation in JavaScript

## 4. Trimming Whitespace
```javascript
const sub1 = "water   ";
const sub2 = "        water   ";

console.log(sub1 === sub2); // false
console.log(sub1.trim() === sub2.trim()); // true
```
*`trim()`* removes whitespace from both ends of a string. It does not affect spaces in the middle.

## 5. Extracting Substrings
```javascript
const word = "howareyou";
console.log(word.slice(2, 5)); // "war"
```
*`slice(start, end)`* extracts characters from `start` to `end-1`. The `start` index is inclusive, and the `end` index is exclusive.

## 6. Splitting Strings
```javascript
const sen = "i do not like coding";
console.log(sen.split(" ")); // ['i', 'do', 'not', 'like', 'coding']
console.log(sen.split('o')); // ['i d', ' n', 't like c', 'ding']
```
*`split(delimiter)`* converts a string into an array based on the delimiter.we have to use a variable to store the output

## 7. Joining Arrays into Strings
```javascript
const newarr = ['i', 'do', 'not', 'like', 'coding'];
console.log(newarr.join('-')); // "i-do-not-like-coding"
```
*`join(delimiter)`* converts an array into a string with elements separated by the delimiter. we have to use a variable to store the output

## 8. Reversing a String
### Method 1: Manual Loop
```javascript
const name = "donaltrump";
let reverse = "";
for (const ch of name) {
    reverse = ch + reverse;
}
console.log(reverse);
```
does a manual reversal by prepending each character.

### Method 2: Built-in Methods
```javascript
const gret = "highhowareyou";
let rev = gret.split("").reverse().join("");
console.log(rev);
```
depends on splitting the string into an array, reversing it, then joining back into a string.
does only work with arrays for reversal.

Note: reverse function only can be use in an array not in string.
Note:we can split a strin g not an array
Note: we can join an array not a string



# Step-by-Step Logic (Reverse Using Built-in)

- Convert string → array using `split("")`
- Reverse array using `reverse()`
- Convert back → string using `join("")`

## Important Notes / Edge Cases

### `new String()` vs primitive string:

- `typeof "abc"` // "string"
- `typeof new String()` // "object"

**Avoid object form.**

- `slice()` does not modify original string.
- `trim()` only removes leading and trailing spaces.

## Common Mistakes

- Assuming strings are mutable:
  - ```js
    str[0] = 'A'; // ❌
    ```
- Forgetting case sensitivity in comparison.
- Using `reverse()` directly on string:
  - ```js
    "abc".reverse(); // ❌
    ```
- Incorrect expectation with whitespace comparison.

## Key Takeaways

- Strings are immutable.
- Use primitive strings instead of `new String()`.
- Normalize case before comparison when needed.
- Use `split()` and `join()` for conversions between string and array.
- Many string operations return new values, not modify original.
