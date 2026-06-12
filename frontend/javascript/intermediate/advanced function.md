<details>
  <summary><b>Hand Note</b></summary>

```js

Advance Function

//in javascript we can access function before or after declarartion not like c++
/*

function outerFunction()
{
    function innerFunction() {
        console.log("this is inner function");
    }
    return innerFunction;
}

*/

//const inner = outerFunction();
//inner();//this is inner function
//innerFunction(); we can not do this, though it is a function , it is inside a scope

//coluser 

/*

function outerFunction() {
    let counter = 0;

    function innerFunction() {
        counter = counter + 1;
        console.log("counter ", counter);
    }
    return innerFunction;
}

const inner = outerFunction();
inner(); // 1
inner(); // 2
inner(); // 3
inner(); // 4

*/

/*
function outerFunction(woner) {
    let counter = 0;

    function innerFunction() {
        counter = counter + 1;
        console.log("counter ", counter,woner);
    }
    return innerFunction;
}

const j = outerFunction("jhon");
j();
j();
j();

const a = outerFunction("alex");
a();
a();
a();

j();
j();
j();
*/

/*
counter  1 jhon
counter  2 jhon
counter  3 jhon
counter  1 alex
counter  2 alex
counter  3 alex
counter  4 jhon
counter  5 jhon
counter  6 jhon
*/

// teach me why it is like that



//callback function: we can pass a function as a parameter
function vote(age, permision) {
    if (age >= 18) {

        permision()
        
    }
}

function votePermision() {
    console.log("You are good to vote");
}

vote(34, votePermision);


// premitive variable always does pass by value
// Non premitive variable (array,object) always does pass by referance that means if we change it inside the function it will reflect to the actual variable

function arg(num1, num2) {
    console.log(arguments);
}
arg(2, 34, 5, 66, 7, 44, 3);
/*
Arguments] {
  '0': 2,
  '1': 34,
  '2': 5,
  '3': 66,
  '4': 7,
  '5': 44,
  '6': 3
}

arguments will give us array like object.
we can get arguments[2] as well

if we do console.log([...arguments]);  we can convert this array like object to array

*/

```
</details>



# Advanced Functions in JavaScript

## Concept Overview

JavaScript functions are first-class citizens, meaning they can:
- Be returned from other functions
- Be passed as arguments
- Maintain state through closures

This enables powerful patterns such as closures, callbacks, and flexible argument handling.

## Key Principles
- Functions can be defined inside other functions (nested functions).
- Inner functions have access to outer function variables (closure).
- Each function execution creates its own independent scope.
- Functions can be passed as arguments (callbacks).
- JavaScript handles arguments dynamically using the `arguments` object.

## Explanation
### 1. Nested Functions and Scope
```javascript
function outerFunction() {
    function innerFunction() {
        console.log("this is inner function");
    }

    return innerFunction;
}

const inner = outerFunction();
inner(); // works
```
**Key Idea:**
- `innerFunction` exists inside `outerFunction`.
- It is not accessible directly outside.
- But returning it allows access.
- `innerFunction(); // ❌ Error (out of scope)`


# 2. Closure (Core Concept)

```javascript
function outerFunction() {
    let counter = 0;

    function innerFunction() {
        counter = counter + 1;
        console.log("counter ", counter);
    }

    return innerFunction;
}

const inner = outerFunction();

inner(); // 1
inner(); // 2
inner(); // 3
```

## Why this works
- `outerFunction()` runs once.
- It creates:
  - `counter = 0`
  - `innerFunction`
- Even after `outerFunction` finishes, `innerFunction` remembers `counter`.

> This is called a **closure**:
> a function that remembers variables from its lexical scope even after the outer function has finished execution.

# 3. Independent Closures

```javascript
function outerFunction(owner) {
    let counter = 0;

    function innerFunction() {
        counter = counter + 1;
        console.log("counter ", counter, owner);
    }

    return innerFunction;
}

const j = outerFunction("john");
const a = outerFunction("alex");

j(); // 1 john
j(); // 2 john
a(); // 1 alex
a(); // 2 alex
```

## Why output behaves like this
- Each call to `outerFunction()` creates a new execution context.
- So:
  - `j` has its own `counter`
  - `a` has its own `counter`
- They do not share state.
- Later:
  - `j();` // continues from previous → **3 john**

# 4. Callback Functions

```javascript
function vote(age, permission) {
    if (age >= 18) {
        permission();
    }
}

function votePermission() {
    console.log("You are good to vote");
}

vote(34, votePermission);
```

**Key Idea:**
- Functions can be passed as arguments.
- `permission` is a callback function.
- It is executed only when the condition is satisfied.

# 5. Arguments Object

```javascript
function arg(num1, num2) {
    console.log(arguments);
}

arg(2, 34, 5, 66, 7);
```

**Output:**

```
{
  '0': 2,
  '1': 34,
  '2': 5,
  '3': 66,
  '4': 7
}
```

# Output:

```json
{
  "0": 2,
  "1": 34,
  "2": 5,
  "3": 66,
  "4": 7
}
```

## Key Idea
- `arguments` stores all passed values.
- It is array-like, not a real array.

## Convert to Array:
```javascript
const arr = [...arguments];
```

## Step-by-Step Logic (Closure Case)
1. Call `outerFunction()`
2. Create variable `counter = 0`
3. Create `innerFunction`
4. Return `innerFunction`
5. Store it in `inner`
6. Each call to `inner()`:
   - Accesses same `counter`
   - Updates it
   - Prints value

## Important Notes / Edge Cases
- Closures keep variables in memory → can cause memory issues if misused.
- Each function call creates a new closure, not shared unless explicitly designed.
- `arguments` is not available in arrow functions.

## Prefer Modern Alternative:
default example:
def arg(...args) {
    console.log(args); // real array
}


# Common Mistakes

- Trying to access inner functions directly
  - `innerFunction();` // ❌ not accessible
- Assuming closures share variables
  - ```javascript
    const a = outerFunction();
    const b = outerFunction();
    // a and b do NOT share state
    ```
- Confusing arguments with arrays
  - `arguments.map(...)` // ❌ error

# Key Takeaways

- Closures allow functions to retain state.
- Every function execution creates its own independent memory.
- Callbacks enable flexible and reusable logic.
- `arguments` provides access to all passed values but should be replaced with rest parameters (`...args`) in modern JavaScript.
