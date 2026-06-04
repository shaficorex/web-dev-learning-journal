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

# Primitive vs Non-Primitive Data Types

## Primitive Data Types

Store the actual value.

```javascript
let a = 10;
let b = a;

b = 20;

console.log(a); // 10
console.log(b); // 20
```

**Primitive types:**
- Number
- String
- Boolean
- Undefined
- Null
- BigInt
- Symbol

## Non-Primitive Data Types

Store a reference (memory address).

```javascript
const arr1 = [1, 2];
const arr2 = arr1;

 arr2.push(3);

 console.log(arr1); // [1, 2, 3]
```

**Non-primitive types:**
- Object
- Array
 
- Function
 

 **Important:** Comparing non-primitive values checks references, not contents.

 ```javascript
 
 {} == {}      // false
 [] == []      // false
 ```

 ## Array Checking 
```javascript
 const arr = [2, 34, 5, 6];
 
 console.log(Array.isArray(arr)); // true
 console.log(typeof arr);         // "object"
 ```
Note: Arrays are a special type of object in JavaScript.

# isNaN()

Used to check whether a value can be converted into a valid number.

```javascript
console.log(isNaN(34));       // false
console.log(isNaN("34"));     // false
console.log(isNaN("abc"));    // true
console.log(isNaN({}));       // true
console.log(isNaN([]));       // false
```

## Why is `isNaN([])` false?

`Number([])` // 0

Since it becomes a valid number, `isNaN([])` returns false.

## Default Parameters

### Without a default value:
```javascript
function add(num1, num2) {
    console.log(num1 + num2);
}
add(10); // NaN
```

### With a default value:
```javascript
def add(num1, num2 = 0) {
    console.log(num1 + num2);
}
add(10); // 10
```

### Common default values:
- Number (addition) -> 0
- Number (multiply) -> 1
- String -> ""
- Array -> []
- Object -> {}

# Function Declaration vs Function Expression

## Function Declaration

Can be called before declaration.

```javascript
add(5, 8);

function add(a, b) {
    return a + b;
}
```

## Function Expression

Cannot be called before declaration.

```javascript
const add = function(a, b) {
    return a + b;
};

add(5, 8);
```

## Arrow Functions

**Basic structure:**

```javascript
const add = (a, b) => a + b;
```

**Single parameter:**

```javascript
const square = x => x * x;
```

**No parameters:**

```javascript
const greet = () => "Hi";
```

**Multiple statements require return:**

```javascript
const calc = (a, b) => {
    const sum = a + b;
    return sum;
};
```

# Undefined vs Null

## Undefined

JavaScript could not find a value.

```javascript
let x;
console.log(x); // undefined
```

**Examples:**
- `obj.name`       // property does not exist
- `arr[100]`       // out of bound index

## Null

Intentionally assigned empty value.

```javascript
let user = null;
```

## Truthy and Falsy Values

**Falsy values:**
- `false`
- `0`
- `""`
- `null`
- `undefined`
- `NaN`

Everything else is truthy.

**Examples:**
- `"0"`       // true
- `' '`       // true (note: space character)
- `[]`        // true (empty array)
- `{}`        // true (empty object)

## Loose Equality (`==`) Confusions

defines that == performs automatic type conversion before comparison.

| Expression | Result |
|------------|---------|
| 2 == "2"           | true |
| 1 == true          | true |
| 0 == false         | true |
| "1" == true        | true |
| "0" == false       | true |
| null == undefined  | true |
| NaN == NaN         | false |
| [] == ""           | true |
| `[3]` == "3"         | true |
| `[2,4]` == "24"      | false |
| `{}` == `{}`           | false |
due to type coercion.
 
**Recommendation:** Prefer strict equality (`===`) and inequality (`!==`).
defines that !== because no automatic type conversion occurs.
