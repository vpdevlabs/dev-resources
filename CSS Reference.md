# CSS Guide

This guide covers the fundamentals of CSS—from how to include styles in HTML, to understanding the syntax and selectors, mastering the box model, creating responsive layouts with Flexbox and Grid, and enhancing text and interactivity with transitions, animations, and media queries.

By studying, modifying, and applying these examples, you can build a strong foundation in CSS and prepare for advanced topics and web development challenges.

---

## 1. Introduction to CSS

CSS (Cascading Style Sheets) is the language used to describe the presentation of HTML documents. It lets you separate content (HTML) from design (layout, colors, fonts, etc.), which helps improve maintainability and reusability.

### Example 1.1 – External CSS

This example shows a simple HTML document that links to an external stylesheet:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>My Website</title>
    <!-- Linking an external CSS file -->
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <h1>Welcome to My Website</h1>
    <p>This page is styled using external CSS.</p>
  </body>
</html>
```

And the corresponding CSS:

```css
/* styles.css */
body {
  background-color: #f0f0f0;
  font-family: Arial, sans-serif;
}

h1 {
  color: #333;
}
```

### Example 1.2 – Inline CSS

You can also apply styles directly to HTML elements using the `style` attribute:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Inline CSS Example</title>
  </head>
  <body>
    <h1 style="color: #2c3e50; text-align: center;">Hello World!</h1>
    <p style="font-family: 'Arial', sans-serif;">
      This paragraph uses inline CSS for quick styling.
    </p>
  </body>
</html>
```

---

## 2. CSS Syntax and Selectors

CSS rules consist of a selector and a declaration block. Selectors target the HTML elements you want to style.

### Example 2.1 – Basic Rule and Type Selector

A simple rule using a type selector:

```css
/* Target all <p> elements */
p {
  color: #333;
  font-size: 16px;
}
```

### Example 2.2 – Various Selectors

This example demonstrates multiple selector types:

```css
/* Class selector */
.highlight {
  background-color: yellow;
}

/* ID selector */
#main-title {
  font-weight: bold;
}

/* Attribute selector */
a[target="_blank"] {
  color: blue;
}

/* Pseudo-class selector */
a:hover {
  text-decoration: underline;
}

/* Pseudo-element selector */
p::first-line {
  font-style: italic;
}
```

---

## 3. CSS Box Model

The box model defines how elements are rendered in terms of their content, padding, borders, and margins.

### Example 3.1 – Simple Box Model Calculation

This snippet defines a box with explicit dimensions:

```css
div.example {
  width: 300px; /* Content width */
  padding: 20px; /* Space inside the border */
  border: 5px solid #333;
  margin: 10px; /* Space outside the border */
}
/* Total width = 300 + (20×2) + (5×2) = 350px */
```

### Example 3.2 – Container Example

A GitHub-inspired layout for centering a container:

```css
#container {
  width: 500px;
  padding: 20px;
  border: 5px solid #000;
  margin: 0 auto; /* Center horizontally */
  background-color: #eee;
}
```

---

## 4. CSS Layout

CSS layout techniques help position elements on the page. Below are examples covering display types, positioning, Flexbox, and Grid.

### 4.1. Display Property

#### Example 4.1 – Block, Inline, and Inline-Block

```css
/* Block element: takes full width */
div.block {
  display: block;
  background: lightblue;
  margin: 5px 0;
}

/* Inline element: only as wide as its content */
span.inline {
  display: inline;
  background: lightgreen;
}

/* Inline-block: respects width/height while flowing inline */
div.inline-block {
  display: inline-block;
  background: lightcoral;
  width: 120px;
  height: 50px;
  margin: 5px;
}
```

### 4.2. Positioning

#### Example 4.2 – Relative vs. Absolute vs. Fixed

```css
/* Relative positioning: moves relative to its normal spot */
.relative-box {
  position: relative;
  top: 10px;
  left: 20px;
  background: #f9c74f;
  padding: 10px;
}

/* Absolute positioning: removed from flow, positioned relative to nearest positioned ancestor */
.absolute-box {
  position: absolute;
  top: 50px;
  left: 50px;
  background: #90be6d;
  padding: 10px;
}

/* Fixed positioning: relative to the viewport */
.fixed-box {
  position: fixed;
  bottom: 0;
  right: 0;
  background: #577590;
  padding: 10px;
  color: white;
}
```

### 4.3. Flexbox Layout

Flexbox makes it easy to create responsive, one-dimensional layouts.

## Flexbox: Examples and Use Cases

Flexbox is ideal for one-dimensional (row or column) layouts, components, and small-scale UI patterns. Here are several practical examples:

### 1. Responsive Navbar with Auto Margins

Using auto margins in a flex container is a popular trick to “push” groups of items to one side. In this example, the logo stays left while navigation links are pushed right.

