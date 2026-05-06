# React Basics and Core Concepts (Deep Explanation)

## Concept Overview

- React is a component-based UI library.
- Instead of writing one big HTML page, you break your UI into small reusable pieces (components).

### Think like this:

- Traditional way → One large file controlling everything ❌
- React way → Many small independent parts working together ✅

### Each component:

- Controls its own UI
- Can receive data
- Can be reused anywhere

## JSX (JavaScript + XML)

JSX allows you to write HTML inside JavaScript, but it is not HTML.

### What actually happens behind the scene:
```jsx
<h1>Hello</h1>
```
This is converted into:
```javascript
React.createElement("h1", null, "Hello");
```
So JSX is just syntactic sugar for JavaScript.

# Components (Core Idea)

## Basic Component
```jsx
function Greet() {
  return <p>Hi, good morning</p>;
}
```

## How it works internally
- `Greet()` is just a function.
- It returns JSX → JSX becomes a React element (object).
- React renders that object to the DOM.

## Why Capital Letter is Required
- `<Greet />`   // React treats this as component.
- `<greet />`   // React treats this as HTML tag (wrong).

React differentiates components using naming conventions.

## Returning Multiple Elements
### Why we need a wrapper
- React components must return one single parent element.

### Reason:
- React internally builds a tree structure (Virtual DOM).
- Each component must return one root node.


# JSX Rules (Deep Understanding)

## 1. Self-closing tags

### HTML:
```html
<img>
```

### JSX:
```jsx
<img />
```

**Reason:**
JSX is closer to XML, where every tag must be closed.

---

## Examples of Correct Usage in JSX:
- **Wrong:**
```jsx
return (
  <h1>Hello</h1>
  <p>World</p>
);
```
- **Correct:**
```jsx
return (
  <div>
    <h1>Hello</h1>
    <p>World</p>
  </div>
);
```
- **Better (Fragment):**
```jsx
return (
  <>
    <h1>Hello</h1>
    <p>World</p>
  </>
);
'this fragment avoids unnecessary DOM nodes.
```


# 2. camelCase Attributes
- `onClick`
- `tabIndex`

**Reason:**
JSX uses JavaScript object style, not HTML string style.

# 3. JavaScript Inside JSX
```jsx
<h1>{name}</h1>
```

## Important:
- `{}` → allows JavaScript expression
- NOT full JavaScript code

### Expression vs Statement
**Allowed:**
- `{name}`
- `{a + b}`
- `{condition ? "yes" : "no"}`

**Not Allowed:**
- `if (condition) {}` ❌
- `for (...) {}` ❌

## JavaScript + JSX Execution Flow
```jsx
function Student() {
  const lastName = "Islam";
  return <h3>Name: Shafi {lastName}</h3>;
}
```
**Execution:**
1. JS runs first → `lastName = "Islam"`
2. JSX reads `{lastName}`
3. Final UI → *Name: Shafi Islam*

# Styling in React (Important Detail)
## 1. External CSS
```html
<div className="box"></div>
```
**Why `className`?**
because:
- `class` is a reserved keyword in JavaScript.



## 2. Inline Style Object

```javascript
const style = {
  border: "2px solid green",
  borderRadius: "10px"
};
```

### Important rules
- Must be object
- Property must be camelCase
- Value must be string or number

### Why object?
Because internally:

```html
<div style={style}></div>
```
becomes:

```javascript
element.style.border = "2px solid green";
```

## Props (VERY IMPORTANT CONCEPT)

**Props** = input to a component

Think:
- **Component** = Function
- **Props** = Function Parameters

### Passing Props
```jsx
<Student skill="react" experience="2" />
```
This becomes:
```javascript
Student({
  skill: "react",
  experience: "2"
});
```
# Receiving Props

```jsx
function Student(props) {
  console.log(props);
}
```

**Output:**

```json
{
  "skill": "react",
  "experience": "2"
}
```

## Destructuring Props (Important)

```jsx
function Student({ skill, experience = 0 }) {
  // component logic
}
```

### What is happening?

Instead of accessing props like:
- `props.skill`
- `props.experience`

you extract them directly in the function parameters.

### Default Value
- `experience = 0`
- If no value is passed for experience, it defaults to `0`.

## Critical Rule

Props are **read-only**.

❌ **Wrong:**
```jsx
props.skill = "python" // This is incorrect because props are read-only.
```

**Reason:**
React uses props for predictable UI rendering and modifying them directly can lead to bugs.

# Conditional Rendering (Core Logic)

React does **NOT** have special syntax.

It uses normal JavaScript logic.

## if-else
```jsx
if (experience > 5) {
  return <p>Experienced</p>;
}
```

## Ternary (Most Used)
```jsx
{experience > 5 ? <p>Experienced</p> : <p>Learning</p>}
```

## && Operator
```jsx
{experience > 5 && <p>Experienced</p>}
```

**Meaning:**
- If true → show
- If false → show nothing

## Variable Approach (Best for Complex UI)
```jsx
let content;

if (condition) {
  content = <A />;
} else {
  content = <B />;
}

return content;
```


# Lists and `map()` (VERY IMPORTANT)

## Why `map()`?

React needs to render multiple components dynamically.

## Basic Example
```jsx
const heroes = ['tom', 'mark'];

heroes.map(hero => <Hero hero={hero} />);
```

## What happens internally
- `[`
- `  Hero({ hero: "tom" }),`
- `  Hero({ hero: "mark" })`
- `]`

React renders each component.

## Key Property (CRITICAL CONCEPT)
```jsx
heroes.map(hero => (
  <Hero key={hero.id} hero={hero} />
));
```

### Why `key` is needed?
- React uses Virtual DOM diffing algorithm.
- When list changes:
  - React compares old vs new.
  - Uses `key` to identify elements.

### Without `key`:
- React re-renders everything (slow).
- Bugs can happen.

## Your Mistake (Important Fix)
- You wrote:
```jsx
<Hero keys={heros.id} />
the correct version is:
<Hero key={hero.id} />
does not use `keys`, use `key`.
hero.id not heros.id.
```


# Export and Import

## Default Export
```javascript
export default Student;
```

## Import
```javascript
import Student from "./Student";
```

# Key Rule
- Only one default export per file

# Important Notes (Deep)
- JSX ≠ HTML → it's JavaScript
- Components must return one root
- Props are immutable
- `key` is required for lists
- `{}` executes JavaScript expressions
- Styling uses JavaScript objects

# Common Mistakes (Critical)
- Using `class` instead of `className`
- Using `keys` instead of `key`
- Writing `if` directly inside JSX
- Forgetting parent wrapper
- Trying to modify props
defaults in React components are generally discouraged.
- Not using a unique key in list items

# Key Takeaways
- React = UI broken into components
- JSX = JavaScript representation of UI
defaults in React components are generally discouraged.
- Props = data flow into components
defaults in React components are generally discouraged.
- Conditional rendering = normal JS logic
defaults in React components are generally discouraged.
- `map()` = dynamic UI rendering
defaults in React components are generally discouraged.
- `key` = performance + correctness
