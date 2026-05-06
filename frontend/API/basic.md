<details>
    <summary><b>Hand Note</b></summary>

        // console.log('hello from js');

// const person = {
//     name: 'shafi',
//     id: 123445,
//     isRich: false,
//     friends:['rahim','karim','ratul']
// }
// console.log(person); //{name: 'shafi', id: 123445, isRich: false, friends: Array(3)}

// const personJson = JSON.stringify(person);
// console.log(personJson); //{"name":"shafi","id":123445,"isRich":false,"friends":["rahim","karim","ratul"]}
// console.log(typeof personJson);//string.. that means JSON.stringify() converts object into string and put key value inside "" notation except number and boolian , also seperate key value using a comma

// const parseJson = JSON.parse(personJson);
// console.log(parseJson);//{name: 'shafi', id: 123445, isRich: false, friends: Array(3)}
// console.log(typeof parseJson);//object
// //that means JSON.parse() converts a json(javascript object notation) string into object 


// const result = fetch('https://jsonplaceholder.typicode.com/todos/1');
// console.log(result);// Promise {<pending>}[[Prototype]]: Promise[[PromiseState]]: "fulfilled"[[PromiseResult]]: Response
// // we can access data using a link using fetch() function. it returns a promise in object formate, that means wait for a moment i will give you data

// fetch('https://jsonplaceholder.typicode.com/todos/1')
//     .then((respon) => console.log(respon));//if we wait for any promiss data and after that if we use .then()
// // that means what ever response will be given will store respon parameter


// fetch('https://jsonplaceholder.typicode.com/todos/1')
//     .then((respon) => console.log(respon.json()));// if we want to convert that response data into json then it also give us a promiss, that means we have to use .then() function to know what kind of data it gave me

// fetch('https://jsonplaceholder.typicode.com/todos/1')
//     .then((respon) => respon.json())
//     .then((data) => console.log(data));//.json() function give us data in object format


// fetch('https://jsonplaceholder.typicode.com/todos/1')
//     .then(response => response.json())
//     .then(json => console.log(json))


// const loadData = () => {
//     fetch('https://jsonplaceholder.typicode.com/todos/1')
//         .then((respon) => respon.json())
//         .then((data) => console.log(data));
// }


// const url = 'https://jsonplaceholder.typicode.com/posts';
// const loadPost = () => {
//     fetch(url)
//         .then((res) => res.json())
//         .then((data) => displayPost(data));

// }

// //get parent
// const postParent = document.getElementById("postList");


// const displayPost = (posts) => {
//     postParent.innerHTML = "";
//     posts.forEach(element => {
//         //create element
//         let li = document.createElement("li");
//         li.innerText = element.title;
//         //append to parent
//         postParent.appendChild(li);
//     });
// }


// "userId": 1,
//     "id": 1,
//         "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
//             "body": "quia et suscipit suscipit recusandae consequuntur expedita et cum reprehenderit molestiae ut ut quas totam nostrum rerum est autem sunt rem eveniet architecto"
// },


// const loadPost = () => {
//     const url = 'https://jsonplaceholder.typicode.com/posts';

//     const postContainer = document.getElementById("post-container");
//     postContainer.innerHTML = "";


//     fetch(url)
//         .then((res) => res.json())
//         .then((posts) => {
//             for (let ele of posts) {
//                 const card = document.createElement("div");
//                 card.innerHTML =
//                     `
//                     <div class="card">
//                         <h2>${ele.title}</h2>
//                         <p>${ele.body}</p>
//                     </div>
//                     `

//                 postContainer.append(card);
//             }

//         })
// }

//need to learn conditional rendaring

/*
GET methode: to get execting data from database
if we want to get whole data:
etch('https://jsonplaceholder.typicode.com/posts') // we will get all data
  .then((response) => response.json())
  .then((json) => console.log(json));


if we want to get one data element we just need to do ..../posts/id number:
etch('https://jsonplaceholder.typicode.com/posts/7') //we will getn number 7 id data
  .then((response) => response.json())
  .then((json) => console.log(json));
*/