```html
<!-- Responsive Navbar -->
<header class="navbar">
  <div class="logo">MySite</div>
  <nav class="nav-links">
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Services</a>
    <a href="#" class="push-right">Contact</a>
  </nav>
</header>
```

```css
.navbar {
  display: flex;
  align-items: center;
  padding: 1rem;
  background: #f9f9f9;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
}

.nav-links {
  display: flex;
  flex: 1;
  gap: 1rem;
}

.push-right {
  margin-left: auto; /* This pushes this link (and any following it) to the right */
}
```

_Why use it?_  
This approach lets you quickly build a header that adapts to different screen sizes without complicated floats or positioning hacks.

---

### 2. Sidebar and Main Content Layout

A common layout has a fixed-width sidebar and fluid main content. While CSS Grid may be preferred for complex page layouts, Flexbox still works well in many cases.

```html
<!-- Sidebar and Main Content -->
<div class="layout">
  <aside class="sidebar">
    <h2>Sidebar</h2>
    <p>Additional navigation or info.</p>
  </aside>
  <main class="main-content">
    <h1>Welcome!</h1>
    <p>This is the main content area.</p>
  </main>
</div>
```

```css
.layout {
  display: flex;
  gap: 1rem;
  padding: 1rem;
}

.sidebar {
  flex: 0 0 250px; /* Fixed width sidebar */
  background: #e0e0e0;
  padding: 1rem;
}

.main-content {
  flex: 1; /* Fills remaining space */
  background: #f4f4f4;
  padding: 1rem;
}
```

_When to use Flexbox?_  
Flexbox is great when the number of columns is fixed and you want content to grow or shrink proportionally along one axis.

---

### 3. Flexible Card Layout

For a grid of cards (such as pricing plans or product cards) that need to wrap and adjust their size dynamically, Flexbox can create a fluid, responsive layout.

```html
<!-- Card Layout -->
<div class="card-container">
  <div class="card">
    <h2>Basic Plan</h2>
    <p>Basic features included.</p>
    <span class="price">$10/month</span>
    <a href="#" class="btn">Sign Up</a>
  </div>
  <div class="card">
    <h2>Pro Plan</h2>
    <p>Advanced features for pros.</p>
    <span class="price">$20/month</span>
    <a href="#" class="btn">Sign Up</a>
  </div>
  <div class="card">
    <h2>Premium Plan</h2>
    <p>All features, best support.</p>
    <span class="price">$30/month</span>
    <a href="#" class="btn">Sign Up</a>
  </div>
</div>
```

```css
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: space-between;
}

.card {
  flex: 1 0 calc(33.33% - 1rem); /* Three cards per row */
  background: #fff;
  border: 1px solid #ddd;
  padding: 1rem;
  display: flex;
  flex-direction: column;
}

.card .price {
  font-size: 1.2rem;
  font-weight: bold;
  margin-top: auto; /* Push price to bottom */
}

.btn {
  display: inline-block;
  margin-top: 0.5rem;
  padding: 0.5rem 1rem;
  background: #007bff;
  color: #fff;
  text-decoration: none;
  text-align: center;
  border-radius: 4px;
}
```

_Why use Flexbox here?_  
Flexbox handles wrapping and equal-height columns effortlessly, making it ideal for components that need to adjust to varying content lengths.

---

### 4.4. CSS Grid Layout

Grid layout is ideal for two-dimensional designs (rows and columns).

## CSS Grid: Examples and Use Cases

CSS Grid is designed for two-dimensional layouts—ideal when you have rows and columns to manage simultaneously.

### 1. The “Holy Grail” Layout

This classic layout includes a header, footer, sidebar, and main content. Using grid-template-areas makes it very readable.

```html
<!-- Holy Grail Layout -->
<div class="grid-container">
  <header class="header">Header</header>
  <nav class="nav">Navigation</nav>
  <main class="main">Main Content</main>
  <aside class="sidebar">Sidebar</aside>
  <footer class="footer">Footer</footer>
</div>
```

```css
.grid-container {
  display: grid;
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header header header"
    "nav main sidebar"
    "footer footer footer";
  gap: 1rem;
  min-height: 100vh;
}

.header {
  grid-area: header;
  background: #007bff;
  color: #fff;
  padding: 1rem;
}

.nav {
  grid-area: nav;
  background: #f4f4f4;
  padding: 1rem;
}

.main {
  grid-area: main;
  background: #fff;
  padding: 1rem;
}

.sidebar {
  grid-area: sidebar;
  background: #f4f4f4;
  padding: 1rem;
}

.footer {
  grid-area: footer;
  background: #333;
  color: #fff;
  padding: 1rem;
  text-align: center;
}
```

_When to use Grid?_  
Use Grid when your layout is two-dimensional—for instance, when you need to define both columns and rows precisely.

---

### 2. Responsive Image Gallery

This example uses the `repeat(auto-fit, minmax(...))` pattern to create a gallery that adapts to the screen size.

