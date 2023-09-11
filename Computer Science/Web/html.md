# HTML Guide

## Introduction

HTML (HyperText Markup Language) is the foundational markup language used for structuring content on the World Wide Web. Created by Tim Berners-Lee in 1990, it has undergone several revisions to accommodate the evolving needs of web developers.

### Key References

- [Wikipedia HTML Overview](https://en.wikipedia.org/wiki/HTML)
- [W3Schools HTML Tutorial](https://www.w3schools.com/html/html_intro.asp)
- [HTML Living Standard by WHATWG](https://html.spec.whatwg.org/)

---

## Core Concepts

### Tags and Elements

**Tags**: HTML is written in the form of tags, delineated by angle brackets (e.g., `<tagname>`).
**Elements**: An HTML element encompasses the start tag, content, and the corresponding end tag (e.g., `<tagname>content</tagname>`).

### Attributes

HTML elements can have attributes like `class`, `id`, or `src` that provide additional metadata or functionalities to the element.

### DOM (Document Object Model)

The DOM is a hierarchical tree-like representation of the content that is used for dynamic manipulation and rendering. It can be accessed and modified using JavaScript.

### Semantic HTML

Semantic elements are HTML elements that express meaning about the structure of the document, which aids in SEO, screen reading, and maintainability.

### HTML Rendering

HTML files are rendered into visual pages by the browser. The rendering engine translates HTML and CSS into the DOM and then paints it on the screen.

## Syntax and Language Specification

HTML adheres to rulesets laid out by W3C or the WHATWG. Here is a minimal skeleton for an HTML5 document:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Document Title</title>
</head>
<body>
    Content here.
</body>
</html>
```

---

## Example Page: Creating and Running an HTML File

1. **Open a terminal and navigate to your preferred directory.**

2. **Create/Open the file in your favorite text editor.**

    ```bash
    nano index.html  # or vi, vim, emacs, code, etc.
    ```

3. **Paste the following HTML example into the text editor and save.**

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Sample Page</title>
        <link rel="stylesheet" href="styles.css">
        <script src="scripts.js"></script>
    </head>
    <body>
        <header>
            <h1 id="title">Sample Page</h1>
        </header>
        <nav>
            <ul>
                <li><a href="#section1">Section 1</a></li>
                <li><a href="#section2">Section 2</a></li>
                <li><a href="#section3">Section 3</a></li>
            </ul>
        </nav>
        <button id="colorButton">Change Color</button>
        <div id="hoverDiv">Hover over me</div>
        <main>
            <section id="section1">
                <h2>Section 1: Paragraphs and Links</h2>
                <p id="textElement">This is a paragraph.</p>
                <a href="https://example.com" target="_blank">External Link</a>
            </section>
            <section id="section2">
                <h2>Section 2: Forms and Inputs</h2>
                <form id="sampleForm">
                    <label for="name">Name:</label>
                    <input type="text" id="name" name="name"><br>

                    <label for="email">Email:</label>
                    <input type="email" id="email" name="email"><br>

                    <input id="submit" type="submit" value="Submit">
                </form>
            </section>
            <section id="section3">
                <h2>Section 3: Lists and Tables</h2>
                <ul>
                    <li>Item 1</li>
                    <li>Item 2</li>
                </ul>
                <table>
                    <thead>
                        <tr>
                            <th>Header 1</th>
                            <th>Header 2</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Data 1</td>
                            <td>Data 2</td>
                        </tr>
                    </tbody>
                </table>
            </section>
        </main>
        <footer>
            <p>Copyright 2023</p>
        </footer>
    </body>
    </html>
    ```

4. **To view the HTML file in a browser, you can either:**
    - Double-click on the `index.html` file, or
    - Run the following command in the terminal to open it in the default web browser:

    ```bash
    xdg-open index.html  # Linux
    start index.html  # Windows
    open index.html  # macOS
    ```
## Commonly Used HTML Tags

Below are some of the most commonly used HTML tags that you will likely encounter and potentially use frequently as a web developer.

### Structural Tags

#### `<html>`
Defines the root of an HTML document. All other tags are nested within this element.

#### `<head>`
Contains meta information about the document and links to scripts and stylesheets.

#### `<body>`
Wraps all the content that is rendered in the browser window.

### Text Formatting Tags

#### `<h1>`, `<h2>`, ..., `<h6>`
Defines headings. `<h1>` is the highest level of heading, and `<h6>` is the lowest.

#### `<p>`
Defines a paragraph.

#### `<strong>`
Defines strong emphasis on its content, typically displayed as bold text.

#### `<em>`
Defines emphasis on its content, typically displayed as italic text.

### Link and Media Tags

#### `<a>`
Defines hyperlinks to other pages or resources.

#### `<img>`
Embeds an image into the document. Requires `src` attribute to point to the image URL.

#### `<video>`
Embeds a video file into the document, allowing for native video playback.

### List Tags

#### `<ul>`
Defines an unordered list. Used in conjunction with `<li>` elements.

#### `<ol>`
Defines an ordered list. Also used with `<li>` elements.

#### `<li>`
Defines a list item that is part of either an ordered or unordered list.

### Form Tags

#### `<form>`
Defines an HTML form containing input elements like text fields, checkboxes, etc.

#### `<input>`
Defines an input field. The `type` attribute specifies the kind of input.

#### `<textarea>`
Defines a multiline text input control.

#### `<button>`
Defines a clickable button, typically used for form submission or JavaScript interactions.

### Semantic Tags

#### `<header>`
Defines a container for introductory content or navigational aids.

#### `<footer>`
Defines a container typically containing metadata, authorship, copyright information, etc.

#### `<main>`
Specifies the main content area of a document.

#### `<article>`
Specifies self-contained content that could be syndicated independently of the rest of the page.

#### `<section>`
Defines a standalone section within an HTML document, usually with its own heading.

#### `<nav>`
Defines a section of a page containing navigation links.

### Special Container Tags

#### `<canvas>`
This tag is used to draw graphics via JavaScript. It's a part of HTML5 and allows for the dynamic rendering of 2D shapes and bitmap images. The `<canvas>` element itself is simply a container for graphics. You must use JavaScript to actually draw the graphics.

#### `<div>`
The `<div>` element is a generic container for flow content that by itself does not represent anything. It can be used to group elements for styling purposes using the class or id attributes, or both. It's often used in conjunction with CSS and JavaScript to manipulate blocks of content.

Both `<canvas>` and `<div>`tags offer powerful features for manipulating web content, albeit in very different capacities. `<canvas>` is specialized for graphical and visual content manipulated via JavaScript, while `<div>` is a general-purpose container used for layout and styling.
