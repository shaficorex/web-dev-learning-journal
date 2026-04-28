<details>
    <summary><b>Hand Note</b></summary>

    ```html
    <!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body id="bd">
    <h1>dom doma dom event</h1>
    <!-- way 1 for event handeling -->
    <!-- if we write on then we will get so many event attribute suggestion
    if we click 7 will be the output -->
    <button onclick="console.log(7)">click me</button>
    <!-- inside "" double quate we habe to use single quate '', or we can do alternate like using '' inside "" -->
    <button onclick="console.log('hi how are you')">get string</button>

    <br>

    <!-- way 2 for event handeling -->
    <!-- we can put a function call inside event atribute value, that means when an event will hapen you will call this function -->
    <button onclick="bgBlue()">change bg</button>
    <!-- we can write this script in different file and make a connecction -->
    <script>
        function bgRed() {
            document.getElementById("bd").style.backgroundColor = "red";
        }

        function bgBlue() {
            document.getElementById("bd").style.backgroundColor = "blue";

        }
    </script>

    <!-- way 3 -->
    <br>
    <button id="btn-bg-green">way 3</button>
    <script>
        const btnBgGreen = document.getElementById("btn-bg-green");
        btnBgGreen.onclick = function () {
            document.getElementById("bd").style.backgroundColor = "green";
        }
    </script>


    <!-- way 4 addEventListener -->
    <!-- ebst practise -->
    <br>
    <button id="btn-make-purple">bg purple</button>

    <script>
        // document.getElementById("btn-make-purple").addEventListener("event type",handler function)
        //note: here event name will be without on
        document.getElementById("btn-make-purple").addEventListener("click",
            function () {
                document.getElementById("bd").style.backgroundColor = "purple";
            }
        )
    </script>

    <!-- try to change h1 text by click event -->

    <br>
    <br>
    <br>
    <p id="name-area">No Name</p>
    <input id="input-name" type="text" placeholder="your name"> <button id="btn-change-name">change name</button>

    <script>
        document.getElementById("btn-change-name").addEventListener("click",
            function () {
                //get input value
                const inputName = document.getElementById("input-name").value;
                //change name
                document.getElementById("name-area").innerText = inputName;

            }
        )
    </script>

    <!-- innerText → what user sees
value → what user types -->

    <br>
    <br>
    <br>

    <h1>my secret code</h1>
    <input id="secreet-code" type="text">
    <button id="btn-delete" disabled>delete</button>

    <script>
        document.getElementById("secreet-code").addEventListener("keyup",
            function (event) {
                // console.log(event);//if i press e it will show all the event: KeyboardEvent {isTrusted: true, key: 'e', code: 'KeyE', location: 0, ctrlKey: false, …}
                // console.log(event.target); // target will give us where event occoured <input id="secreet-code" type="text"> 
                // //now if we do value we will get what we have typed
                // console.log(event.target.value);

                const text = event.target.value;
                const btnDelete = document.getElementById("btn-delete");
                if (text === "delete") {
                    console.log("delete typed");
                    btnDelete.removeAttribute("disabled");
                }
                else {
                    console.log("something else");
                    btnDelete.setAttribute("disabled",true);
                }
            }
        )
    </script>


<!-- event bubbling:
 when any event triggers then browser start to find it from top to bottom means html->body->section->ol->li
 
 step2: when browser finds the target the event occure
 step3: now it will go on top and if on the way it gets any eventhandler it will triggers it
 
 we can do event.stopPropagation and event.stopImmediatePropagation for stop bubbling-->


 <!-- event deligation
  need to leran it in details way -->


</body>

</html>
    ```
</details>


# Event Handling in JavaScript

## Concept Overview

Event handling in JavaScript allows you to execute code in response to user interactions such as clicks, typing, or mouse movements. These interactions are called **events**, and JavaScript provides multiple ways to handle them.

## Key Principles
- An event is an action triggered by the user or browser.
- An event handler is a function that runs when the event occurs.
- Events can be attached in different ways, but some methods are better for scalability and maintainability.

## Methods of Event Handling

### 1. Inline Event Handling (HTML Attribute)

Attach events directly inside HTML elements.

```html
<button onclick="console.log(7)">click me</button>
<button onclick="console.log('hi how are you')">get string</button>
```
**Explanation:**
- The `onclick` attribute directly executes JavaScript code.
- Simple but not recommended for large applications.

### 2. Calling a Function from HTML

Define a function in JavaScript and call it from HTML.

```html
<button onclick="bgBlue()">change bg</button>
```
```javascript
<script>
function bgBlue() {
    document.getElementById("bd").style.backgroundColor = "blue";
}
</script>
```
**Explanation:**
- Cleaner than inline code.
- Still mixes HTML and JavaScript logic.


# 3. Using DOM Property (`element.onclick`)

Assign a function to an element’s event property.

```javascript
const btnBgGreen = document.getElementById("btn-bg-green");

btnBgGreen.onclick = function () {
    document.getElementById("bd").style.backgroundColor = "green";
};
```

## Explanation
- Keeps JavaScript separate from HTML.
- Only one handler can be assigned per event (overwrites previous).

# 4. Using `addEventListener` (Best Practice)

Attach event listeners using JavaScript.

```javascript
document.getElementById("btn-make-purple").addEventListener("click", function () {
    document.getElementById("bd").style.backgroundColor = "purple";
});
```

## Explanation
- Most flexible and scalable method.
- Allows multiple event listeners on the same element.
- Cleaner separation of concerns.

# Working with Input and DOM Manipulation

## Example: Updating Text from Input

```javascript
document.getElementById("btn-change-name").addEventListener("click", function () {
    const inputName = document.getElementById("input-name").value;
    document.getElementById("name-area").innerText = inputName;
});
```

