# HTML Reference Guide

This document serves as a reference for HTML elements, including semantic and non-semantic tags, forms, tables, and special characters.

## Table of Contents

1. [HTML Tags](#html-tags)
   - [Semantic Tags](#semantic-tags)
   - [Non-Semantic Tags](#non-semantic-tags)
   - [Block Tags](#block-tags)
   - [Inline Tags](#inline-tags)
2. [Forms](#forms)
3. [HTML Tables](#html-tables)
4. [Special Characters (UTF-8)](#special-characters-utf-8)

---

## HTML Tags

### Semantic Tags

Semantic tags define the purpose and structure of content. They improve accessibility, SEO, and code maintainability.

1. **`<!DOCTYPE html>`**  
   Declares the document type.

   ```html
   <!DOCTYPE html>
   ```

2. **`<html>`**  
   The root element of an HTML page.

   ```html
   <html lang="en"></html>
   ```

3. **`<head>`**  
   Contains metadata such as the title, stylesheets, and scripts.

   ```html
   <head>
     <title>My Website</title>
     <link rel="stylesheet" href="style.css" />
   </head>
   ```

4. **`<body>`**  
   Contains the main content of the page.

   ```html
   <body>
     <!-- Content goes here -->
   </body>
   ```

5. **`<header>`**  
   Represents the header section of a page.

   ```html
   <header>
     <h1>My Website</h1>
   </header>
   ```

6. **`<nav>`**  
   Defines a navigation bar.

   ```html
   <nav>
     <ul>
       <li><a href="#home">Home</a></li>
       <li><a href="#about">About</a></li>
       <li><a href="#services">Services</a></li>
     </ul>
   </nav>
   ```

7. **`<section>`**  
   Represents a section in a document.

   ```html
   <section>
     <h2>Welcome to Our Website</h2>
     <p>This is the main content of our website.</p>
   </section>
   ```

8. **`<article>`**  
   Denotes independent, self-contained content.

   ```html
   <article>
     <h3>Latest News</h3>
     <p>Read about our new services and upcoming events.</p>
     <time datetime="2024-01-15">January 15, 2024</time>
   </article>
   ```

9. **`<aside>`**  
   Used for sidebar content.

   ```html
   <aside>
     <h3>Quick Links</h3>
     <ul>
       <li><a href="#privacy">Privacy Policy</a></li>
       <li><a href="#terms">Terms of Service</a></li>
     </ul>
   </aside>
   ```

10. **`<footer>`**  
    Represents the footer section of a page.

    ```html
    <footer>
      <p>&copy; 2024 My Website. All rights reserved.</p>
    </footer>
    ```

11. **`<address>`**  
    Provides contact information.

    ```html
    <address>
      <strong>Company Name</strong><br />
      123 Main Street<br />
      City, State, Country
    </address>
    ```

12. **`<time>`**  
    Represents date/time information.
    ```html
    <p>
      The event will take place at
      <time datetime="2024-05-20T18:00">6 PM on May 20</time>.
    </p>
    ```

#### Example: Including All Semantic Tags

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <header>
      <h1>Welcome to My Website</h1>
      <nav>
        <ul>
          <li><a href="#home">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a href="#services">Services</a></li>
        </ul>
      </nav>
    </header>

    <section>
      <article>
        <h2>Latest News</h2>
        <p>This is the latest news article posted on our website.</p>
        <time datetime="2024-01-15">January 15, 2024</time>
      </article>

      <aside>
        <h3>Quick Links</h3>
        <ul>
          <li><a href="#privacy">Privacy Policy</a></li>
          <li><a href="#terms">Terms of Service</a></li>
        </ul>
      </aside>
    </section>

    <footer>
      <address>
        Company Name<br />
        123 Main Street<br />
        City, State, Country
      </address>
      <p>&copy; 2024 My Website. All rights reserved.</p>
    </footer>
  </body>
</html>
```

**Benefits of Semantic Tags:**

- **SEO:** Search engines can better understand your content.
- **Accessibility:** Screen readers can navigate more effectively.
- **Maintenance:** Easier to update and modify content.

---

### Non-Semantic Tags

Non-semantic tags are used primarily for styling and layout. They do not convey meaning about the content.

#### 1. `<div>`

- **Purpose:** A generic container to group other elements.
- **Example:**
  ```html
  <div class="header">
    <h1>My Website</h1>
  </div>
  ```

#### 2. `<span>`

- **Purpose:** An inline container used to apply styles to a portion of text.
- **Example:**
  ```html
  This is some <span style="color: red;">important</span> text.
  ```

#### Example: Using Non-Semantic Tags

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Example of Non-Semantic Tags</title>
    <style>
        .header {
            background-color: #f0f0f0;
            padding: 20px;
        }
        .nav {
            background-color: #333;
            color: white;
            padding: 15px;
        }
        .content {
            margin-top: 50px;
            padding: 20px;
        }
        .highlight {
            font-weight: bold;
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <div class="header">
        <h1>My Website</h1>
    </div>

    <!-- Navigation -->
    <div class="nav">
        <a href="#home">Home</a> |
        <a href="#about">About</a> |
        <a href="#services">Services</a> |
        <a href="#contact">Contact</a>
    </div>

    <!-- Main Content -->
    <div class="content">
        <h2>Welcome to Our Website</h2>
        <p>
          This is an example of how non-semantic tags can be used for layout and styling.
          Notice that the structure relies on `<div>` and `<span>` tags, which allow us to apply styles effectively.
        </p>
        <p>
          Here's a highlighted word: <span class="highlight">Important</span>.
        </p>
    </div>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <p>&copy; 2024 My Website. All rights reserved.</p>
        </div>
    </footer>
</body>
</html>
```

**Why Use Non-Semantic Tags?**

- **Styling:** They allow specific styling without implying meaning.
- **Layout:** Useful for creating complex layouts.
- **Accessibility:** Can be combined with semantic tags for enhanced accessibility.

**Best Practices:**

- Use non-semantic tags only when necessary for styling.
- Combine with semantic tags to ensure a balance between structure and design.
- Use classes and IDs for effective CSS styling.

---

### Block Tags

Block-level elements take up the full width of their container. Common examples include:

1. **`<p>` - Paragraph**

   ```html
   <p>This is a sample paragraph using the <code>&lt;p&gt;</code> tag.</p>
   ```

2. **Heading Tags (`<h1>` to `<h6>`)**

   ```html
   <h1>Main Heading</h1>
   <h2>Section Subheading</h2>
   ```

3. **Lists (`<ul>`, `<ol>`)**

   ```html
   <ul>
     <li>List Item 1</li>
     <li>List Item 2</li>
     <li>List Item 3</li>
   </ul>

   <ol>
     <li>Step 1</li>
     <li>Step 2</li>
     <li>Step 3</li>
   </ol>
   ```

4. **`<li>` - List Item**  
   Example with inline formatting:

   ```html
   <ul>
     <li><strong>List Item with Strong Text</strong></li>
     <li><em>List Item with Emphasized Text</em></li>
   </ul>
   ```

5. **`<img>` - Image**

   ```html
   <img src="example.jpg" alt="Sample Image" />
   ```

6. **`<video>` - Video Element**
   ```html
   <video controls>
     <source src="example.mp4" type="video/mp4" />
     Your browser does not support this video format.
   </video>
   ```

---

### Inline Tags

Inline tags affect only the content within them. Common examples include:

1. **`<a>` - Hyperlink**

   ```html
   Click here to visit: <a href="https://www.example.com">Example Website</a>
   ```

2. **`<em>` and `<strong>` - Emphasis and Strong Text**

   ```html
   This is an <em>italicized</em> word and a <strong>bolded</strong> word.
   ```

3. **`<sup>` and `<sub>` - Superscript and Subscript**

   ```html
   The number 2: <sup>2</sup>

   Subscript example: <sub>subscript text</sub>
   ```

4. **`<abbr>` and `<acronym>` - Abbreviations**

   ```html
   This is an <abbr title="HyperText Markup Language">HTML</abbr> document.
   ```

5. **`<bdo>` - Bidirectional Override**
   ```html
   <bdo dir="rtl">This text is right-to-left.</bdo>
   ```

#### Example: Combining Block and Inline Tags

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Mixed Tags Example</title>
  </head>
  <body>
    <h1>Welcome to Our Website</h1>
    <p>
      <a href="https://www.example.com">Visit our main site</a> for more
      information.
    </p>

    <h2>Features</h2>
    <ul>
      <li><em>Italicized feature</em></li>
      <li><strong>Bold feature</strong></li>
      <li><sup>*</sup> Superscript note</li>
      <li><sub>Subscript notation</sub></li>
    </ul>

    <h3>Image and Video Section</h3>
    <p>
      Please see our <a href="https://www.example.com/gallery">gallery</a> for
      images and videos.
    </p>
    <img src="example.jpg" alt="Sample Image" />

    <video controls>
      <source src="example.mp4" type="video/mp4" />
      Your browser does not support this video format.
    </video>

    <h3>About</h3>
    <p>
      We use technologies like
      <abbr title="HyperText Markup Language">HTML</abbr> and
      <abbr title="Cascading Style Sheets">CSS</abbr> to create our websites.
    </p>

    <bdo dir="rtl">Right-to-left text override example.</bdo>
  </body>
</html>
```

**Summary:**

- **Block Tags:** Used for creating distinct sections (e.g., paragraphs, headings, lists, images, and videos).
- **Inline Tags:** Affect only parts of the text (e.g., hyperlinks, emphasis, and abbreviations).

---

## Forms

HTML forms allow user input and data submission. Key elements include:

1. **`<form>`**  
   Defines an HTML form.

   ```html
   <form action="/submit" method="POST">
     <!-- Form elements go here -->
   </form>
   ```

2. **`<input>`**  
   Accepts user input (text, password, email, etc.).

   ```html
   <!-- Text input -->
   <input type="text" name="username" placeholder="Enter your username" />

   <!-- Password input -->
   <input type="password" name="password" placeholder="Enter your password" />

   <!-- Email input -->
   <input type="email" name="email" placeholder="Enter your email" />
   ```

3. **`<textarea>`**  
   Allows multi-line text input.

   ```html
   <textarea
     name="message"
     rows="4"
     placeholder="Type your message here..."
   ></textarea>
   ```

4. **`<select>` and `<option>`**  
   Creates a drop-down list.

   ```html
   <select name="country">
     <option value="usa">United States</option>
     <option value="can">Canada</option>
     <option value="uk">United Kingdom</option>
   </select>
   ```

5. **`<button>`**  
   A button to submit the form.
   ```html
   <button type="submit">Submit Form</button>
   ```

### Form Methods

- **GET:** Appends form data to the URL. Suitable for non-sensitive data (e.g., search queries).
- **POST:** Sends form data in the request body. Recommended for sensitive information.

#### Example: GET Form

```html
<form action="/search" method="GET">
  <input type="text" name="query" placeholder="Search..." />
  <button type="submit">Search</button>
</form>
```

#### Example: POST Form

```html
<form action="/login" method="POST">
  <input type="text" name="username" placeholder="Username" required />
  <input type="password" name="password" placeholder="Password" required />
  <button type="submit">Login</button>
</form>
```

---

## HTML Tables

Tables are used for displaying data in a structured format. Key table tags include:

1. **`<table>`**  
   Defines the table structure.

   ```html
   <table>
     <tr>
       <th>Product</th>
       <th>Price</th>
     </tr>
     <tr>
       <td>Laptop</td>
       <td>$999</td>
     </tr>
   </table>
   ```

2. **`<tr>`**  
   Represents a table row.

   ```html
   <tr>
     <td>New York</td>
     <td>Population: 8.6 million</td>
   </tr>
   ```

3. **`<th>`**  
   Defines a header cell.

   ```html
   <th>Name</th>
   ```

4. **`<td>`**  
   Defines a standard cell.

   ```html
   <td>John Doe</td>
   ```

5. **`<thead>`, `<tbody>`, and `<tfoot>`**  
   Organize table sections for headers, body, and footer.

   ```html
   <thead>
     <tr>
       <th>Month</th>
       <th>Sales</th>
     </tr>
   </thead>
   <tbody>
     <tr>
       <td>January</td>
       <td>$10,000</td>
     </tr>
   </tbody>
   <tfoot>
     <tr>
       <td>Total Sales:</td>
       <td>$50,000</td>
     </tr>
   </tfoot>
   ```

6. **`<col>` and `<colgroup>`**  
   Define column properties.

   ```html
   <colgroup span="3">
     <col width="10%" />
     <col width="40%" />
     <col width="50%" />
   </colgroup>
   ```

7. **`<caption>`**  
   Provides a title for the table.
   ```html
   <caption>
     Monthly Sales Data
   </caption>
   ```

#### Example: HTML Table with Spanning

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>HTML Table Example</title>
  </head>
  <body>
    <table border="1">
      <!-- Table Caption -->
      <caption>
        Employee Performance Summary Report
      </caption>

      <!-- Table Header -->
      <thead>
        <tr>
          <th>Name</th>
          <th>Department</th>
          <th>Position</th>
          <th>Location</th>
          <th colspan="2">Performance Metrics</th>
        </tr>
      </thead>

      <!-- Column Definitions -->
      <colgroup span="5">
        <col width="30%" />
        <col width="15%" />
        <col width="20%" />
        <col width="15%" />
        <col width="20%" />
      </colgroup>

      <!-- Table Body -->
      <tbody>
        <tr>
          <td>John Doe</td>
          <td rowspan="3">Marketing</td>
          <td>Sales Manager</td>
          <td>New York</td>
          <td>95%</td>
          <td>$120,000</td>
        </tr>
        <tr>
          <td>Jane Smith</td>
          <td>Data Analyst</td>
          <td>Dallas</td>
          <td>88%</td>
          <td>$95,000</td>
        </tr>
        <tr>
          <td>Mike Johnson</td>
          <td rowspan="3">Operations</td>
          <td>Project Manager</td>
          <td>Chicago</td>
          <td>85%</td>
          <td>$100,000</td>
        </tr>
      </tbody>

      <!-- Table Footer -->
      <tfoot>
        <tr>
          <td colspan="4">Total Employees:</td>
          <td>3</td>
        </tr>
        <tr>
          <td colspan="6">
            Note: Figures are approximate and subject to change.
          </td>
        </tr>
      </tfoot>
    </table>
  </body>
</html>
```

**Key Points for Tables:**

- Use `<thead>`, `<tbody>`, and `<tfoot>` for better structure.
- Use `colspan` and `rowspan` for cell spanning.
- `<caption>` improves accessibility by providing a clear table title.

---

## Special Characters (UTF-8)

Special characters should be properly encoded in HTML. Common entities include:

- `&nbsp;` – Non-breaking space
- `&copy;` – Copyright symbol
- `&reg;` – Registered trademark
- `&lt;` – Less than sign
- `&gt;` – Greater than sign
- `&amp;` – Ampersand
- `&quot;` – Double quotes
- `&apos;` – Apostrophe
- `€` – Euro symbol
- `–` – En dash
- `—` – Em dash

#### Example

```html
<p>
  Special characters: &copy;, &reg;, &amp;, &lt;, &gt;, &quot;Hello &ndash;
  World&quot;
</p>
```

---

## Final Notes

- **Semantic tags** enhance SEO, accessibility, and maintainability.
- **Non-semantic tags** are essential for styling and layout.
- **Block and inline tags** should be used appropriately to create structured and visually appealing web content.
- **Forms and tables** require a clear structure for proper data collection and display.
- **Special characters** must be encoded to ensure proper rendering.

This guide is intended to provide reference for creating well-structured, accessible, and maintainable HTML content.

---

Created by [VPDevLabs](https://github.com/vpdevlabs)
