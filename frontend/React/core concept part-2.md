
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



# Event Handling

In most cases, event handler functions are written above the return statement inside a component.

## Basic Event Handling
- Event names are written in camelCase.
- The function must be passed inside `{}`.
- Do not call the function directly. Pass the function reference.

```jsx
function App() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    alert("clicked");
  };

  return (
    <>
      <section id="center">
        <h1>react+vite</h1>
        <button onClick={handleClick} className="btn">
          Click Me
        </button>
      </section>
    </>
  );
}
```

# Passing Parameters to Event Handlers

If you write:

```jsx
onClick={handleClick(5)}
```

The function will execute immediately during rendering, before the button is clicked.

To pass parameters, wrap the function call inside an arrow function:

```jsx
onClick={() => handleClick(5)}
```

## Example:

```jsx
function App() {
  const [count, setCount] = useState(0);

  const handleClick = (num) => {
    const newNum = num + 5;
    alert(newNum);
  };

  return (
    <> 
      <section id="center">
        <h1>react+vite</h1>
        <button onClick={() => handleClick(10)} className="btn">
          Click Me
        </button>
      </section>
    </>
  );
}
```

# Array Destructuring

Destructuring allows us to extract values from an array into variables.

## Way 1
```javascript
const [first, second] = [20, 50];
// first = 20
// second = 50
```

## Way 2
```javascript
const arr = [20, 50];
const [first, second] = arr;
// first = 20
// second = 50
```

## Way 3
Functions can also be stored inside arrays.
```javascript
function greet() {
  console.log("Hi");
}

const [first, second] = [100, greet];
second(); // calls greet()
```

## Way 4
Destructuring values returned from a function.
```javascript
def dis() {
  return [200, 400];
}

const [first, second] = dis();
console.log(first); // 200
```

# State Hook (`useState`)
`useState()` is used to store and update data inside a component.

## Syntax
```javascript
const [variable, setVariable] = useState(initialValue);
```
- `variable` → current state value 
- `setVariable` → function used to update the state 
- `initialValue` → initial state value 

## Example:
```jsx
function Cricket() {
  const [score, setScore] = useState(0);
  const [six, setSix] = useState(0);

  const handleSingle = () => {
    const newScore = score + 1;
    setScore(newScore);
  };

  const handleSix = () => {
    const newSix = six + 1;
    setSix(newSix);

    const newScore = score + 6;
    setScore(newScore);
  };

  return (
    <div className="student">
      <h2>Score: {score}</h2>
      <h3>Sixes: {six}</h3>

      <button onClick={handleSingle} className="btn">
        Single
      </button>

      <button className="btn">Four</button>

      <button onClick={handleSix} className="btn">
        Six
      </button>
    </div>
 );
}
```

## Important Note:
When a state value changes using a setter function (`setScore`, `setSix`), React re-renders the component and displays the updated value.


# Loading Data from an API Using fetch

## Method 1: Using fetch() Directly

### Step 1: Create a Promise
```javascript
const fetchUser = fetch(
  "https://jsonplaceholder.typicode.com/users"
).then((res) => res.json());
```

- `fetch()` returns a Promise.
- `res.json()` converts the response into JavaScript objects.

### Step 2: Wrap the Component with Suspense
```jsx
<Suspense fallback={<h3>Loading...</h3>}>
  <Users fetchUser={fetchUser}></Users>
</Suspense>
```
- `fallback` specifies what will be shown while the data is loading.
- The Promise is passed to the component as a prop.

### Step 3: Use React's use() Function
```jsx
function Users({ fetchUser }) {
  const users = use(fetchUser);

  console.log(users);

  return (
    <div className="student">
      <h1>Users</h1>
    </div>
  );
}
```
The `use()` function waits for the Promise to resolve and returns the fetched data.

# Complete Example

```jsx
const fetchUser = fetch(
  "https://jsonplaceholder.typicode.com/users"
).then((res) => res.json());

function App() {
  return (
    <>
      <section id="center">
        <h1>react+vite</h1>

        <Suspense fallback={<h3>Loading...</h3>}>
          <Users fetchUser={fetchUser}></Users>
        </Suspense>
      </section>
    </>
  );
}

function Users({ fetchUser }) {
  const users = use(fetchUser);

  console.log(users);

  return (
    <div className="student">
      <h1>Users</h1>
    </div>
  );
}
```

# Loading Data Using Async/Await

## Step 1: Create an Async Function

`await` can only be used inside an async function.

```javascript
const fetching = async () => {
  const res = await fetch(
    "https://jsonplaceholder.typicode.com/users"
  );

  return res.json();
};
```

## Step 2: Call the Function Inside the Component

Call the async function inside the component and store the returned Promise.

```jsx
function App() {
  const userPromise = fetching();

  return (
    <> 
      <section id="center">
        <h1>react+vite</h1>
        
        <Suspense fallback={<h3>Loading...</h3>}>
          <Users userPromise={userPromise}></Users>
        </Suspense>
      </section>
    </>
  );
}
```

## Step 3: Use the Promise with `use()`

```jsx
function Users({ userPromise }) {
  const users = use(userPromise);

  return (
    <div className="student">
      <h1>Users</h1>
      
      {users.map((user) => (
        <Friend key={user.id} user={user}></Friend>
      ))}
    </div>
  );
}
```

# Display Individual User Data

```jsx
function Friend({ user }) {
  const { name, username } = user;

  return (
    <div className="card">
      <h3>Name: {name}</h3>
      <p>Username: {username}</p>
    </div>
  );
}
```

## Note

- The API returns a property called **username**, not **uname**.
- Correct destructuring:

```jsx
const { name, username } = user;
```
- Incorrect destructuring:

```jsx
const { name, uname } = user;
```
