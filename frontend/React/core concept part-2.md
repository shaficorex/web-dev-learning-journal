
<details>
  <summary><b>Hand Note</b></summary>

  React core concept-2

Most of the case we will write function for even handling  right above of return of a component.

While  writing o’clock we have to write in camel case and write the handle function inside a {} inside {} do not call the function , just write function name.

unction App() {
  const [count, setCount] = useState(0)

  const handleClick = ()=>{
    alert("clicked");
  }

  return (
    <>
      <section id="center">
        <h1>react+vit</h1>
        <button onClick={handleClick} className='btn'>click me</button>
      </section>
    </>
  )
}


But if we want to pass a parameter then if we do onClick={handleClick(5)} then it will call the function before clicking. For this situation we have to wrap with an arrow function during calling. Like onClick={()=>handleClick(5)}

function App() {
  const [count, setCount] = useState(0)

  const handleClick = (num)=>{
    const newNum = num + 5;
    alert(newNum);
  }

  return (
    <>
      <section id="center">
        <h1>react+vit</h1>
        <button onClick={()=>handleClick(10)} className='btn'>click me</button>
      </section>
    </>
  )
}



//way 1
  //const [first, second] = [20, 50];//here first=20 and second=50

  //way 2
  //const arr = [20, 50];
  //const [first, second] = arr;//here first=20 and second=50

  //way 3
  // function greet()
  // {
  //   console.log("hi");
  // }
  // const [first, second] = [100, greet] //here first=100 and second is greet function
  // second();

  //way 4
  // function dis() {
  //   return [200, 400];
  // }
  // const [first, second] = dis();//here first=200 and second=400
  // console.log(first);


State hook: needs to understand
function Cricket()
{
  const [score, setScore] = useState(0); // initial value of count is 0
  //for distrucring [variable, set+variable]
  const [six, setSix] = useState(0);
  
  const handleSingle = () => {
    const newScore = score + 1;
    setScore(newScore);
  }
  const handleSix = () => {
    const newSix = six + 1;
    setSix(newSix);

    const newScore = score + 6;
    setScore(newScore);
  }
  return (
    <div className='student'>
      <h2>score: {score}</h2>
      <h3>sixes: { six}</h3>
      <button onClick={handleSingle} className='btn'>single</button>
      <button className='btn'>four</button>
      <button onClick={handleSix} className='btn'>six</button>
    </div>
  )
}



How to load data from API using fetch:

1.Normally fetch data from api  and keep this as a global: 
const fetchUser = fetch('https://jsonplaceholder.typicode.com/users')
  .then((res) => res.json());  //promiss

2.call the component inside suspense:

<Suspense fallback={<h3>loading...</h3>}>
          {/* during data fetching what it will show does by fallback function */}
          <Users fetchUser={fetchUser}></Users>
          {/* send fetch data to the component  */}
        </Suspense>

3.use that passing data inside the use function  inside the component. Use function helps to get data

function Users({ fetchUser }) {
  const users = use(fetchUser);
  console.log(users);
  return (
    <div className='student'>
      <h1>users</h1>
    </div>
  );
}


This is the full code:
const fetchUser = fetch('https://jsonplaceholder.typicode.com/users')
  .then((res) => res.json());  //promiss

function App() {
  
  return (
    <>
      <section id="center">
        <h1>react+vit</h1>
        <Suspense fallback={<h3>loading...</h3>}>
          {/* during data fetching what it will show does by fallback function */}
          <Users fetchUser={fetchUser}></Users>
          {/* send fetch data to the component  */}
        </Suspense>
        
      </section>
    </>
  )
}

function Users({ fetchUser }) {
  const users = use(fetchUser);
  console.log(users);
  return (
    <div className='student'>
      <h1>users</h1>
    </div>
  );
}



With async await:

For first step we have to declare an arrow function because we can not apply async await without a  function.
const fetching = async() => {
  const res = await fetch('https://jsonplaceholder.typicode.com/users');
  return res.json();
}


Second steps we have to call that fetching function inside App function but outside the return . 
function App() {
  const userPromiss = fetching();
  return (
    <>
      <section id="center">
        <h1>react+vit</h1>
        <Suspense fallback={<h3>loading...</h3>}>
          {/* during data fetching what it will show does by fallback function */}
          <Users userPromiss={userPromiss}></Users>
          {/* send fetch data to the component  */}
        </Suspense>
        
      </section>
    </>
  )
}


Then rest of the steps are same as normal fetching
Full code :
const fetching = async() => {
  const res = await fetch('https://jsonplaceholder.typicode.com/users');
  return res.json();
}

