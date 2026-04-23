# JavaScript Objects

## Concept Overview

An object in JavaScript is a collection of key–value pairs used to store structured data. It allows grouping related properties and behaviors (functions) under a single entity.

## Key Principles
- Objects store data as key: value pairs.
- Keys are strings (or Symbols); values can be any data type.
- Objects can contain:
  - Primitive values (number, string, boolean)
  - Arrays
  - Other objects (nested objects)
  - Functions (methods)
- Objects are mutable (can be modified after creation).

## Explanation
### Creating an Object
```javascript
const student = {
    name: "shafi",
    id: 123,
    subject: ["bangla", "english", "math"],
    isPassed: true,
    gpa: 4.57,
    "fav places": ["cardiff", "ponty"],
    appearance: {
        hair: "black",
        height: 78,
        face: {
            shape: "round"
        }
    },
    act: function () {
        console.log("he is a good student");
    }
};
```


# Accessing Object Properties

## 1. Dot Notation
```javascript
console.log(student.id);
const stuName = student.name;
```

## 2. Bracket Notation
```javascript
console.log(student["isPassed"]);
console.log(student["fav places"]);
```

## 3. Dynamic Key Access
```javascript
const keyName = "fav places";
console.log(student[keyName]);
```

# Modifying Object Properties
```javascript
student.gpa = 3.50;
student["fav places"].push("trimance");
```

# Getting Keys and Values
```javascript
const getKeys = Object.keys(student);
const getValues = Object.values(student);
```

# Accessing Nested Objects
```javascript
console.log(student.appearance.face.shape); // round
```

# Deleting Properties
```javascript
delete student.id;
```


# Looping Through an Object

```javascript
for (const key in student) {
    console.log(student[key]);
}
```

## Object Methods (Functions Inside Objects)

`student.act();`

## Different Ways to Create Objects

- `const pencil = new Object();`        // Constructor method
- `const pen = Object.create({});`     // Prototype-based creation

## Objects Inside Arrays

```javascript
const arr = [
    {name: "shafi", roll: 345, isPassed: false},
    {name: "holand", roll: 678, isPassed: false},
    {name: "shafi", roll: 345, isPassed: false}
];

console.log(arr[1]);
```

## Step-by-Step Logic (How Object Works Internally)

- JavaScript stores objects as references in memory.
- Each key maps to a value.
- Accessing with `.` or `[]` retrieves the value using the key.
- Modifying updates the same memory reference.


# Important Notes / Edge Cases
- Keys with spaces must use bracket notation.
- Objects are passed by reference, not by value.
- Functions inside objects are called methods.
- Arrays inside objects behave like normal arrays.

# Common Mistakes

- Using dot notation with keys that contain spaces:
  - `student.fav places` ❌

- Forgetting brackets for dynamic keys:
  - `student.keyName` ❌
  - `student[keyName]` ✅

- Confusing arrays and objects:
  - Arrays → ordered (index-based)
  - Objects → unordered (key-based)

# Key Takeaways
- Objects are fundamental for structured data in JavaScript.
- Use dot notation for simple keys, bracket notation for complex or dynamic keys.
- Objects support nesting and functions.
- Understanding objects is critical for real-world applications (APIs, databases, etc.).
