<details>
    <summary><b>Hand Note</b></summary>

```js

Javascript array

Array is a object of class in javascript, that is why we can store different type of data inside an array

const num = [1, 2, 3, 4, 5, 6];
const mixedArray = [1, 2, "banana","rafiq", true,"banana","water", 1.4];

console.log(mixedArray[2]);
mixedArray[1] = 1000;

console.log(num.length);

num.push(100, 200, 300);
const outLast=num.pop(); //it will pop from last and store it inside out, if no element insoide array it will return undefine. that means after poping it will return what it has popped
console.log(outLast);

const outFirst = num.shift(); //same as pop , but pop from front
console.log(outFirst);

num.unshift(5000, 6000, 70000);//it will push at front
console.log(num);

console.log(mixedArray.includes("water"));//true print, includes() checks the elementis inside the array or not 
//best for ifelse condition
if (mixedArray.includes("water"))
{
    console.log("water found");
}

console.log(mixedArray.indexOf("banana"));//checks from 0 to last for the element, if duplicate then return the first index
console.log(mixedArray.indexOf("apple")); //if no element like that then return -1

const val = 12;
console.log(Array.isArray(num));// true
console.log(Array.isArray(val));// false. we use it to check weather a variable is array or not

console.log(num.slice(1, 5));//1 to 4 index


console.log(num.concat(mixedArray)); //to concate two array. firstarray.concat(secondarray)

console.log(num.splice(4, 3));//it will remove 3 element from index 4 inclusive
console.log(num);



let arr = [3, 2, 4, 56, 7, 8, 99];
console.log(arr.join('|'));//3|2|4|56|7|8|99
//it will add all the element from an array with a specefire and make it a string


console.log(arr.reverse());// to reverse an arrray.
//or we can use a new array and unshift. or we can run the llop from last


//sort 
//javascript sort by alphabatical order like strin . in number ass well. i will learn later hot ro sort number in javascript

```
</details>


# JavaScript Arrays

## Concept Overview

An array in JavaScript is a special type of object used to store ordered collections of values. Arrays are dynamic and can hold elements of different data types within the same structure.

## Key Principles
- Arrays are objects with indexed elements (0-based index).
- They can store mixed data types (numbers, strings, booleans, etc.).
- Arrays are mutable, meaning their contents can be changed.
- Built-in methods allow efficient manipulation of data.

## Explanation

### Creating Arrays
```javascript
const num = [1, 2, 3, 4, 5, 6];
const mixedArray = [1, 2, "banana", "rafiq", true, "banana", "water", 1.4];
```

### Accessing and Modifying Elements
```javascript
console.log(mixedArray[2]); // "banana"
mixedArray[1] = 1000; // modify value
```

### Array Length
```javascript
console.log(num.length); // total elements
```

### Common Array Methods
#### Adding and Removing Elements
```javascript
to add elements at the end:
num.push(100, 200, 300); // add to end 
// Remove last element:
const outLast = num.pop(); 
// removes last element and returns it 
// Remove first element:
const outFirst = num.shift(); 
// removes first element and returns it 
// Add elements at the beginning:
num.unshift(5000, 6000, 70000); 
// adds elements at the beginning```
```


# Searching Elements
```javascript
console.log(mixedArray.includes("water")); // true

if (mixedArray.includes("water")) {
    console.log("water found");
}