function App() {
  const userPromiss = fetching();
  return (
    <>
      <section id="center">
        <h1>react+vit</h1>
        <Suspense fallback={<h3>loading...</h3>}>
          {/* during data fetching what it will show does by fallback function */}
          <Users userPromiss={userPromiss}></Users>
          {/* send fetch data to the component  */}
        </Suspense>
        
      </section>
    </>
  )
}

function Users({ userPromiss }) {
  const users = use(userPromiss);
  return (
    <div className='student'>
      <h1>users</h1>
      {
        users.map(user=><Friend key={user.id} user={user}></Friend>)
      }
    </div>
  );
}

function Friend({user})
{
  const { name,uname} = user;
  return (
    <div className='card'>
      <h3>name: { name}</h3>
      <p>user name: { uname}</p>
    </div>
  )
}

</details>



# Event Handling in React

## What is Event Handling?

An event means something happening in the browser.

### Examples:
- User clicks button
- User types in input field
- User submits form
- User moves mouse

React allows us to respond to these events using functions.

## Basic Structure
```jsx
function App() {
  const handleClick = () => {
    alert("clicked");
  }
  return (
    <button onClick={handleClick}>
      Click Me
    </button>
  )
}
```

## Very Important Understanding
This line:
```jsx
onClick={handleClick}
```
does **NOT** call the function immediately.

Instead:
- React stores the function reference.
- Then later, when the user clicks the button, React calls the function.

## Real Flow Internally
When React sees:
```jsx
<button onClick={handleClick}>
```
it basically remembers:
> "If this button gets clicked, run handleClick function."
Nothing runs immediately.
Only after clicking:
handleClick()
takes place internally by React.


# Why handleClick() is Wrong

If you write:

```jsx
onClick={handleClick()}
```

then JavaScript executes the function immediately during rendering.

**Meaning:**

`handleClick()` runs **BEFORE** the button appears.

That is why an alert appears automatically without clicking.

## Simple Mental Model

### Correct

```jsx
onClick={handleClick}
```

**Meaning:**

"React, call this later."

### Wrong

```jsx
onClick={handleClick()}
```

**Meaning:**

"Run this **NOW**."

## Why Event Names Use camelCase

### HTML:
- `onclick`

### React:
- `onClick`

Because JSX is closer to JavaScript than HTML.
JavaScript naming convention uses camelCase.

## Examples:
- `onClick`
- `onMouseMove`
- `onChange`
- `onSubmit`


# Passing Parameters in Event Handler

## Problem

Suppose:

```javascript
const handleClick = (num) => {
  alert(num);
}
```

Now you want to send `10`.

You may think:

```jsx
onClick={handleClick(10)}
```

But this is wrong.

## Why Wrong?

Because:

```javascript
handleClick(10)
```

e executes immediately during rendering.

So alert appears instantly.

## Correct Solution

```jsx
onClick={() => handleClick(10)}
```

## Deep Explanation of Arrow Function Here

This part:

```jsx
() => handleClick(10)
```

g creates a **NEW FUNCTION**.
This new function does not run immediately.
React stores this function.
After clicking:
- React calls arrow function 
- Arrow function calls `handleClick(10)`

# Internal Visualization

## React stores:

```jsx
() => handleClick(10)
```

**NOT:**

```jsx
handleClick(10)
```

*Huge difference.*

---

## 2. Array Destructuring

### What Problem Does Destructuring Solve?

**Without destructuring:**

```javascript
const arr = [20, 50];
const first = arr[0];
const second = arr[1];
```

*Too much repetitive code.*

### Destructuring Shortcut

```javascript
const [first, second] = [20, 50];
```

JavaScript automatically assigns:
- `first = 20`
- `second = 50`

---

## Visual Understanding

```javascript
const [a, b] = [100, 200];
```

Think like:
- `a` gets the first value (`100`)
- `b` gets the second value (`200`)

---

## Why React Uses Destructuring in useState?

React returns an array:
```jsx
[ currentValue, updatingFunction ] 
```
Example:
```jsx
const [score, setScore] = useState(0);
```
Internally React gives something like:
```jsx
[0, function]
```
and then destructuring happens:
- `score = 0`
- `setScore = function`


# 3. Deep Understanding of `useState`

## Biggest Concept
React components normally forget values after re-render.

**State** solves this problem.

## Why Normal Variable Fails

