# JavaScript Conditional Logic and Comparison

## Concept Overview

Conditional logic in JavaScript controls the flow of execution based on boolean expressions. This includes `if...else`, `else if`, nested conditions, the ternary operator, and logical operators such as `&&`, `||`, and `!`.

## Key Principles
- Conditions evaluate to true or false.
- Code blocks execute only when conditions are satisfied.
- Use strict comparison (`===`, `!==`) to avoid type coercion issues.
- Logical operators combine multiple conditions.

## Explanation

### 1. if...else Condition
Executes one block if the condition is true, otherwise executes another.

```javascript
const sal = 200;
const h = 60;
const hasCar = false;
const hasBcs = true;

if ((sal > 100 && h > 65) || (hasCar === true && hasBcs === true)) {
    console.log("kobul");
} else {
    console.log("not kobul");
}
```
**Logic:**
- `(sal > 100 && h > 65)` → both must be true
- `(hasCar === true && hasBcs === true)` → both must be true
- If either group is true → overall condition is true

### 2. if...else if...else
Used when multiple conditions need to be checked in sequence.

```javascript
def condition1():
    // runs if condition1 is true
elif condition2():
    // runs if condition1 is false and condition2 is true
else:
    // runs if all conditions are false
```
(Note: The last code snippet appears to be a pseudocode; replace with actual JavaScript syntax as needed.)


# 3. Nested if

An if statement inside another if.

```javascript
if (true) {
    if (false) {
        console.log("inner");
    } else {
        console.log("nested else");
    }
}
```

# 4. Ternary Operator

Short form of `if...else` for single expressions.

```javascript
let price = 30;
(price > 20) ? console.log("hi") : console.log("bye");
```

# 5. Ternary with Assignment

```javascript
let price = 30;
let isLeader = true;

price = isLeader === false ? 10 : price + 40;
console.log(price);
```

**Logic:**
- If `isLeader === false` → assign `10`
- Otherwise → assign `price + 40`

# 6. Nested Ternary (Use Carefully)

```javascript
let price = 30;
let isLeader = false;

price = isLeader === false \
    ? (price > 20 ? 100 : 200) \
    : price + 40;

console.log(price);
```

# 7. Logical NOT (!) 

Reverses a boolean value.

```javascript
const isPassed = false;

if (!isPassed) {
    console.log("good boy");
}
```

# 8. Comparison Operators

```javascript
console.log(10 == '10');  // true (only checks value)
console.log(10 === '10'); // false (checks value + type)
```

## Step-by-Step Logic
- Evaluate condition inside `if`.
- If true → execute block.
- If false → move to `else` or `else if`.
- Logical operators combine multiple conditions.
- Ternary operator evaluates and directly returns a value.

## Important Notes / Edge Cases
- Always prefer `===` over `==` to avoid unexpected type coercion.
- Nested ternary reduces readability; avoid in complex logic.

## Boolean Variables and Conditions
Boolean variables do not need `=== true`:

```javascript
if (hasCar) { ... } // cleaner
```

## Common Mistakes
- Using `==` instead of `===`
- Overusing nested ternary operators
- Writing redundant conditions like:
  
```javascript
if (isPassed === true)
```
after instead of:
```javascript
def if (isPassed)
done in a cleaner way.
```
to misunderstand operator precedence in complex conditions.

# Key Takeaways 
- `if...else` controls flow based on conditions.
- Logical operators (`&&`, `||`, `!`) are essential for combining conditions.
- Ternary operator is a concise alternative but should be used carefully.
- Always use strict equality (`===`, `!==`) for predictable behavior.