console.log(mixedArray.indexOf("banana")); // first occurrence index
console.log(mixedArray.indexOf("apple"));  // -1 if not found
```

# Type Checking
```javascript
const val = 12;
console.log(Array.isArray(num)); // true
console.log(Array.isArray(val)); // false
```

# Extracting and Modifying Portions
## slice (non-destructive)
```javascript
console.log(num.slice(1, 5)); 
// returns elements from index 1 to 4
```
## splice (destructive)
```javascript
console.log(num.splice(4, 3)); 
// removes 3 elements starting from index 4
console.log(num); // original array is modified
```

# Combining Arrays
```javascript
console.log(num.concat(mixedArray));  //it returns a new array
```

# Converting to String
```javascript
let arr = [3, 2, 4, 56, 7, 8, 99];
console.log(arr.join('|')); 
// "3|2|4|56|7|8|99"
```

# Reversing Array
```javascript
console.log(arr.reverse()); 
// reverses array in-place
```



# Sorting Array

```javascript
arr.sort();
```

**Default sorting** is lexicographical (string-based). This causes incorrect results for numbers:

```javascript
[10, 2, 5].sort(); // [10, 2, 5]
```

```javascript
// Before sorting
heights = [1, 1, 4, 2, 1, 3];
ex      = [1, 1, 4, 2, 1, 3];

// After sorting
ex.sort((a, b) => a - b);

heights = [1, 1, 4, 2, 1, 3];
ex      = [1, 1, 1, 2, 3, 4];

//sort() modifies the original array and also returns the same array reference.
```

# Why [...heights]?

```javascript
let ex = [...heights];
```

creates a new array:

```javascript
heights = [1, 1, 4, 2, 1, 3]
ex      = [1, 1, 4, 2, 1, 3]
```

Then sorting `ex` does not affect `heights`.

```javascript
ex.sort((a,b) => a - b);
```

After sorting `ex`, the arrays are:

```javascript
heights = [1, 1, 4, 2, 1, 3]
ex      = [1, 1, 1, 2, 3, 4]
```
<details>
    <summary><b>How does (a, b) => a - b work?</b></summary>

    # Sorting Numbers in JavaScript

## Take Two Numbers at a Time

- Compare two numbers `a` and `b`.
- If the result is negative (`a - b < 0`), then **`a` comes before `b`**.
- If the result is positive (`a - b > 0`), then **`a` comes after `b`**.
- If the result is zero (`a - b = 0`), their order stays the same.

## Examples:

### When Result is Negative:

```plaintext
2 - 5 = -3
```

*Negative, so:* 

**2 comes before 5**

### When Result is Positive:

```plaintext
10 - 2 = 8
```

*Positive, so:* 

**10 comes after 2**

### When Result is Zero:

```plaintext
e.g.,
5 - 5 = 0
```

*Their order stays the same.*

## Sorting in Ascending Order:
```javascript
arr.sort((a, b) => a - b);
```
Result:
```json
[2, 5, 10]
```

## Sorting in Descending Order:
```javascript
arr.sort((a, b) => b - a);
```
Result:
```json
[10, 5, 2]
```

## Quick Memory Trick:
- `a - b`: Small to Large order.
- `b - a`: Large to Small order.

> **Note:** Whenever you sort numbers in JavaScript, always use a compare function. Using just `sort()` without it is usually only safe for strings.

</details>
**Correct numeric sorting:**

```javascript
[10, 2, 5].sort((a, b) => a - b); // ascending
```

## Important Notes / Edge Cases
- `pop()` and `shift()` return `undefined` if the array is empty.
- `slice()` does not modify the original array.
- `splice()` modifies the original array.
- `reverse()` also modifies the original array.
- Arrays can contain duplicate values.
- `indexOf()` only returns the first occurrence.

## Common Mistakes
- Assuming `sort()` works correctly for numbers without a comparator.
- Confusing `slice()` (non-destructive) with `splice()` (destructive).
- Forgetting that arrays are objects and passed by reference.
- Using `indexOf()` when duplicates exist without handling all occurrences.

## Step-by-Step Logic Example (`splice`)
```javascript
let arr = [10, 20, 30, 40, 50, 60];
// remove 2 elements from index 2
arr.splice(2, 2);
// result: [10, 20, 50, 60]
```

## Key Takeaways
- JavaScript arrays are flexible and allow mixed data types.
- Many built-in methods exist for efficient data manipulation.
- Understanding destructive vs non-destructive methods is critical.
- Sorting numbers requires a custom comparator function.
