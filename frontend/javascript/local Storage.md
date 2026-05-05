# Concept Overview

Local Storage is a Web Storage API that allows websites to store data in the browser as key–value pairs. The data persists even after page reloads or browser restarts, making it suitable for saving user preferences, carts, and simple state.

## Key Principles
- Data is stored as key–value pairs
- Storage is persistent (no expiration unless manually cleared)
- Data is stored as strings only
- Accessible via the `localStorage` object

## Core Methods
- `localStorage.setItem("key", value);` — Save data
- `localStorage.getItem("key");` — Retrieve data
- `localStorage.removeItem("key");` — Remove specific item
- `localStorage.clear();` — Clear all items

## Handling Non-Primitive Data
Local Storage only supports strings. Arrays and objects must be converted.

### Convert Object → String
```js
JSON.stringify(object);
```
### Convert String → Object
```js
JSON.parse(string);
```

# Example: Storing and Retrieving Data

## Store a Number
```javascript
const addNumberToLs = () => {
    let number = Math.ceil(Math.random() * 100);
    localStorage.setItem('number', number);
}
```

## Retrieve a Number
```javascript
const getNumberFromLs = () => {
    console.log(localStorage.getItem('number'));
}
```

## Example: Storing an Object
```javascript
const setObjectToLs = () => {
    const obj = { name: "shafi", id: 123, subject: "english" };
    localStorage.setItem('obj', JSON.stringify(obj));
}
```

## Reading Object
```javascript
const readObjectFromLs = () => {
    const customerObj = localStorage.getItem('obj');
    const parsedObj = JSON.parse(customerObj);
    console.log(parsedObj.name);
}
```

# Add to Cart Logic Using Local Storage
## Step-by-Step Logic
- Take input from user
- Retrieve existing cart from local storage
- Update cart (add or increase quantity)
- Convert to JSON string
- Save back to local storage
- Display updated cart


# Implementation

```javascript
const handleAddProduct = () => {
    const productElement = document.getElementById("product");
    const quantityElement = document.getElementById("quantity");

    const product = productElement.value;
    const quantity = parseInt(quantityElement.value);

    addProductToCart(product, quantity);
    displayStoredData();

    productElement.value = "";
    quantityElement.value = "";
}
```

## Add Product to Cart

```javascript
const addProductToCart = (product, quantity) => {
    let cart = getCart();

    if (cart[product]) {
        cart[product] += quantity;
    } else {
        cart[product] = quantity;
    }

    localStorage.setItem("cart", JSON.stringify(cart));
}
```

## Get Cart from Local Storage

```javascript
const getCart = () => {
    let cart = {};
    const jsonCart = localStorage.getItem("cart");

    if (jsonCart) {
        cart = JSON.parse(jsonCart);
    }

    return cart;
}
```


# Display Stored Data

```javascript
const displayStoredData = () => {
    document.getElementById("add-items").innerHTML = "";
    let cart = getCart();

    for (let item in cart) {
        displayCart(item, cart[item]);
    }
}
```

# Render Cart Items

```javascript
const displayCart = (product, quantity) => {
    const addItems = document.getElementById("add-items");
    const li = document.createElement("li");

    li.innerText = `${product}: ${quantity}`;
    addItems.appendChild(li);
}
```

# Important Notes / Edge Cases
- `localStorage.clear()` removes all keys (not a single item)
- Data persists across sessions but is limited (~5MB depending on browser)
- `getItem()` returns `null` if key does not exist
- Always check before parsing JSON to avoid errors
- Keys are case-sensitive

# Common Mistakes
- Trying to store objects without `JSON.stringify()`
- Forgetting `JSON.parse()` when retrieving data
- Using `clearItem()` (incorrect method — correct is `clear()`)
- Not handling null values from `getItem()`
- Assuming localStorage supports complex data types directly

# Key Takeaways
- Local Storage is useful for persistent client-side data.
- Always convert objects/arrays using JSON methods.
- Manage data carefully to avoid overwriting or errors.
- Ideal for small-scale storage like carts, preferences, and UI state.
