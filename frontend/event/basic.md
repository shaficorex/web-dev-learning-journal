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
