<details>
  <summary><b>Steps to structure web page</b></summary>


  ## 🎨 Design (Figma)

View the design here:  
[https://www.figma.com/file/your-file-id](https://www.figma.com/design/KwDHxD3CgZ7xP18GrFHacs/Techwave.-.L1.2?node-id=1-40&t=CE2Aqtcv1f3Aqr14-1)

  # Guide to Structuring Your Figma and HTML

## 1. Identify Main Sections

Open your Figma file and avoid coding at this stage.

You should see a structure similar to:

```
Page
 ├── Navbar
 ├── Hero Section
 ├── Services / Features
 ├── Stats / Info
 ├── Footer
```

If these sections are not clearly visible, **zoom out** and **simplify** the view.

---

## 2. Focus Only on the Navbar First

### Step-by-step approach:
- Do not modify the entire page yet.
- Ask yourself:
  - On the left side → *Logo?*
  - On the right side → *Menu?*

### Navbar Structure:
```
Navbar
 ├── Logo
 └── Menu items
```

### HTML Structure (Thinking in Code):
```html
<nav class="navbar">
  <div class="logo">Techwave</div>
  <ul class="menu">
    <li>Home</li>
    <li>About</li>
    <li>Service</li>
    <li>Contact</li>
  </ul>
</nav>
```

### Layout Decision:
- Use **Flexbox** for layout:
```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```
the end.
done. move on.


# 3. Hero Section (Most Important)

**Now look at the hero.**

**Ask:**

- Is it split left/right? → **YES**

## Hero Structure

- **Left:** Text + Button
- **Right:** Image/Illustration

### HTML:
```html
<section class="hero">
  <div class="hero-left">
    <h1>Title</h1>
    <p>Description</p>
    <button>Get Started</button>
  </div>
  
  <div class="hero-right">
    <img src="..." />
  </div>
</section>
```

# 4. Layout Decision (Critical)

👉 **Two columns → FLEX**

### CSS:
```css
.hero {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
```

# 5. Size Thinking (This is Where You Struggle)

## Ask:

**Should both sides be equal?**

- If yes:

```css
.hero-left,
.hero-right {
  flex: 1;
}
```

- If text is smaller:

```css
.hero-left {
  flex: 1;
}
.hero-right {
  flex: 1.2;
}
```

# 6. Spacing (Don’t Guess)

## Check Figma:

- **Distance from edge:** Use padding.
- **Distance between elements:** Use gap or margin.

## Example:

```css
.hero {
  padding: 60px;
  gap: 40px;
}
```


# 7. Features / Cards Section

**Look carefully:**

**Ask:**

- Are items in rows and columns?

**If yes → Grid**

## Features
- Card
- Card
- Card
- Card

### HTML:
```html
<section class="features">
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
</section>
```

### Layout decision:
> 👉 Multiple equal boxes → GRID

```css
.features {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}
```

## 8. Responsive Thinking (VERY IMPORTANT)

Now simulate:
> 👉 Screen becomes small

**Ask:**
- Is 4 columns possible? → NO?

Adjust layout for smaller screens:
```css
@media (max-width: 768px) {
  .features {
    grid-template-columns: repeat(2, 1fr);
  }
}

```
to ensure the layout adapts.
during screen size reduction.
'think about stacking elements like hero sections:
define media query for hero stacking:
```css
@media (max-width: 768px) {
  .hero {
    flex-direction: column;
  }
}
```
done.


# 9. Common mistakes YOU are likely making

- ❌ Writing CSS without structure

  → **Fix:** Always draw layout first

- ❌ Using margin randomly

  → **Fix:**
  - Layout → flex/grid
  - Spacing → gap/padding

- ❌ Not controlling width

  → **Fix:** Use flex instead of random width

- ❌ Ignoring parent container

  → **Fix:** Always style parent first

# 10. Final mental execution (this is what you must do every time)

When you see a design:
1. Break into sections
2. Build HTML skeleton
3. Break section into parts
4. Choose layout (flex/grid)
5. Align (justify + align)
6. Control size (flex/width)
7. Add spacing
8. Style text/colors
9. Make responsive
</details>
