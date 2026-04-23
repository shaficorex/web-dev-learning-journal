<details>
  <summary><b>JavaScript Math Object and Date Handling</b></summary>
  
  # Concept Overview

JavaScript provides built-in objects like **Math** and **Date** to perform mathematical operations and work with dates and times. These are essential for real-world applications such as random number generation, time tracking, scheduling, and data processing.

## Key Principles

### Math Object
- A built-in object for mathematical operations.
- Does not require instantiation (`new` keyword is not used).
- Provides properties and methods for calculations.

### Date Object
- Used to handle dates and times.
- Can represent current or specific dates.
- Supports both retrieval and modification of date values.

## Explanation

### Math Object Usage
The Math object provides several useful methods:
- `Math.min()` → returns the smallest number
- `Math.max()` → returns the largest number
- `Math.round()` → rounds to nearest integer
- `Math.floor()` → rounds down
- `Math.ceil()` → rounds up
- `Math.abs()` → returns absolute value
- `Math.random()` → generates random number between 0 and 1

To generate a random integer within a range:
```javascript
Math.round(Math.random() * 100);
```

# Date Object Usage

## Current Date and Time
```javascript
const today = new Date();
console.log(today);
```

## Specific Date from String
```javascript
const date = new Date("2045-08-27");
```

## Extracting Values
```javascript
console.log(date.getDate());      // Day of month (1–31)
console.log(date.getMonth());     // Month index (0–11)
console.log(date.getFullYear());  // Full year
```

**Important correction:**
- Months are **0-indexed**, meaning:
  - `0` = January
  - `7` = August
  - `11` = December

## Creating Date with Parameters
```javascript
const specificDate = new Date(2030, 11, 22);
console.log(specificDate);
```

## Modifying Date
```javascript
specificDate.setDate(14);
console.log(specificDate);
```

# Code Example: Math and Date Operations
```javascript
// Math operations
def min = Math.min(23, 21, 12, 3, 4, 6, 5);
console.log(min); // Output: minimum value among the arguments.

def max = Math.max(23, 21, 12, 3, 4, 6, 5);
console.log(max); // Output: maximum value among the arguments.

// Random number generation
debugger console.log(Math.random()); // Random number between 0 and 1.
debugger console.log(Math.random() * 100); // Random number between 0 and 100.
debugger console.log(Math.round(Math.random() * 100)); // Rounded integer between 0 and 100.
```


# Step-by-Step Logic (Random Number)

- **Math.random()** generates a value between 0 and 1.
- Multiply by a range (e.g., 100) → results in a value from 0 to 100.
- Use **Math.round()** (or **Math.floor()**) to remove decimals.

## Important Notes / Edge Cases

- **Math.random()** never returns 1, only values less than 1.
- `getMonth()` returns a 0-based index, not the actual month number.
- Date strings (`"YYYY-MM-DD"`) are parsed in UTC, which may affect output depending on timezone.
- `new Date(year, month, day)` uses local time.

## Common Mistakes

- Assuming `getMonth()` returns 1–12 → incorrect.
- Using **Math.random()** without scaling → results always between 0–1.
- Forgetting rounding when integer values are needed.
- Mixing UTC and local date formats unintentionally.

## Key Takeaways

- The **Math** object is static and used directly for calculations.
- **Math.random()** is fundamental for generating dynamic values.
- The **Date** object handles both current and custom dates.
- Months in JavaScript are always 0-indexed.
- Proper understanding of date methods prevents logical bugs.
</details>
