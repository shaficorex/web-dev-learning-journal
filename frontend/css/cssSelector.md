# CSS Selectors – Complete Guide

## Concept Overview

CSS selectors are used to target HTML elements and apply styles. They define which elements in the DOM will receive specific styling rules.

Understanding selectors is fundamental because they directly control how styles are applied and overridden.

## Key Principles
Selectors target elements based on:
- Tag name
- Class
- ID
- Attributes
- Relationships (parent/child)
- State (pseudo-classes)

Multiple selectors can be combined to increase specificity.
CSS follows a priority system (specificity) to resolve conflicts.

## 1. Basic Selectors
### Element Selector
Targets all elements of a specific type.
```css
p {
  color: red;
}
```
Applies to all `<p>` elements.

### Class Selector (`.`)
Targets elements with a specific class.
```css
.box {
  background: blue;
}
```
<div class="box"></div>


# ID Selector (#)

Targets a unique element.

```css
#title {
  font-size: 20px;
}
```

<h1 id="title"></h1>

**Note:** IDs should be unique per page.

## 2. Combining Selectors

### Multiple Classes

```css
.box.red {
  color: red;
}
```

Targets elements that have both `box` and `red` classes.

### Element + Class

```css
p.text {
  color: green;
}
```

Targets `<p>` elements with class `text`.

## 3. Descendant Selector (Space)

Targets elements nested inside another element (at any depth).

```css
div p {
  color: blue;
}
```

Targets all `<p>` inside `<div>`.

## 4. Child Selector (> )

Targets direct children only.

```css
div > p {
  color: red;
}
```

Only `<p>` that are immediate children of `<div>`.


# 5. Group Selector (,)

Apply the same style to multiple elements.

```css
h1, h2, p {
  color: black;
}
```

## 6. Pseudo-Classes

Used to style elements based on their state.

### Hover

```css
button:hover {
  background: red;
}
```
* When mouse is over the button.

### Active

```css
button:active {
  background: blue;
}
```
* When the button is being clicked.

### Focus

```css
input:focus {
  border: 2px solid green;
}
```
* When the input is selected (clicked or tabbed into).

## 7. Universal Selector

Targets all elements.

```css
targets all elements with * {
  margin: 0;
}
definitely use cautiously, as it affects the entire page.
```


# 8. Attribute Selectors

## Basic Pattern
```css
element[attribute="value"] {
  /* styles */
}
```

### Example: Paragraph
```html
<p type="info">Hello</p>
<p type="warning">Hi</p>
```
```css
p[type="info"] {
  color: blue;
}
```

## Example: Custom Data Attribute
```html
<p data-type="important">Text</p>
```
```css
p[data-type="important"] {
  font-weight: bold;
}
```

### Without Element Selector
```css
[data-type="important"] {
  color: green;
}
```
*Works on any element with that attribute.*

## Attribute Exists
```css
p[title] {
  color: red;
}
targets <p> elements that have a title attribute.
```

## Attribute Contains Value
```css
p[class*="box"] {
  color: blue;
}
targets classes containing "box".
```


# 9. Specificity (Priority System)

When multiple rules apply, CSS chooses based on specificity:

## Priority Order:
- ID > Class > Element

### Example
```html
<p id="one" class="two">Hello</p>
```
```css
p { color: green; }
.two { color: blue; }
#one { color: red; }
```

**Result:** Red (ID wins)

## Important Notes / Edge Cases
- Avoid overusing IDs for styling; prefer classes for reusability.
- Attribute selectors are powerful but can reduce readability if overused.
- `data-*` attributes are best practice for custom data.
- Specificity conflicts can lead to unexpected results—understand the hierarchy.

## Common Mistakes
- Using IDs multiple times on a page.
- Confusing descendant (`div p`) with child (`div > p`).
- Overusing universal selector (`*`), impacting performance.
- Ignoring specificity, leading to styles not applying as expected.

## Key Takeaways
- CSS selectors determine what gets styled.
- Combining selectors increases precision.
- Pseudo-classes handle user interaction states.
- Attribute selectors allow flexible targeting.
- Specificity controls which styles win in conflicts.
