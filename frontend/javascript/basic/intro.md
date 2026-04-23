# JavaScript Fundamentals: Core Concepts and Runtime Behavior

## Concept Overview

JavaScript is a high-level, dynamically typed programming language primarily used to build interactive web applications. It runs in browsers and environments like Node.js.

## Key Principles
- **High-level:** Abstracts low-level memory management.
- **Dynamically typed:** Variable types are determined at runtime.
- **Single-threaded with event loop** (in most environments).
- **Interpreted** (but modern engines use Just-In-Time compilation internally).

## Compiler vs Interpreter
### Interpreter
- Executes code line by line.
- Translates and runs code at runtime.
- Easier debugging, slower execution compared to compiled languages.

### Compiler
- Translates entire code into machine code before execution.
- Produces an optimized version of the program.

## JavaScript Reality
JavaScript engines (like V8 in Chrome/Node.js) use a mix:
- Parse → interpret → optimize using JIT (Just-In-Time compilation).
- So JavaScript is not purely interpreted or compiled.

## Running JavaScript in VS Code (Node.js Setup)
### Steps (macOS)
1. **Install Homebrew**
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
2. **Add to PATH**
echo 'eval "$(/opt/homebrew/bin/brew shellenv zsh)"' >> ~/.zprofile
eval '"$(/opt/homebrew/bin/brew shellenv zsh)"'
3. **Install Node.js**
brew install node
4. **Verify**
node -v
npm -v
5. **Run JS file**
node filename.js
### Key Points
- Node.js allows running JavaScript outside the browser.
- npm is included with Node.js.
- Restart terminal if node is not recognized.



# Variables in JavaScript

## Types of Declarations
```javascript
var num = 5;
let count = 10;
const PI = 3.14;
```
| Keyword | Scope     | Reassignable | Notes                     |
|---------|-----------|--------------|---------------------------|
| var     | Function  | Yes          | Avoid in modern JS      |
| let     | Block     | Yes          | Preferred                 |
| const   | Block     | No           | Must be initialized       |

## Naming Conventions
- **camelCase** → `myNameIs` (standard in JS)
- **snake_case** → `my_name_is`
- **PascalCase** → `MyNameIs` (used for classes)

## Type Checking
```javascript
var num = 5;
console.log(typeof num); // "number"
```

## Type Conversion
### String to Number
```javascript
parseInt("10");     // 10
parseFloat("10.5"); // 10.5
```
### Invalid Conversion
```javascript
parseInt("ten"); // NaN
```
**NaN (Not a Number)**
isNaN("123"); // false
isNaN("abc"); // true
isNaN(true);  // false (true → 1)
> Note: isNaN() coerces values before checking, which can be confusing.

## String and Number Behavior
### Addition (Special Case)
```javascript
console.log(5 + "10"); // "510"
```
> If one operand is a string → concatenation happens.



# Mixed Operations

```javascript
console.log(20 - "5"); // 15
console.log("5" - 15); // -10
console.log("5" * 5);  // 25
console.log(20 / "2"); // 10
```

**Note:** JS converts strings to numbers for `-`, `*`, `/`.

## Floating Point Precision Issue
```javascript
var total = 0.1 + 0.2;
console.log(total); // 0.30000000000000004
```
**Fix:**
```javascript
console.log(total.toFixed(2)); // "0.30"
```
*Note:* `toFixed()` returns a string.

## Infinity in JavaScript
```javascript
console.log(30 / 0);  // Infinity
console.log(-30 / 0); // -Infinity
```

## Expression Evaluation Order
```javascript
to console:
console.log(2 + 4 + 19 + 3 + "000000000" + 5 + 4);
// "2800000000054"
```
### Explanation:
- Numbers are added first → results in `28`
- Then a string is encountered → everything becomes string concatenation.

## Important Notes / Edge Cases
- JavaScript uses type coercion heavily.
- `NaN` is a special numeric value.
- Floating point arithmetic is not precise.
- Using `var` should generally be avoided in modern code.

## Common Mistakes
- Assuming `isNaN()` checks without conversion.
- Mixing string and number unintentionally.
- Forgetting that `toFixed()` returns a string.
- Using `var` instead of `let`/`const`.

## Key Takeaways
- JavaScript is high-level and dynamically typed.
- It uses both interpretation and JIT compilation.
- Type coercion is a critical concept to understand.
- String and number operations behave differently depending on context.
- Floating-point precision issues are normal in JavaScript.