```html
<!-- Responsive Image Gallery -->
<div class="gallery">
  <img src="https://via.placeholder.com/300" alt="Gallery Image" />
  <img src="https://via.placeholder.com/300" alt="Gallery Image" />
  <img src="https://via.placeholder.com/300" alt="Gallery Image" />
  <img src="https://via.placeholder.com/300" alt="Gallery Image" />
  <img src="https://via.placeholder.com/300" alt="Gallery Image" />
  <img src="https://via.placeholder.com/300" alt="Gallery Image" />
</div>
```

```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  padding: 1rem;
}

.gallery img {
  width: 100%;
  height: auto;
  display: block;
}
```

_Why use Grid here?_  
Grid’s auto-fill/auto-fit and minmax functions make it simple to create layouts that adjust the number of columns based on the viewport width.

---

### 3. Nested Grid for a Dashboard

For more complex pages like dashboards, you can nest grids within grid items to achieve highly structured layouts.

```html
<!-- Dashboard Layout -->
<div class="dashboard">
  <header class="dash-header">Dashboard Header</header>
  <div class="dash-content">
    <nav class="dash-nav">Side Navigation</nav>
    <section class="dash-main">
      <div class="widget">Widget 1</div>
      <div class="widget">Widget 2</div>
      <div class="widget">Widget 3</div>
      <div class="widget">Widget 4</div>
    </section>
  </div>
  <footer class="dash-footer">Dashboard Footer</footer>
</div>
```

```css
.dashboard {
  display: grid;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header header"
    "nav main"
    "footer footer";
  gap: 1rem;
  min-height: 100vh;
}

.dash-header {
  grid-area: header;
  background: #005f73;
  color: #fff;
  padding: 1rem;
}

.dash-content {
  display: grid;
  grid-template-columns: 250px 1fr;
  gap: 1rem;
  grid-area: nav / main;
}

.dash-nav {
  grid-area: 1 / 1 / 2 / 2;
  background: #0a9396;
  color: #fff;
  padding: 1rem;
}

.dash-main {
  grid-area: 1 / 2 / 2 / 3;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1rem;
}

.widget {
  background: #94d2bd;
  padding: 1rem;
  text-align: center;
}

.dash-footer {
  grid-area: footer;
  background: #001219;
  color: #fff;
  padding: 1rem;
  text-align: center;
}
```

_When is nested grid helpful?_  
When your page is complex (like a dashboard), you can use an outer grid for the major layout areas and nest inner grids to control the layout within each area.

---

## When to Use Flexbox vs. Grid

- **Flexbox** shines with components and one-dimensional layouts (e.g., navbars, toolbars, small card groups). Use it when you need to distribute space among items along a single axis.
- **Grid** is perfect for two-dimensional layouts (e.g., full-page layouts, image galleries, complex dashboards) where you must manage both rows and columns simultaneously.

By combining both tools, you can often use Grid for the overall page layout and Flexbox within individual grid cells for finer alignment control. This hybrid approach is common on modern websites and is supported by many design frameworks.

_Additional Resources:_  
For more examples, check out [Grid by Example](https://gridbyexample.com/examples/) and [CSS Flexbox Real World Use Cases](https://ishadeed.com/article/flexbox-real-world-use-cases/)

---

---

## 5. Styling Text

CSS gives you powerful control over typography and text presentation.

### Example 5.1 – Font Properties

```css
p {
  font-family: "Georgia", serif;
  font-size: 18px;
  font-weight: normal;
  font-style: italic;
  color: #333;
}
```

### Example 5.2 – Text Decoration and Shadows

```css
h1 {
  color: #264653;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 2px;
  text-shadow: 1px 1px 2px #ccc;
}
```

---

## 6. Advanced Topics

### 6.1. Transitions and Animations

CSS transitions and animations create smooth, dynamic effects.

#### Example 6.1 – Button Transition

```css
.button {
  background: #2a9d8f;
  color: white;
  padding: 10px 20px;
  border: none;
  transition: background 0.3s ease;
}

.button:hover {
  background: #21867a;
}
```

#### Example 6.2 – Simple Keyframe Animation

```css
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.fade-in {
  animation: fadeIn 2s ease-in-out;
}
```

### 6.2. Media Queries

Media queries let you adjust your layout for different screen sizes.

#### Example 6.3 – Responsive Background Color

```css
@media (max-width: 600px) {
  body {
    background: #e9c46a;
  }
}
```

### 6.3. Custom Properties (Variables) and @import

Custom properties help you reuse values, and @import lets you include external CSS files.

#### Example 6.4 – CSS Variables

```css
:root {
  --primary-color: #e76f51;
}

.header {
  background: var(--primary-color);
  color: white;
  padding: 20px;
}
```

#### Example 6.5 – Using @import

```css
/* main.css */
@import url("reset.css");

body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}
```

---

Created by [VPDevLabs](https://github.com/vpdevlabs)
