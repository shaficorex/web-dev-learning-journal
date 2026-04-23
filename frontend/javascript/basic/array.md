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
console.log(num.concat(mixedArray));
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