/*
POST methode: send data from client side to server side:

fetch('https://jsonplaceholder.typicode.com/posts', { // we want to send data inside this link
  method: 'POST',       //this methode name will be constant
  body: JSON.stringify({  // we have to send object, but before sending we have to convert it into json format
    title: 'foo',       // we will just change this body section to send our custome data
    body: 'bar',
    userId: 1,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8', this header section will be constenet
  },
})
  .then((response) => response.json()) //. to get data we will use these two line
  .then((json) => console.log(json));

  output:
  {
  id: 101,
  title: 'foo',
  body: 'bar',
  userId: 1
}
*/

/*
DELETE method: just we need to add the id number which one we want to DELETE:

fetch('https://jsonplaceholder.typicode.com/posts/6', { //id 6 will be deleted
  method: 'DELETE',
});

*/

/*
data edit PATCH methode: we need to add the id last of the link and change inside body what we want to update:
//rest of the thing will be same as POST method


fetch('https://jsonplaceholder.typicode.com/posts/7', { // if database does not find id 7 data it does not do anything , but if gets then change it
  method: 'PATCH',
  body: JSON.stringify({
    title: 'data changed',
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
})
  .then((response) => response.json())
  .then((json) => console.log(json));

*/

/*
data edit PUT method:we need to add the id last of the link and change inside body what we want to update:

fetch('https://jsonplaceholder.typicode.com/posts/9', { //here if database does not get id 9 then it will create id 9 and change. here is the difference between PATCH and PUT
  method: 'PUT',
  body: JSON.stringify({
    id: 9,
    title: 'foo',
    body: 'bar',
    userId: 1,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
})
  .then((response) => response.json())
  .then((json) => console.log(json));

*/


/*
HTTP status code:
200:ok
301:moved permanently
302:moved temporarilly
404:not found
500:internal server error
503: service unavaiable
*/


//Async and Await

// fetch('https://jsonplaceholder.typicode.com/posts/1')
//     .then((response) => response.json())
//     .then((json) => console.log(json));

// console.log("hi");
// console.log(true);

// here we are not getting data serial by serial. getting first hi then true then fetching data
//because it takes time to fetch data so browser excute first whatever will take less time .

//we can make it syncronise

const makeSyn = async() => { //we are making this function asyncronus so we have to declare it async

    const res = await fetch('https://jsonplaceholder.typicode.com/posts/1');// it promiss us to give data so it will take time so we have to use await
    //it means wait here untill you get the data
    console.log("hi");

    const json = await res.json(); //same reson to use await
    console.log(json);

    console.log(true);

    // now we will get hi then json data then true
}
makeSyn();
    
</details>

----

# JavaScript JSON, Fetch API, and Async/Await 

## Concept Overview

This covers how JavaScript handles data exchange and asynchronous operations, which is the backbone of any real-world web app.

You are dealing with three layers:

- **Data format** → JSON
- **Communication** → Fetch API
- **Execution control** → Promises / async-await

If you do not understand these deeply, API-based projects will feel confusing.

## JSON Handling (Critical Foundation)
### Why JSON exists
Browsers and servers cannot send raw JavaScript objects over the network. They need a universal format → JSON (JavaScript Object Notation).

### Object → JSON (Serialization)
```javascript
const person = {
    name: 'shafi',
    id: 123445,
    isRich: false,
    friends: ['rahim', 'karim', 'ratul']
};

const personJson = JSON.stringify(person);
```
### What actually happens internally
- Object is converted into a string
- Keys become "double quoted"
- Structure is preserved
- Data becomes transferable over HTTP

### Result:
```json
{"name":"shafi","id":123445,"isRich":false,"friends":["rahim","karim","ratul"]}
```

# JSON → Object (Deserialization)

```javascript
const parsed = JSON.parse(personJson);
```

## What happens
- String is converted back into a real JavaScript object.
- Now you can use `.name`, `.friends`, etc.

## Important Edge Cases
- ❌ Invalid JSON → crashes
- Example:
  ```javascript
  JSON.parse("{name: 'shafi'}"); // ERROR
  ```
- JSON must follow strict rules:
  - Keys must be in double quotes.
  - No trailing commas.

# Fetch API (Core Communication Layer)

## What is fetch() really?
```javascript
const result = fetch(url);
```
- It does **NOT** return data directly.
- It returns a **Promise**.

## Think like this:
> "I will give you data later, not now."

