# CSS Guide

## Introduction

Cascading Style Sheets (CSS) is a stylesheet language used for describing the presentation of a document written in HTML. CSS allows you to control layout, typography, and the overall look and feel of the web page.

### References

- [Wikipedia HTML Overview](https://en.wikipedia.org/wiki/Cascading_Style_Sheets)
- [W3Schools CSS Tutorial](https://www.w3schools.com/css/)
- [CSS Specifications by WHATWG](https://www.w3.org/Style/CSS/specs.en.html)
- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS)

---

## Core Concepts
1. **Selectors**: Indicate which elements a set of CSS rules apply to.
2. **Properties**: The attributes you want to change (e.g., `color`, `margin`).
3. **Values**: The values assigned to properties (e.g., `red`, `16px`).
4. **Inheritance**: Some properties (like font) are automatically inherited by child elements unless otherwise specified.
5. **Specificity**: Determines which styles are applied when conflicting styles exist.
6. **Box Model**: Conceptual model describing the layout with margin, border, padding, and content.
7. **Flexbox/Grid**: Modern layout models for complex design structures.
8. **Responsive Design**: Techniques to make web pages render well on different devices.

---

## Syntax

Here's a simple example of CSS syntax:

```css
/* Example of basic CSS syntax */
p {
  color: red;
  font-size: 16px;
}
```

---

## Example Page

To create and view a simple HTML/CSS page, follow the steps below:

1. **Navigate to the directory where you created your index.html file.**

2. **Create/Open the CSS file in a text editor.**
   ```bash
   nano styles.css  # or vi, vim, emacs, code, etc.
   ```

3. **Paste the following CSS into the text editor.**
   ```css
    /* Base Styles */
    :root {
        --primary-color: #007bff;
        --secondary-color: #6c757d;
        --bg-color: #f8f9fa;
        --font-color: #343a40;
    }

    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background-color: var(--bg-color);
        color: var(--font-color);
    }

    /* Header */
    header {
        background-color: var(--primary-color);
        color: white;
        text-align: center;
        padding: 1rem;
    }

    /* Navigation */
    nav ul {
        background-color: var(--secondary-color);
        overflow: hidden;
        color: white;
    }

    nav ul li {
        float: left;
        display: block;
        text-align: center;
        padding: 14px 16px;
        text-decoration: none;
    }

    /* Main Content */
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 1rem;
        padding: 1rem;
    }

    section {
        border-radius: 8px;
        background-color: white;
        margin: 1rem;
        padding: 1rem;
        width: 100%;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }

    /* Buttons */
    button {
        background-color: var(--primary-color);
        color: white;
        border: none;
        padding: 10px 20px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 20px;
        cursor: pointer;
        border-radius: 4px;
    }

    /* Hover Div */
    #hoverDiv {
        width: 200px;
        height: 200px;
        background-color: var(--secondary-color);
        color: white;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 10px 20px;
        transition: background-color 0.3s;
    }

    #hoverDiv:hover {
        background-color: var(--primary-color);
    }

    /* Form Styles */
    form input[type="text"],
    form input[type="email"] {
        width: 100%;
        padding: 12px 20px;
        margin: 8px 0;
        box-sizing: border-box;
        border: 2px solid var(--primary-color);
        border-radius: 4px;
    }

    /* Lists and Tables */
    table {
        width: 100%;
        border-collapse: collapse;
    }

    table, th, td {
        border: 1px solid var(--primary-color);
    }

    th, td {
        text-align: left;
        padding: 8px;
    }

    th {
        background-color: var(--primary-color);
        color: white;
    }

    /* Footer */
    footer p {
        text-align: right;
        margin: 10px 20px;
    }


        }

        /* Style the footer */
        footer {
        background-color: #333;
        color: white;
        text-align: center;
        padding: 10px;
        position: relative;
        bottom: 0;
        width: 100%;
        }

        /* Add responsiveness to layout */
        @media (max-width: 600px) {
        nav ul li {
            float: none;
            display: block;
        }
        }
   ```

4. **In your HTML file, make sure to link this CSS file inside the head tag.**
   ```html
   <link rel="stylesheet" href="styles.css">
   ```

5. **To view the HTML file in a browser.**
   ```bash
    xdg-open index.html  # Linux
    start index.html  # Windows
    open index.html  # macOS
   ```
---

## Most Commonly Used CSS Properties

CSS properties are the building blocks of styling web pages. They control everything from layout to typography to animation.

### Layout

1. **`display`**: Specifies the display behavior of an element (block, inline, flex, grid, etc.).
2. **`width` and `height`**: Sets the dimensions of the element.
3. **`margin`**: Controls the space outside the element's border.
4. **`padding`**: Controls the space between the element's content and its border.
5. **`box-sizing`**: Specifies how the dimensions of the element are calculated.

### Typography

1. **`font-family`**: Specifies the typeface to be used.
2. **`font-size`**: Controls the size of the text.
3. **`font-weight`**: Specifies the thickness of the character outlines (normal, bold, bolder, etc.).
4. **`text-align`**: Sets the horizontal alignment of the text within an element.
5. **`line-height`**: Sets the amount of space between lines of text.

### Visual

1. **`color`**: Sets the color of the text.
2. **`background-color`**: Sets the background color of an element.
3. **`border`**: Defines the border surrounding an element.
4. **`box-shadow`**: Adds shadow effects around an element's frame.
5. **`opacity`**: Sets the opacity level for an element.

### Interaction and Animation

1. **`cursor`**: Specifies the type of cursor to be displayed.
2. **`hover`**: Describes how an element should be styled when the mouse is placed over it.
3. **`transition`**: Sets the speed and nature of transition between multiple states.
4. **`animation`**: Allows the application of animation logic.

### Flexbox and Grid

1. **`justify-content`**: Aligns items along the main axis of a flex container.
2. **`align-items`**: Aligns items along the cross-axis.
3. **`grid-template-rows` / `grid-template-columns`**: Define the layout in CSS grid.

---

