# JavaScript Loops

## Concept Overview

Loops in JavaScript are used to execute a block of code repeatedly based on a condition. They are essential for iterating over data structures like arrays and for performing repetitive tasks efficiently.

## Key Principles
- A loop continues execution while a condition is true.
- Different loop types are used depending on the scenario:
  - `for...of` → iterate over iterable data (arrays, strings)
  - `for` → when iteration count is known
  - `while` → when iteration count is unknown
  - `do...while` → guarantees at least one execution
- Loop control statements:
  - `break` → exits the loop completely
  - `continue` → skips the current iteration

## Explanation

### 1. for...of Loop (Array Iteration)
Used to iterate through elements of an iterable (like arrays).

```javascript
const nums = [9, 8, 7, 6, 5, 4, 3, 2, 1];

for (const num of nums) {
    console.log(num);
}
```
Directly accesses values (not indices). Cleaner and more readable for arrays.

### 2. while Loop
Used when the number of iterations is not known beforehand.

```javascript
let loopVariable = 0;

while (loopVariable < 5) {
    console.log("looping");
    loopVariable++;
}
```
Condition is checked before each iteration. If condition is false initially, loop will not run.


# 3. for Loop

Used when the number of iterations is known.

```javascript
for (let i = 0; i < 10; i += 2) {
    console.log(i);
}
```

**Structure:**
- Initialization → `let i = 0`
- Condition → `i < 10`
- Update → `i += 2`

Provides full control over loop execution.

# 4. do...while Loop

Executes the code at least once, regardless of the condition.

```javascript
let i = 10;

do {
    console.log("hi");
    i++;
} while (i < 10);
```

Condition is checked after execution.
Even if the condition is false initially, it runs once.

# Step-by-Step Logic (Example: for loop)
1. Initialize `i = 0`
2. Check condition `i < 10`
3. Execute loop body
4. Increment `i` by 2
5. Repeat until condition becomes false



# Loop Control Statements

## break

Stops the loop immediately.

```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) break;
    console.log(i);
}
```

## continue

Skips current iteration and moves to the next one.

```javascript
for (let i = 0; i < 5; i++) {
    if (i === 2) continue;
    console.log(i);
}
```

# Important Notes / Edge Cases
- Infinite loops occur when the condition never becomes false.
- Always ensure the loop variable is updated correctly.
- `for...of` does not provide index directly (use `for` if index is needed).
- `do...while` is rarely used but important for specific cases.

# Common Mistakes
- Forgetting to update loop variable → infinite loop.
- Using `==` instead of proper logic in conditions.
- Misplacing `break` or `continue`.
- Expecting `while` loop to run at least once (it may not). 

# Key Takeaways
- Choose loop type based on use case:
  - Known iterations → `for`
  - Unknown iterations → `while`
  - Guaranteed execution → `do...while`
  - Iterating arrays → `for...of`
- Control flow (`break`, `continue`) is critical for managing loop behavior.
- Proper condition and update logic prevent bugs and infinite loops.