## Understanding Promise Flow (Important)
```javascript
fetch(url)
    .then(res => res.json())
    .then(data => console.log(data));
```
### Step-by-step mental model:
1. `fetch()` → sends request → returns Promise.
2. `.then(res => ...)` → runs when response arrives.
3. `res.json()` → extracts body → returns another Promise.
4. `.then(data => ...)` → final usable data.

## Why `.json()` is another Promise (Common confusion)
- Because parsing also takes time.
- So:
  - `fetch` → Promise
  - `json()` → Promise
- Two async layers.


# HTTP Methods (Real Understanding)

## 1. GET (Read Data)
```javascript
fetch('/posts')
```
- No body
- Only retrieves data

**Mental model:**
> "Give me data"

---

## 2. POST (Create Data)
```javascript
fetch('/posts', {
  method: 'POST',
  body: JSON.stringify({...}),
  headers: {
    'Content-type': 'application/json'
  }
});
```
- Key logic:
  - You MUST send data as JSON string
  - You MUST tell server using headers

**Mental model:**
> "Create new data using this information"

---

## 3. DELETE (Remove Data)
```javascript
fetch('/posts/6', { method: 'DELETE' });
```

**Mental model:**
> "Delete item with ID 6"

---

# 4. PATCH (Partial Update)

```javascript
fetch('/posts/7', {
  method: 'PATCH',
  body: JSON.stringify({ title: 'changed' }),
  headers: { 'Content-type': 'application/json' }
});
```

**Only updates specific fields.**

# 5. PUT (Full Replace)

```javascript
fetch('/posts/9', {
  method: 'PUT',
  body: JSON.stringify({
    id: 9,
    title: 'foo',
    body: 'bar',
    userId: 1
  }),
});
```

## Key difference:

| PATCH | PUT |
| --- | --- |
| Partial update | Full replace |
| Keeps old fields | Overwrites everything |

# Rendering Data in DOM (Very Important for Projects)

## Code
```javascript
const displayPost = (posts) => {
    const container = document.getElementById("post-container");
    container.innerHTML = "";

    posts.forEach(post => {
        const div = document.createElement("div");

        div.innerHTML = `
            <div class="card">
                <h2>${post.title}</h2>
                <p>${post.body}</p>
            </div>
        `;

        container.appendChild(div);
    });
};
```

## What is happening step-by-step
- Clear old UI (`innerHTML = ""`)
- Loop through API data
- Create new DOM elements
- Inject dynamic data (`${}`)
- Append to page


# Asynchronous Behavior (Very Important Concept)

## Problem
```javascript
fetch(url);
console.log("hi");
```

**Output:**

```
hi
(data later)
```

**Because:**
- JavaScript does **NOT wait**
- It runs **fast code first**

## async / await (Clean Solution)

### Code
```javascript
const makeSyn = async () => {
    const res = await fetch(url);
    console.log("hi");
    const data = await res.json();
    console.log(data);
    console.log(true);
};
```

### Real Execution Flow
- Function marked `async`
- `await fetch()` → pauses execution
- When response comes → continue
- `await res.json()` → pauses again
- Final output becomes sequential:
  
  ```plaintext
  hi
  (data)
  true
  ```
---
---
## Error Handling (important)
### Correct way:
```javascript
const loadData = async () => {
    try {
        const res = await fetch(url);
        if (!res.ok) {
            throw new Error("HTTP error")
        }
        const data = await res.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
};
```

<details>
  <summary><b>Details explanition about Try...Catch</b></summary>

  # Step 1: Basic Idea

`try...catch` is used to handle runtime errors (errors that happen while the code is running).

```javascript
try {
    // code that might break
} catch (error) {
    // runs if error happens
}
```

# Step 2: Simple Example

```javascript
try {
    console.log(a); // 'a' is not defined → error
} catch (error) {
    console.log("Error caught");
}
```

## What Happens Step-by-Step:
- `try` block starts
- `console.log(a)` → error occurs
- JavaScript stops execution inside `try` immediately
- Jumps to `catch`
- Executes `catch` block

### Output:
```
Error caught
```

# Step 3: Important Rule

👉 When an error happens:
- Remaining code inside `try` is skipped.
- Control goes directly to `catch`.

# Step 4: Accessing the Error
```javascript
try {
    console.log(a);
} catch (error) {
    console.log(error);
}
```

You get details like:
- Error message
- Error type

# Step 5: No Error Case
```javascript
try {
    console.log("Hello");
} catch (error) {
    console.log("This will NOT run");
}
```

