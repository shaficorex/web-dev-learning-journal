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
*`split(delimiter)`* converts a string into an array based on the delimiter.

## 7. Joining Arrays into Strings
```javascript
const newarr = ['i', 'do', 'not', 'like', 'coding'];
console.log(newarr.join('-')); // "i-do-not-like-coding"
```
*`join(delimiter)`* converts an array into a string with elements separated by the delimiter.

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
