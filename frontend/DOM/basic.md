<details>
    <summary><b>Hand Note</b></summary>

```html

Dom

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        h1{
            color: aqua;
        }
        .bg{
            background-color: blue;
        }

        .sz{
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
        <li  id="bestSong" class="good bg">song-2</li>
        <li class="good">song-3</li>
    </ul>

    <script>
        console.log("hello from javascript");
    </script>
    <script src="./js/hello.js"></script>
</body>
</html>







How to connect javascript?
<script>
        console.log("hello from javascript");
    </script>
Keep this imediet upper of closing body tag.if we do inspect we can see hello from javascript inside the console.

To connect js file inside index.html file which is outside

<script src="./js/hello.js"></script>

Note: the exception of script file deepens on fifo, means whatever script file on top will execute first

console.log(document);
Here whole html file is a document object and all the elements are property,
We can access those element how we accesss property from an object.
It organise everything from parents to child like a tree

Note: browser makes dom from html and javascript uses that dom to manipulate anything in website. Dom makes thee website interactive

Note:if we do document. Then we will get so many property


console.log(document.getElementsByTagName("h1"));// we will get a array like object and its elements will be all the h1 tags inside whole html,
//if we click dropdown of any of the h1 , we will get the propertys of h1, like innerHtml, inner Text.


for (const ele of document.getElementsByTagName("li")) //as we are gettting an atrray we can do for..of to loop it
{
    console.log(ele.innerText); //innerText to get text value inside the tag
}

// if we want we can change the inner text as well

Note: we can get particularly one element from same tag name
We can use an id for that element and use document.getElementsById


Note: if we want to get a particular group of elements , then we can give those elements. A class name and use  document.getElementsClassName.
Here also we will get array like object collection. And we can do loop it and get innerText as well

Note: if dom do not get anything it will return a empty collection , that means null


console.log(document.querySelectorAll("ul .good"));
If we use  querySelectorAll() then we can use any css selector to get the elements. It gives us novelist which array like object. If no element found it will give empty nodelist 

Note: querySelector("ul .good") will give only the first element. If no element found it will give null.


1. NodeList
Example

const nodes = document.querySelectorAll("li");

Features
* Can contain any nodes (usually elements)
* Static (does NOT update automatically)
* Supports:

nodes.forEach(...)


2. HTMLCollection
Example

const items = document.getElementsByTagName("li");

Features
* Contains only HTML elements
* Live (updates automatically when DOM changes)
* Does NOT support forEach directly

Key Differences
Feature	NodeList	HTMLCollection
Source	querySelectorAll	getElementsBy...
Type	any nodes	only elements
Live or Static	❌ Static	✅ Live
forEach	✅	❌
Updates automatically	❌	✅


Dom traversing means finding right element from the dom


console.log(document.querySelectorAll("ul .good"));

const title = document.getElementById("title1");
console.log(title.style);//we will get all the style for that elements
//now if we do dot then we can get access all the css style attribute like color, gap,padding,margin
//then we can assign new style
console.log(title.style.color);
title.style.color = "red"; //.color is a attribute name and "red" is a attribute value
console.log(title.style.color);//red
//note: margin-left is a css attribute, but in javascript we will write marginLeft, that means no hyphen and uppercase of the imidiate letter from hyphen


Note: if we do getElementById() it will always give us nodeList, then we can go to childNode or parentNode.


Note:if we get any array like collection or array like nodeList, I mean anything inside [] then we can run for..of loop on it



console.log("hello from hello.js file");
console.log(document.getElementsByTagName("h1"));// we will get a array like object and its elements will be all the h1 tags inside whole html,
//if we click dropdown of any of the h1 , we will get the propertys of h1, like innerHtml, inner Text.


for (const ele of document.getElementsByTagName("li")) //as we are gettting an atrray we can do for..of to loop it
{
    console.log(ele.innerText); //innerText to get text value inside the tag
}

console.log(document.querySelectorAll("ul .good"));

const title = document.getElementById("title1");
console.log(title.style);//we will get all the style for that elements
//now if we do dot then we can get access all the css style attribute like color, gap,padding,margin
//then we can assign new style
console.log(title.style.color);
title.style.color = "red"; //.color is a attribute name and "red" is a attribute value
console.log(title.style.color);//red
//note: margin-left is a css attribute, but in javascript we will write marginLeft, that means no hyphen and uppercase of the imidiate letter from hyphen


const song = document.getElementById("bestSong");
console.log(song.classList);// DOMTokenList(2) ['good', 'bg', value: 'good bg']
//it will show all the classes for that elements
song.classList.add("sz"); // we can add a new class
song.classList.remove("bg");// we can remove a class from an element


console.log(song.getAttribute("id"));//bestSong
// id="bestSong"  here id is an attribute and bestSong is its value
//like this way we can get the value of any attribute

song.setAttribute("title", "this is the best song");//here title:"this is the best song"
// we have to pass the attribute name and its value



//innerText vs innerHtml
//innerText: we will get just visible text of an element, not the comment
//innerHtml:we will get all the html tags and comment and text inside that element



let bd = document.getElementById("list")
console.log(bd.childNodes);
console.log(bd.parentNode);


//1.create element and set innerText
const newEle = document.createElement("li");
newEle.innerText = "song-4";

//2.find the parent where you will keep the newelement
const par = document.getElementById("list")

//33.append newele inside the parent
par.appendChild(newEle);


//with innerhtml
const newElement = document.createElement("li"); //create element
//set element
newElement.innerHTML = 
`
<ul>
    <li>bangla</li>
    <li>english</li>
    <li>spanish</li>
</ul>
`
//apppend element
par.appendChild(newElement);




```
</details>




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