### Example:
```jsx
function App() {
  let count = 0;

  const increase = () => {
    count++;
    console.log(count);
  }

  return (
    <button onClick={increase}>
      Add
    </button>
  );
}
```
Console increases.

**BUT UI does not update.**

### Why?
Because React does not track normal variables.

## State is Special Memory
```jsx
const [count, setCount] = useState(0);
```
tReact tracks state variables.

## When state changes:
React automatically re-renders UI.

## Full Flow of State Update
Suppose:
```jsx
setCount(5);
```
tReact does these internally:

### Step 1: Store new value.
- `count = 5`

### Step 2: Re-run component function.
- `function App()` runs again.

### Step 3: Generate new JSX.

### Step 4: Compare old UI vs new UI.
tThis process is called:
a **Reconciliation**

### Step 5: Update only changed parts in browser.


# Why React is Fast

React does **NOT** reload the whole page.

It updates only necessary parts.

## Cricket Example Deep Explanation

```jsx
const [score, setScore] = useState(0);
```

### Initially:
- `score = 0`
- UI shows:
  - `score: 0`

### When Clicking Single:
```jsx
const handleSingle = () => {
  const newScore = score + 1;
  setScore(newScore);
}
```

Suppose `score` was 0.
Then:
- `newScore = 1`
- Then:
  - `setScore(1)`

React updates state.
Component re-renders.
Now UI becomes:
- `score: 1`

## Why Functional Update is Better

Instead of:
```jsx
setScore(score + 1);
```
better:
```jsx
setScore(prev => prev + 1);
```

# Why?

Because state updates can be asynchronous.

React may batch updates together.

Using previous value guarantees correct update.

## Example Problem
```javascript
setScore(score + 1);
setScore(score + 1);
```

You may expect `+2`.

But often it becomes `+1`.

Because both use the same old value.

## Correct Version
```javascript
setScore(prev => prev + 1);
setScore(prev => prev + 1);
```

Now the result becomes `+2` correctly.

---

# 4. Fetch API Deep Explanation

## What is an API?

An API is a system that provides data.

### Example API:

[https://jsonplaceholder.typicode.com/users](https://jsonplaceholder.typicode.com/users)

This returns fake user data.

## What Fetch Does

```javascript
fetch(url)
```

Sends a request to the server.

## Important Understanding

Fetching data takes time because data comes through the internet. So JavaScript does **NOT** stop execution.

Instead:
- `fetch()` immediately returns a **Promise**.

## What is a Promise?

A Promise means:
> "I will give result later."

### Three states of a Promise:
- Pending
- Resolved
- Rejected

## Step-by-Step Fetch Flow:
1. ```javascript fetch('https://jsonplaceholder.typicode.com/users') ```
2. Browser sends request.
3. `fetch()` instantly returns a Promise.
4. JavaScript continues running other code.
5. When data arrives, the Promise resolves.

## Why `.json()` Is Needed?
The server sends JSON text, for example:
```json
{
  "name": "Leanne Graham"
}
```
`.json()` converts JSON text into a JavaScript object.



# Understanding Suspense

## Problem Before Suspense

Initially, data is unavailable.

So React cannot render users immediately.

## Suspense Solution

```jsx
<Suspense fallback={<h3>loading...</h3>}>
```

Fallback UI appears while waiting.

Think like:

> "If child component is waiting for async data, show loading text."

## Understanding `use()`

```jsx
const users = use(userPromise);
```

`use()` waits for Promise result.

## Internal Idea

- If Promise is unfinished:
  - React pauses rendering.
  - Suspense shows fallback.
- When Promise resolves:
  - React continues rendering.

## Async Await Deep Understanding
### Why Async Await Exists
Promises with `.then()` can become messy.
Example:
```js
af fetch(url)
  .then(res => res.json())
  .then(data => console.log(data))
```
Async/await makes code look synchronous.
### Deep Explanation
```js
const fetching = async () => {
  // function body here...
}
```
`async` means:
> "This function returns a Promise."
'that means:
the `await` keyword in an async function does the following:
defines an asynchronous operation that pauses execution until the Promise resolves, then resumes with the resolved value.



# Key Takeaways

- React event handlers store function references.
- `onClick={handleClick}` is different from `onClick={handleClick()}`.
- Arrow functions delay execution.
- Destructuring extracts array values cleanly.
- `useState` creates reactive state.
- State updates trigger component re-rendering.
- React updates only changed UI parts.
- `fetch()` returns a Promise because network requests are asynchronous.
- Suspense handles loading UI.
- `use()` waits for Promise data.
- Async/await simplifies asynchronous code.