**Output:**

Hello

👉 *Catch only runs if an error occurs*

# Step 6: Using `throw` (Very Important)

You can manually create an error:
```javascript
try {
    throw new Error("Something wrong");
} catch (error) {
    console.log(error.message);
}
```

**Output:**

Something wrong

# Step 7: Why `throw` is Needed (Connect with `fetch`)

Earlier problem:
```javascript
const res = await fetch(url);
```
even if status = 404 → no error.
s0, you do:
```javascript
if (!res.ok) {
    throw new Error("HTTP error");
}
the now:
you force an error, and catch will run.
```

# Step 8: async + try/catch

Works only with `await`

```javascript
const loadData = async () => {
    try {
        const res = await fetch(url);
        const data = await res.json();
        console.log(data);
    } catch (error) {
        console.log("Error:", error);
    }
};
```

# Step 9: What try-catch CANNOT catch

This is where many get confused.

❌ **It does NOT catch async errors without await**

```javascript
try {
    fetch(url); // no await
} catch (error) {
    console.log("Will NOT run");
}
```

**Because:**
- `fetch()` runs later (async)
- `try-catch` already finished

# Step 10: Correct way for async

```javascript
try {
    const res = await fetch(url); // now it can catch
} catch (error) {
    console.log("Caught");
}
```

# Final Understanding

- **try** → run risky code
- **catch** → runs only if an error happens
- **throw** → manually create an error
- **await** → required to catch async errors

## One-line Memory Rule

> try-catch only works for errors that happen inside it and at that moment


</details>

---
---


<details>
  <summary><b>Details explanition about Error Handling</b></summary>

  # Step 1: What You Expect vs Reality

## You Think:

```javascript
try {
    const res = await fetch(url);
} catch (error) {
    console.log("error");
}
```

## You Expect:

* If URL is wrong → catch runs

## Reality:

❌ Not always

# Step 2: What fetch() Actually Does

fetch() only fails in one situation:

✅ **Case A: Network problem**
- No internet
- Server unreachable
- → catch runs

❌ **Case B: Server returns error (404, 500)**

### Example:
```javascript
fetch('https://jsonplaceholder.typicode.com/posts/9999')
```
- Server responds: 404
- But response still comes back.

**So:**
fetсh() says → “I got a response”
❌ No error thrown 
❌ catch NOT triggered


# Step 3: What is inside `res`

```javascript
const res = await fetch(url);
```

`res` contains:
- `res.status` // e.g., 404
- `res.ok` // false

## So:
- `res.ok === true` → everything fine
- `res.ok === false` → something wrong (e.g., 404, 500)

# Step 4: YOU must check it

**This is the missing step:**
```javascript
if (!res.ok) {
    throw new Error("Something went wrong");
}
```

*Now you are manually saying:*
> "If server response is bad → treat it as error"

# Step 5: Full correct flow
```javascript
try {
    const res = await fetch(url);

    // Step 1: check response
    if (!res.ok) {
        throw new Error("HTTP error");
    }

    // Step 2: get data
    const data = await res.json();

    console.log(data);
} catch (error) {
    console.log("Error:", error.message);
}
```


# Step 6: What Happens in 3 Situations

## ✅ Case 1: Good Request (200)
- `fetch()` → success
- `res.ok = true`
- Data prints

## ❌ Case 2: 404 Error
- `fetch()` → still success
- `res.ok = false`
- Throw error runs → goes to catch

## ❌ Case 3: No Internet
- `fetch()` fails → directly goes to catch

---

## Final Understanding (Keep This in Your Head)
- `fetch()` only cares: “Did I get a response?”
- It does NOT care: “Is the response correct?”

---

## So:
- `catch` → handles network errors
- `res.ok` → handles HTTP errors


  
</details>

# Common Mistakes (You are close to these)
- Thinking `fetch()` returns data directly ❌
- Forgetting second `.then()` after `.json()` ❌
- Not using `await` for `.json()` ❌
- Not handling errors ❌
- Confusing PATCH vs PUT ❌

# Key Takeaways
- JSON is required for client-server communication
- `fetch()` always returns a Promise
- `.json()` is also asynchronous
- Async code runs out of order unless controlled
- `async/await` makes code predictable and readable
- HTTP methods define intent (read, create, update, delete)
