# JavaScript Guide

## Introduction

JavaScript is a high-level, interpreted programming language primarily known for adding interactivity and other behavior to web pages. It's part of the ECMAScript standard and runs not only in the browser but also on servers via Node.js.

### References

- [Wikipedia](https://en.wikipedia.org/wiki/JavaScript)
- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [ECMAScript Specifications](https://www.ecma-international.org/ecma-262/)


---

## Core Concepts

1. **First-class Functions**: Functions in JavaScript are first-class objects.
2. **Prototypes**: JavaScript uses prototypal inheritance.
3. **Event Loop**: Understand how async code works via the event loop.
4. **Closures**: Function objects that have access to variables from their containing function.
5. **Hoisting**: Variables and function declarations moved to the top of their containing scope during compilation.
6. **Strict Mode**: A way to enforce stricter parsing and error handling.

---

## Syntax

JavaScript's syntax is C-style, with semicolons used to separate statements and curly braces to define blocks of code.

```javascript
// This is a single-line comment
const x = 10;  // Declaring a constant

// Defining a function
function add(a, b) {
  return a + b;
}
```

---

## Example Code

Here's a walkthrough to create and run a simple JavaScript code snippet.

1. **Navigate to the directory where you created your index.html file.**

2. **Create/Open the JavaScript file in a text editor.**
   ```bash
   nano script.js  # or vi, vim, emacs, code, etc.
   ```

3. **Paste the following JavaScript code into the text editor.**
   ```javascript
    document.addEventListener('DOMContentLoaded', function() {
    // Reference to the button and div elements
    const colorButton = document.getElementById('colorButton');
    const submit = document.getElementById('submit');
  
    // Function to generate random RGB color
    const getRandomColor = () => {
      const letters = '0123456789ABCDEF';
      let color = '#';
      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    };
  
    // Event listener for button click to change its background color
    colorButton.addEventListener('click', function() {
      const newColor = getRandomColor();
      document.documentElement.style.setProperty('--primary-color', newColor);
    });
  
    // Event listener for div hover to display alert
    submit.addEventListener('click', function() {
      alert('You submited!');
    });
  });

   ```

4. **In your HTML file, make sure to link this JS file inside the head tag.**
   ```html
   <script src="script.js"></script>
   ```

5. **To view the HTML file in a browser.**
   ```bash
    xdg-open index.html  # Linux
    start index.html  # Windows
    open index.html  # macOS
   ```
