<details>
  <summary><b>Hand Note</b></summary>

  ```js
Some advance topics

const arr = [2, 34, 5, 6, 77, 8];
console.log(Array.isArray(arr));//for checking Array
console.log(typeof arr);//object print

// isNaN() to check it is not a number
//if it is true that means it is not a number
//if false that means it is number;
console.log(isNaN(34));//false
console.log(isNaN("34"));//false -- if it is number inside string then it is a number
console.log(isNaN("asddff"));//true
console.log(isNaN({}));//true -- object is not a number
console.log(isNaN([]));//false---exceptional


Note : need to know about permeative and non permeative datatype



//default parameter
// function add(num1, num2)
// {
//     const total = num1 + num2;
//     console.log(num1, num2, total);
// }

/*
default property for type ofm data
number--> 0 for add
number--> 1 for multiplication
string---> ""
array---> []
object---> {} or default property inside object

*/


// add(10); //10 undefined NaN
// //i have to give two parameter

// function add(num1, num2=0) { //if we do not pass any value for num2 , it will be 0 otherwise what i will pass
//     const total = num1 + num2;
//     console.log(num1, num2, total);
// }
// //if we declare the function like that we can call it before the declaration as well
// add(10);//10 0 10
// add(10, 30);//10 30 40

// add2(5, 8); invalid, we can not call before declaration if we declare using a variable
// const add2 = function (num1, num2)
//     {
//     console.log(num1 + num2);
// }

// add2(3, 4);//valid

//arrow function
//const arro = (num1, num2) => num1 + num2;//main stricture (parameter)=>statement. if one statement then no need to use {}, one line statement automaticly returns
//const arro = x => x * 10;//if one parameter then no need to use ()
//const arro = () => console.log("hi");//we will get hi undefine because it is not returning anything
//const arro = () => 3.141;// return 3.141 , no undefine

// const arro = (num1, num2) => {
//     const dif = Math.max(num1, num2) - Math.min(num1, num2);
//     const sum = num1 + num2;
//     return dif * sum;  //if we use multiline starement we have to return it
// }

// const isEqual = (num1, num2) => num1 === num2; //boolian return
// console.log(isEqual(3,5));


//templete string for multiline string
//const money = 100;
//const sentence = `give me the sum of ${10 + money + 23} pounds`;
//console.log(sentence);//ive me the sum of 133 pounds
// use `` for writing multiline string, if want any variable inside it use ${variable}
// we can write html also inside it
//${} we can put here function call, variable, calculation



//spread operator
// const arr = [1, 23, 4];
// console.log(arr);//[ 1, 23, 4 ]. with []
// console.log(...arr);//1 23 4 without [], that means ... will give us all the value one by one not the whole array
// //... will give us what is inside chips packet, variable will give us the whole packet

// const arr2 = [3, 6, 8];
// function f(n1, n2, n3) {
//     return Math.max(n1, n2, n3);
// }
// //console.log(f(arr2));//undefined because we are sending one parameter which is an arry, three element doesent mean three parameter will take those
// console.log(f(...arr2));//it will spread and three elements will act like three parameter

// const ref = [3, 45, 6, 77, 85, 4, 3, 22, 3];
// console.log(Math.max(ref));//Nan
// console.log(Math.max(...ref)); 85

// const ref2 = ref;// if we copy an array or object like this , the referance will be copied and changes will be reflacted in both array
// ref2.push(100);
// console.log(ref);/*
//   3, 45,  6, 77,  85,
//   4,  3, 22,  3, 100
// ] */

// const ref2 = [...ref, 300];//we can do same thing inside an object
// console.log(ref);//here 300 will not be added in ref , here ref 2 copy the element from ref one by one, not the referance


// //object and array decturing
// const student = { //we can access property using student.name
//     name: "shafi",
//     id: 123,
//     subject:"DSA"
// }
// //but if we declare like this we can access using key name
// const { product, brand: productBrand } = { product: "iphone", brand: "apple", price: 980 }
// console.log(product);
// console.log(productBrand);// we can change the keyname and keep it in a new variable. if we already have variable withe the same keyname then we have to change it like this

// //same thing we can do for array
// const [first, second] = [4, 5, 6, 6, 7];
// console.log(second);//5

// const newarr = [2, 3, 4, 5];
// const [one, two] = newarr;//first elementof newarr will go at one variable and second one will go at two


// const company = { product: "iphone", brand: "apple", price: 980 };
// console.log(Object.keys(company));//[ 'product', 'brand', 'price' ]
// console.log(Object.values(company));// 'iphone', 'apple', 980 ]
// console.log(Object.entries(company));// [ 'product', 'iphone' ], [ 'brand', 'apple' ], [ 'price', 980 ] ] we will get key-value pair in a array, it will be 2D array
// delete company.brand;//brand property will be deleted. it can delete objects own property not inheruted property
// Object.freeze(company);// now we can not change,add,delete or update any property
// Object.seal(company);//we cannot delete or add any property, but we can modify any existing property


//about undefine
/*
1. if my function have two parameter and while calling it if i pass 1 value then second one will be undefine
2.if we want to get access any object property which is not inside that object then we will gety undefine
3.if we try to get out of bound array value we will get undefine

*/

// need to know deferance between undefine and null


//truthy and falsy
/*

if (data) {
    console.log("true");
}
else {
    console.log("false");
}

*/

//data="".  false
//data="0".  true
//data=" ".  true
//data=null.  false
//data=undefined.  false
//data={}.  true
//data=[]  true



//double == confusions
//key rule: if both values are non-premetive then it will return false.if any value premitive then it will convet the premitive value and then check
//if(2=="2"). true
//if(1==true). true
//if(0==false). true
//if("1"==true). true
//if("0"==false). true
//if(null==undefined). true
//if(NaN==NaN). false
//if([]==""). true
//if([3]=="3"). true
//if([2,4]=="24"). false
//if({}=={}). false

//teach me why these are happening in a organise way





  ```