## Key Concepts
- `.value` → retrieves user input from input fields.
- `.innerText` → updates visible text content in elements.


# Keyboard Events and Dynamic Validation

## Example: Enable Button on Specific Input
```javascript
document.getElementById("secreet-code").addEventListener("keyup", function (event) {
    const text = event.target.value;
    const btnDelete = document.getElementById("btn-delete");

    if (text === "delete") {
        btnDelete.removeAttribute("disabled");
    } else {
        btnDelete.setAttribute("disabled", true);
    }
});
```

## Step-by-Step Logic
- `keyup` event triggers when a key is released.
- `event.target` gives the element where the event occurred.
- `.value` gets the current input.
- Condition checks if input matches "delete".
- Button is enabled/disabled accordingly.

## Event Object
When an event occurs, JavaScript provides an event object containing useful information.
```javascript
function (event) {
    console.log(event);
    console.log(event.target);
}
```

## Important Properties
| Property | Description |
| --- | --- |
| `event.target` | The element that triggered the event |
| `event.type` | Type of event (`click`, `keyup`, etc.) |

## Event Bubbling
### Concept
Event bubbling describes how events propagate in the DOM.

### Flow
1. Event starts from the root (`html` → `body` → ...)
2. Reaches the target element
3. Bubbles back up to the root

### Control Bubbling
- `event.stopPropagation();`
event.stopImmediatePropagation();`
- `stopPropagation()` stops the event from moving upward.
- `stopImmediatePropagation()` stops all further handlers.

-----------------------
<details>
  <summary><b>Event Bubbling (Deep Explanation)</b></summary>

  # Core Idea

When an event happens on an element, it does not stay there. It travels through the DOM in a specific order.

## Actual Flow (3 Phases)
- **Capturing phase** (top → target)
  - html → body → parent → child
- **Target phase**
  - Event reaches the exact element clicked
- **Bubbling phase** (target → top)
  - child → parent → body → html

By default, JavaScript handles events in the bubbling phase.

## Example
```html
<div id="parent">
    <button id="child">Click me</button>
</div>
```
```javascript
document.getElementById("parent").addEventListener("click", function () {
    console.log("parent clicked");
});

document.getElementById("child").addEventListener("click", function () {
    console.log("child clicked");
});
```

**If you click the button:**
- child clicked
- parent clicked

**Why?**
- Event first happens on button (target)
- Then bubbles up to parent

## Stop Bubbling
```javascript
document.getElementById("child").addEventListener("click", function (event) {
    event.stopPropagation();
    console.log("child only") ; 
}); 
```
**Now output:**
- child only

## Important Points
- Bubbling is default behavior.
- Parent handlers can run even if you clicked a child.
- Can cause bugs if not understood.
</details>

-------------

# Event Delegation (Concept)

Instead of adding event listeners to multiple child elements, attach a single listener to a parent and handle events using `event.target`.

## Useful for:
- Dynamic elements
- Performance optimization

----------------------------
<details>
  <summary><b>Event Delegation (Deep Explanation)</b></summary>

  # Core Idea

Instead of attaching event listeners to multiple child elements, attach one listener to the parent and detect which child triggered the event.

This works because of **event bubbling**.

## Problem Without Delegation
```javascript
const items = document.querySelectorAll("li");

items.forEach(item => {
    item.addEventListener("click", function () {
        console.log("item clicked");
    });
});
```
**Issues:**
- Adds many event listeners (memory cost)
- Does not work for dynamically added elements

## Solution: Event Delegation
```javascript
document.getElementById("list").addEventListener("click", function (event) {
    console.log(event.target);
});
```

## Example HTML
```html
<ul id="list">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```
If you click "Item 2":
`<li>Item 2</li>`


# Target Filtering (Important)

You usually don’t want clicks on the parent, only specific children.

```javascript
// Event listener for clicks on the list
document.getElementById("list").addEventListener("click", function (event) {
    if (event.target.tagName === "LI") {
        console.log("Clicked:", event.target.innerText);
    }
});
```

## Handling Dynamic Elements

```javascript
const list = document.getElementById("list");

// Event delegation for existing and future list items
list.addEventListener("click", function (event) {
    if (event.target.tagName === "LI") {
        event.target.remove();
    }
});

// Dynamically adding a new item
const li = document.createElement("li");
li.innerText = "New Item";
list.appendChild(li);
```

No extra event listener is needed for the new item.


# When to Use Event Delegation

## Use it when:
- Many similar child elements exist
- Elements are added dynamically
- Performance matters

## Avoid it when:
- You need strict control per element
- Events don’t bubble (e.g., focus, blur)

# Key Takeaways
- Event bubbling moves events upward in the DOM
- `event.stopPropagation()` stops bubbling
- Event delegation uses bubbling to handle multiple elements efficiently
- `event.target` is the key to delegation
- Delegation is more scalable and performant than attaching multiple listeners
</details>

------------------------------

## Important Notes
- Prefer `addEventListener` for real-world applications.
- Avoid inline event handling in production code.
- Always separate HTML structure and JavaScript logic when possible.
- Be careful with exact string matching (e.g., "delete" is case-sensitive).

## Common Mistakes
- Using `.innerText` instead of `.value` for input fields.
- Overwriting events using `onclick` instead of `addEventListener`.
- Forgetting that event names in `addEventListener` do not use `on` (use "click", not "onclick").
- Ignoring event propagation, leading to unexpected behavior.

## Key Takeaways
- There are four main ways to handle events, but `addEventListener` is preferred.
- The event object provides powerful control and context.
- DOM manipulation allows dynamic UI updates.
- Event bubbling and delegation are essential for advanced event handling.
