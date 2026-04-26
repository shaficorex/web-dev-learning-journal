```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        h1 {
            color: aqua;
        }

        .bg {
            background-color: blue;
        }

        .sz {
            font-size: 3em;
        }
    </style>

    <link rel="stylesheet" href="./styles.css">
</head>

<body>
    <h1 id="title1">wellcome to my dom</h1>
    <h1>how are you</h1>

    <ul id="list">
        <li>song-1</li>
        <li id="bestSong" class="good bg">song-2</li>
        <li class="good">song-3</li>
    </ul>

    <script>
        console.log("hello from javascript");
    </script>
    <script src="./js/hello.js"></script>
</body>

</html>

```


# DOM (Document Object Model) in JavaScript

## Concept Overview

The DOM (Document Object Model) is a tree-like representation of an HTML document created by the browser. JavaScript interacts with this structure to read, modify, and update content dynamically, making web pages interactive.

## Key Principles
- The browser converts HTML into a DOM tree.
- Each HTML element becomes a node (object).
- JavaScript accesses and manipulates these nodes using the `document` object.
- Elements are structured in parent-child relationships.

## Connecting JavaScript to HTML

### Inline Script
Placed before the closing `</body>` tag:
```html
<script>
    console.log("hello from javascript");
</script>
```

### External Script
```html
<script src="./js/hello.js"></script>
```

### Execution Order Rule (FIFO)
Scripts run from top to bottom in the order they appear.

# Accessing the DOM

## Entire Document
```javascript
console.log(document);
```

## Select by Tag Name
```javascript
document.getElementsByTagName("h1");
```
**Returns:** an `HTMLCollection` (Array-like, but not a real array)

## Select by ID
```javascript
document.getElementById("title1");
```
**Returns:** a single element, not a collection

## Select by Class Name
```javascript
document.getElementsByClassName("good");
```
**Returns:** an `HTMLCollection`

## Query Selectors (Modern Approach)
```javascript
// First match:
document.querySelector("ul .good");
// All matches:
document.querySelectorAll("ul .good"); // returns a NodeList
```
Supports `forEach` on NodeList.


# Looping Through Elements

```javascript
for (const ele of document.getElementsByTagName("li")) {
    console.log(ele.innerText);
}
```

## NodeList vs HTMLCollection
| Feature | NodeList | HTMLCollection |
|---------|----------|----------------|
| Source  | querySelectorAll | getElementsBy... |
| Type    | Any nodes | Only elements |
| Live    | ❌ Static | ✅ Live |
| forEach | ✅        | ❌             |

## Modifying Elements
### Style Manipulation
```javascript
const title = document.getElementById("title1");
title.style.color = "red";
```

**Note:**
- CSS `margin-left` → JS `marginLeft`

### Class Manipulation
```javascript
const song = document.getElementById("bestSong");
song.classList.add("sz");
song.classList.remove("bg");
```

### Attributes
```javascript
// Get attribute value
toStringAttribute="id";
song.getAttribute("id")
// Set attribute value
toStringAttribute="title";
song.setAttribute("title", "this is the best song")
```

## innerText vs innerHTML
| Property     | Description                     |
|--------------|---------------------------------|
| innerText   | Visible text only               |
| innerHTML   | Full HTML content (tags + text)|




# DOM Traversing

```javascript
const bd = document.getElementById("list");

bd.childNodes;
bd.parentNode;
```

## Creating and Adding Elements

### Step-by-Step Logic
1. Create element
2. Add content
3. Select parent
4. Append to parent

### Example
```javascript
const newEle = document.createElement("li");
newEle.innerText = "song-4";

const par = document.getElementById("list");
par.appendChild(newEle);
```

### Using innerHTML
```javascript
const newElement = document.createElement("li");
newElement.innerHTML = `
<ul>
    <li>bangla</li>
    <li>english</li>
    <li>spanish</li>
</ul>
`;
par.appendChild(newElement);
```

## Important Notes
- If no element is found:
  - `querySelector` → null
  - `querySelectorAll` → empty NodeList
  - `getElementsBy...` → empty HTMLCollection
- Collections are array-like, not real arrays.
- `getElementById()` returns a single element (not NodeList).

## Common Mistakes
- Assuming `getElementById()` returns a collection.
- Using `forEach` on HTMLCollection.
- Forgetting camelCase in style properties.
- Confusing `innerText` with `innerHTML`.
- Thinking all collections are static (`HTMLCollection` is live). 
 
## Key Takeaways 
- DOM is the bridge between HTML and JavaScript.
- Use `querySelector` / `querySelectorAll` for flexibility.
- Understand the difference between NodeList and HTMLCollection.
- DOM manipulation involves selecting, modifying, and creating elements.
- Proper script placement avoids loading issues.
