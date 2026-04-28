<details>
  <summary><b>Hand Note</b></summary>

```js
Array power


/*
function doubleIt(num) {
    return num * 2;
}

let arr = [1, 2, 3, 4, 5, 6, 7];
//const doubled = arr.map(doubleIt);// map function take every element from array and calls doublrIt function element by element and put the return value as arrrayn in a new variable
const doubled = arr.map(num => num * 2);// we can do it in one line
console.log(doubled);
*/
let arr = [1, 2, 3, 4, 5, 6, 7];
//arr.forEach(num => console.log(num * 2));  //forEach does same thing but it doesnot return anything , usualy we use it for doing print 
//forEach mainly used for looping
//const doFilter = arr.filter(num => num % 2 === 0);
//filter does the same things like map ,but the main difference is , it's function checks a condition and return whichever meets the condition and give us in an array
//console.log(doFilter);

//const doFind = arr.find(num => num % 2 === 0);//it does the same thing like filter but give us the first match. it does not give us a whole array, jjust give us one value
//if there is no match then find will return undefine

const total = arr.reduce((sum, num) => sum + num, 0);
console.log(total);
/*
we can get total sum of an array in one line using reduce function
we need to pass one callback function and what will be the initial value of sum.
in callback function sum will be current total and num will be current index value
*/

```

</details>



# JavaScript Array Power Methods

## Concept Overview

JavaScript provides powerful array methods that allow you to process data efficiently without writing manual loops. These methods are part of functional programming and help write cleaner, more readable code.

## Key Principles
- These methods iterate over arrays internally.
- Most of them accept a callback function.
- They do not mutate the original array (except if explicitly coded inside).
- Some return new arrays, others return single values or nothing.

## Explanation

### 1. map()

Transforms each element and returns a new array.

```javascript
const arr = [1, 2, 3, 4, 5, 6, 7];
const doubled = arr.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10, 12, 14]
```

- Runs for every element
- Must return a value for each element
- Output array length = input array length

### 2. forEach()

Executes a function for each element but returns nothing.

```javascript
darr.forEach(num => console.log(num * 2));
```
Used for side effects (e.g., logging, DOM updates)
Cannot store results directly


# Array Methods

## 3. `filter()`

Returns a new array containing elements that satisfy a condition.

```javascript
const evenNumbers = arr.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4, 6]
```

- Callback must return `true` or `false`
- Output array may be smaller (or empty)

## 4. `find()`

Returns the first element that matches a condition.

```javascript
const firstEven = arr.find(num => num % 2 === 0);
console.log(firstEven); // 2
```

- Stops after first match
- Returns `undefined` if no match is found

## 5. `reduce()`

Reduces the array into a single value.

```javascript
const total = arr.reduce((sum, num) => sum + num, 0);
console.log(total); // 28
```

### Step-by-Step Logic of `reduce()`
| Step | sum | num | result |
|-------|-------|------|---------|
| Initial | - | - | - |
| ...   | ...   | ...  | ...     |
| Final | - | - | **28** |

- `sum` = accumulator (stores running result)
- `num` = current element
- `0` = initial value


# Important Notes / Edge Cases
- `map`, `filter` always return arrays
- `find` returns a single value, not an array
- `reduce` can return any type (number, object, array, etc.)
- If no initial value is provided in `reduce`, the first element is used as the initial accumulator
- `forEach` cannot be stopped early (no break)

# Common Mistakes
- Using `forEach` when you need a returned array → use `map`
- Using `filter` when you only need one value → use `find`
- Forgetting to return inside `map` or `filter`
- Misunderstanding `reduce` accumulator logic
- Assuming `find` returns an array (it does not)

# Key Takeaways
- Use `map` for transformation
- Use `filter` for selection
- Use `find` for first match
- Use `reduce` for aggregation
- Use `forEach` for side effects only