</details>

# Some Advanced Concepts

## Concept Overview

This section strengthens understanding of JavaScript’s internal behavior, especially type coercion, memory model, and function behavior, which are critical for writing predictable code.

### 1. Type Checking (Why `typeof` Fails for Arrays)
```javascript
const arr = [1, 2, 3];

typeof arr;          // "object"
Array.isArray(arr);  // true
```
**Why this happens**

Internally, JavaScript does not have a separate “array” type at the `typeof` level. Arrays are implemented as special objects.

So:
- `typeof []` → "object"
- This is a language design limitation.

### Correct Mental Model
- Use `typeof` → for primitives.
- Use `Array.isArray()` → for arrays.

### 2. `isNaN()` Deep Behavior (Important)
```javascript
isNaN("34");     // false
isNaN("abc");    // true
isNaN([]);       // false
```
**What actually happens internally**

`isNaN(value)` does this:
1. Convert value → Number
2. Check if result is NaN

**Examples breakdown:**
- `Number("34")` → 34 → not NaN → false
- `Number("abc")` → NaN → true
- `Number([])` → 0 → false
- `Number({})` → NaN → true


# Explanation of JavaScript Type Conversions and Memory Model

## Why does `[]` convert to `0`?
- `[].toString()` → `""`
- `Number("")` → `0`

## Correct Approach
- Use `Number.isNaN(value);`
- No conversion needed for strict checks

## Primitive vs Non-Primitive (Memory Model)

### Primitive
```javascript
let a = 10;
let b = a;
 b = 20;
```
- Stored directly in memory
- `a` and `b` are independent after assignment

### Non-Primitive (Reference Type)
```javascript
let arr1 = [1, 2];
let arr2 = arr1;

arr2.push(3);
```
- Both point to the same memory location
- Change in one affects the other

### Visualization:
```
arr1 ──► [1, 2, 3]
arr2 ──┘
```
**Fix:** Use copy instead of reference:
```javascript
let arr2 = [...arr1];
```

# 4. Default Parameters (Why Needed)

```javascript
function add(a, b) {
    return a + b;
}

add(10); // NaN
```

**Why NaN?**
- `b` is `undefined`
- `10 + undefined` → **NaN**

## Solution
```javascript
function add(a, b = 0) {
    return a + b;
}
```

## Key Insight
Default parameters prevent:
- `undefined`
- unexpected **NaN**

# 5. Function Types (Execution Difference)

## Function Declaration (Hoisting)
```javascript
add(2, 3);

function add(a, b) {
    return a + b;
}
```
**Why it works:**
- JavaScript moves function declaration to the top during the execution phase.

## Function Expression (No Hoisting)
```javascript
add2(2, 3); // ERROR

const add2 = function(a, b) {
    return a + b;
};
```
**Why it fails:**
- `const` is hoisted but not initialized.
- It exists in the **Temporal Dead Zone (TDZ)**.


