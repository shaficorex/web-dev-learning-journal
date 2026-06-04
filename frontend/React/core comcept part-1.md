# React

React is a component-based JavaScript library used to build user interfaces.

We usually work in JSX files, where JSX means:

- JavaScript + XML-like syntax

## Component

A component is a small reusable part of a website.

A component returns JSX (which looks similar to HTML).

## Structure of a Component
```jsx
function Greet() {
  return (
    <p>Hi, good morning</p>
  );
}
```

## Important Notes
- Component names should start with a capital letter.
- `function Greet() {}`
- This helps React understand that it is a custom component, not an HTML tag.

If we use:
```jsx
<Greet></Greet>
```
or:
```jsx
<Greet />
```
React will render whatever the component returns.

## Returning Multiple Elements
A component can return only one parent element.
If we want to return multiple elements, we must wrap them inside:
- `div`
- `section`
- `Fragment (<> </>)`

### Example:
```jsx
function Student() {
  return (
    <div>
      <h3>Name: Shafi</h3>
      <p>ID: 23456</p>
    </div>
  );
}
```
Think of it like a normal function returning one value. React components must also return one root element.

# Rules of JSX

## 1. All tags must be closed

```jsx
<img />
<br />
<input />
```

Unlike HTML, JSX requires self-closing tags.

## 2. HTML attributes use camelCase

**Examples:**
- onClick
- tabIndex
- className

**Not:**
- onclick
- tabindex
- class

## 3. Dynamic JavaScript values use `{}`

In JavaScript template literals:
```js
`${name}`
```
In JSX:
```jsx
{name}
```
No `$` sign is needed.


# Using JavaScript Inside JSX

We cannot write JavaScript statements directly inside JSX.

**Invalid:**

```jsx
return (
  if(true){
    ...
  }
)
```

But we can use JavaScript expressions inside `{}`.

**Valid:**

```jsx
<h3>{name}</h3>
```

We can write any JavaScript code before `return`.

**Example:**

```jsx
function Student() {
  const lastName = "Islam";
  const concat = "@&12£$%^&**";

  return (
    <div>
      <h3>Name: Shafi {lastName}</h3>
      <p>Password: 23456{concat}</p>
    </div>
  );
}
```

# Three Ways to Apply CSS

## 1. External CSS File

Create styles in:

```css
App.css
```

Then use:

```jsx
<div className="student">
```

## 2. Style Object
```jsx
function Student() {
  const studentStyle = {
    border: "2px solid green",
    margin: "40px",
    padding: "20px",
    borderRadius: "10px"
  };
  return (
    <div style={studentStyle}>
      ...
    </div>
  );
}
```
**Important:**
- CSS properties use camelCase.
- Example:
  - `border-radius` becomes `borderRadius`

## 3. Inline Style Object
```jsx
function Student() {
  return (
    <div
      style={{
        border: "2px solid green",
        margin: "40px",
        padding: "20px",
        borderRadius: "10px"
      }}
    >
      ...
    </div>
  );
}
```

# Passing Data to Components (Props)

Props allow us to pass data from a parent component to a child component.

## Example:

```jsx
<Student skill="React"></Student>
```

or

```jsx
<Student skill="React" />
```

## Receiving Props

```jsx
function Student(props) {
  return (
    <div>
      <p>Skill: {props.skill}</p>
    </div>
  );
}
```

`props` is an object containing all attributes passed to the component.

## Destructuring Props

Instead of writing:
- `props.skill`
- `props.experience`

We can destructure:

```jsx
function Student({ skill, experience }) {
  return (
    <div>
      <p>Skill: {skill}</p>
      <p>Experience: {experience}</p>
    </div>
  );
}
```

# Understanding Destructuring

## Object:

```javascript
const props = {
  studentName: "Shafi",
  studentId: "123"
};
```

## Correct destructuring:

```javascript
const { studentName, studentId } = props;
```

## After destructuring:
- `studentName` // "Shafi"
- `studentId`   // "123"

*The variable names must match the property names.*

## Default Values

```jsx
function Student({ skill, experience = 0 }) {
  return (
    <p>{experience}</p>
  );
}
```

If no `experience` value is passed, React will use `0`.

## Important
- Props are read-only.
- We should never modify props inside a component.

## Import and Export

### When a component is in another file:
- **Export:**
  ```javascript
  export default Student;
  ```
  
a file can have only one default export.
- **Import:**
  ```javascript
  import Student from "./Student";
  ```
and then we can use:
```javascript
<Students />
```

# Conditional Rendering

React allows us to render different JSX based on conditions.

## Example:

```jsx
function Student({ skill, experience }) {
  if (experience > 5) {
    return (
      <div>
        <p>Skill: {skill}</p>
        <p>Experience: {experience} years</p>
      </div>
    );
  }
  return <p>Still learning</p>;
}
```

## Other Ways

### Ternary Operator
`condition ? valueIfTrue : valueIfFalse`

**Example:**

```jsx
{
  experience > 5
    ? <p>Expert</p>
    : <p>Still learning</p>
}
```

### && Operator
`condition && <p>Show this</p>`
- Renders only when the condition is true.

### || Operator
`value || "Default Value"`
- Usually used for fallback values when the left side is falsy.


# Storing JSX in a Variable

JSX can be assigned to a variable.

```jsx
function Student({ skill, experience }) {

  let task;

  if (experience > 5) {
    task = <p>Experienced Developer</p>;
  } else {
    task = <p>Still learning</p>;
  }

  return task;
}
```

# JavaScript Inside JSX

Inside `{}` we can write JavaScript expressions.

Examples:
- `{name}`
- `{age + 5}`
- `{isActive ? "Yes" : "No"}`


# Rendering Lists with `map()`

## When we want to work with every element of an array, we often use `map()`.

### Example:

```jsx
function App() {
  const heroes = ["Tom", "Mark", "Jack", "Sam"];
  return (
    <>
      {
        heroes.map(hero =>
          <Hero hero={hero}></Hero>
        )
      }
    </>
  );
}

function Hero({ hero }) {
  return <li>{hero}</li>;
}
```

# Rendering Lists with `map()`

## When we want to work with every element of an array, we often use `map()`.

### Example:

```jsx
function App() {
  const heroes = ["Tom", "Mark", "Jack", "Sam"];
  return (
    <>
      {
        heroes.map(hero =>
          <Hero hero={hero}></Hero>
        )
      }
    </>
  );
}

function Hero({ hero }) {
  return <li>{hero}</li>;
}
```

### Rendering Objects with `map()`:

```jsx
function App() {
  const heroes = [
    { id: "1", name: "Tom", age: 25 },
    { id: "2", name: "Mark", age: 57 },
    { id: "3", name: "Sam", age: 34 }
  ];

  return (
    <>
      {
        heroes.map(hero =>
          <Hero key={hero.id} hero={hero} />
        )
      }
    </>
  );
}
def function Hero({ hero }) {return (liHero: {hero.name} | Age: {hero.age}li);}
```

# Important

- `key={hero.id}`
- `key` helps React identify elements efficiently when rendering lists.
- Every item in a list should have a unique key.
- `key` is a special React prop and is not accessible inside the child component.
