# JavaScript Functions

## Concept Overview

A function in JavaScript is a reusable block of code designed to perform a specific task. Functions can accept inputs (parameters), process them, and optionally return a result.

## Key Principles
- Functions are declared using the `function` keyword.
- Parameters allow passing data into a function.
- A function may or may not return a value.
- JavaScript is dynamically typed, so parameter types are not declared.
- Functions can accept any type of data: numbers, strings, arrays, objects, etc.
- JavaScript provides a special `arguments` object inside regular functions.

## Explanation

### Function Declaration and Call
A function is defined once and can be executed multiple times.

```javascript
function startFan() {
    console.log("stand up");
    console.log("walk towards switch");
    console.log("press switch");
}
// function call
startFan();
```

### Function with Parameters and Return Value
```javascript
function add(num1, num2) {
    return num1 + num2;
}
console.log(add(56, 34));
```
* `num1` and `num2` are parameters.
* The function returns the sum using `return`.
* The returned value can be used or printed.



# Passing Arrays (or Other Types)

```javascript
function lenArray(arr) {
    return arr.length;
}

console.log(lenArray([12, 3, 44, 54, 5]));
```

Functions can accept arrays, objects, strings, etc.
Here, the function returns the length of the array.

## Default Return Value

If a function does not explicitly return a value, it returns `undefined`.

```javascript
function test() {}

console.log(test()); // undefined
```

## Input Validation

```javascript
function addNums(n1, n2) {
    if (typeof n1 !== "number" || typeof n2 !== "number") {
        console.log("please provide a number");
        return; // ensures function exits
    }
    return n1 + n2;
}

const out = addNums("two", 7);
console.log(out);
```
* `typeof` is used to validate input types.
* Always `return` after invalid input to avoid unexpected behavior.

## The Arguments Object

```javascript
function arrayObj(n1, n2) {
    console.log(n1, n2);
    console.log(arguments);
}

arrayObj(34, 29, 3, 45, 6, 7, 8, 9, 3);
```
* `arguments` is an array-like object containing all passed arguments.
* It is **not** a real array (no array methods like `map`, `filter`).
* Works only in regular functions (not in arrow functions).

### Example structure of `arguments`:
| Key | Value |
defaults to:
dictionary with keys `'0'`, `'1'`, `'2'`, etc., corresponding to argument positions.



# Step-by-Step Logic (Example: add function)

- **Function is declared with parameters** `num1` and `num2`.
- **When called**, values are passed into parameters.
- The function executes `num1 + num2`.
- **Result is returned**.
- **Caller receives and uses the result**.

## Important Notes / Edge Cases

- Missing arguments become `undefined`.
- Adding non-numbers may result in string concatenation or `NaN`.
- Always validate input in critical functions.
- `arguments.length` gives the number of passed arguments.

## Common Mistakes

- Not using `return` when a value is expected.
- Assuming `arguments` is a real array.
- Forgetting input validation.
- Using arrow functions and expecting arguments to exist.

## Key Takeaways

- Functions improve code reuse and structure.
- Parameters allow flexible input handling.
- `return` controls output from a function.
- Input validation prevents runtime errors.
- `arguments` allows handling variable inputs but has limitations.