# Arrow Function (Key Behavior)

```javascript
const sum = (a, b) => a + b;
```

## Important Differences
- No `this` binding (lexical `this`)
- Cleaner syntax
- Needs `return` for multi-line functions

# Spread Operator (Real Understanding)

```javascript
const arr = [1, 2, 3];
console.log(...arr); // 1 2 3
```

## What it actually does
- Breaks iterable into individual elements

## Function Case
- Example:
  ```javascript
  Math.max(...arr);
  ```
- Instead of:
  - `Math.max([1,2,3])` ❌
  - `Math.max(1,2,3)` ✅

# Copy vs Reference (Critical)
- Example:
  ```javascript
  const a = [1,2];
  const b = a;        // reference copy
  const c = [...a];   // value copy
  ```

# Destructuring (How It Works Internally)
## Object Destructuring Example:
```javascript
const { name } = { name: "Shafi" };
```
### Internally:
```javascript
const name = obj.name;
```


# Array

```javascript
const [first, second] = [10, 20];
```

## Internally:

- `first = arr[0];`
- `second = arr[1];`

## 8. Object Methods (Important Behavior)

- `Object.keys(obj);`
- `Object.values(obj);`
- `Object.entries(obj);`

## Key Insight

`Object.entries(obj);`

Returns:

```json
[
  [key, value],
  [key, value]
]
```

Useful for loops.

## Freeze vs Seal

- `Object.freeze(obj);`
  - No add, delete, update.
- `Object.seal(obj);`
  - Can update existing properties.
  - Cannot add or delete properties.


# 9. Undefined vs Null (Clear Difference)

**Undefined (automatic)**
```javascript
let x;
console.log(x); // undefined
```

**Null (intentional)**
```javascript
let x = null;
```

## Mental Model
| Type       | Meaning                     |
|------------|------------------------------|
| undefined  | value not assigned          |
| null       | value intentionally empty   |

# 10. Truthy vs Falsy (Core Logic)
JavaScript converts values → Boolean in conditions:
```javascript
if (value) { }
```

## Falsy Values
- false
- 0
- ""
- null
- undefined
- NaN

*Everything else → truthy*

# 11. == Deep Explanation (Most Important)
## Core Idea
`==` triggers type coercion.

## Step-by-Step Mental Model
When JS sees:
```javascript
a == b;
```
it follows:
1. **Are types same?**
   - Yes → compare directly.
2. **If different:**
   - Convert both to number (mostly).
3. **If object involved:**
   - Convert object → primitive.
4. **Compare again.**


# Case 1: Primitive Conversion

2 == "2"

## Steps:

- "2" → Number → 2
- 2 == 2 → true
- 1 == true
- true → 1
- 1 == 1 → true

# Case 2: Special Rule
null == undefined → true

*Only case where no conversion rule applies.*

# Case 3: Object Conversion
[] == ""

## Steps:

- [] → ""
- "" == "" → true
- [3] == "3"
- [3] → "3"
- "3" == "3" → true
- [2,4] == "24"
- [2,4] → "2,4"
- "2,4" != "24" → false

# Case 4: Object vs Object
{} == {} → false

*Because:*
*Different memory reference*

# Case 5: NaN
NaN == NaN → false
*Why?*
NaN is defined as:
> *"Not equal to anything, including itself"*


# Summary Table

| Expression | Result | Reason |
|--------------|---------|---------|
| `2 == "2"` | true | string → number |
| `1 == true` | true | boolean → number |
| `"1" == true` | true | boolean → number |
| *both* | 1 | null == undefined, special rule |
| `NaN == NaN` | false | special rule |
| `[] == ""` | true | [] → "" |
| `[3] == "3"` | true | [3] → "3" |
| `[2,4] == "24"` | false | "2,4" ≠ "24" |
| `{ } == { }` | false | reference |

## Important Notes

- `==` is predictable, but requires deep understanding.
- `===` is safe and recommended.

```js
// Example:
2 === "2" // false
```

## Common Mistakes

- Using `==` in conditions.
- Not understanding reference copying.
- Misusing `isNaN()`.
- Forgetting default parameters.
- Expecting objects to compare by value.

## Key Takeaways

- Always prefer `===`.
- Understand type coercion rules, not just memorize results.
- Use spread operator to avoid mutation bugs.
- Learn reference vs. value deeply.
- Think step-by-step how JavaScript evaluates expressions.
