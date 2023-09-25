# React.js

React is a JavaScript library for building user interfaces. It is maintained by Facebook and a community of individual developers and companies. 

[Wikipedia](https://en.wikipedia.org/wiki/React_(software))  
[React Learn](https://react.dev/learn)

## Prerequisites

Ensure Node.js is installed; if not, consult the previous Node.js installation guide.

## Installation

### Using Create React App

React itself is a library, not a standalone software. Create React App provides a minimal setup:

```bash
npx create-react-app my-app
cd my-app
```

### Alternative Stacks

- `Next.js`: For server-rendering and static generation.
- `Remix`: Rich nested layouts with optimal loading.
- `Gatsby`: For static sites.
- `Expo`: For React Native projects.

### Run the App

```bash
npm start
```

Access the app at http://localhost:3000.


## Creating Our First Page

### Create HelloWorld Component

1. **Navigate to the `src` folder and create a new file named `HelloWorld.js`**

    ```bash
    code src/HelloWorld.js
    ```

2. **In `HelloWorld.js` add the following code:**

    ```javascript
    import React from 'react';

    function HelloWorld() {
      return (
        <div>
          <h1>Hello, World!</h1>
        </div>
      );
    }

    export default HelloWorld;
    ```

### Update App Component

1. **Open `src/App.js` and import the `HelloWorld` component:**

    ```javascript
    import HelloWorld from './HelloWorld';
    ```

2. **Replace the `return` statement in `App.js` to include `HelloWorld`**

    ```javascript
    function App() {
      return (
        <div className="App">
          <HelloWorld />
        </div>
      );
    }
    ```

### Applying CSS

1. **Create a new CSS file:**

    ```bash
    code src/HelloWorld.css
    ```

2. **Apply styles in `HelloWorld.css`:**

    ```css
    h1 {
      color: blue;
    }
    ```

3. **Import the CSS in `HelloWorld.js`:**

    ```javascript
    import './HelloWorld.css';
    ```

## Testing Your First Page

1. **Save all the changes and the development server should automatically reload the page.**

2. You should now see a "Hello, World!" message styled in blue.

## Key Concepts

**`Declarative`**: Enables straightforward UI views that automatically update with state changes.

**`Components`**: UI's reusable, self-contained building blocks, either as functional or class-based elements.

**`Function Components`**:Function components are simpler and easier to test, they promote the use of hooks and often don't have their own state.

**`React Hooks`**: Hooks are functions that let you 'hook into' React state and lifecycle features from function components.

**`Virtual DOM`**: React maintains a virtual DOM that helps in efficient updates and rendering.

**`Class Components`**: Class components make use of ES6 classes and often contain state and lifecycle methods.

**`Server Components`**: React server components aim to provide a modern UX with a server-driven mental model.

**`Routing`**: For client-side routing in React, libraries like React Router or Next.js can be used.

**`JSX`**: JavaScript XML is a syntax extension for JavaScript, which is used with React to describe what the UI should look like.


## Directory and File Structure of a React Project

When you initialize a new React application using `create-react-app`, several files and folders are generated automatically to give you a good starting point for development.

### Root Directory

**`node_modules/`**: This directory contains all the npm packages and libraries that your project depends on.
  
**`public/`**: This directory contains the static assets that will be served directly by the web server. It includes the `index.html` file where your React app is attached.

  - `index.html`: The main HTML page that is loaded when someone visits your app.
  - `favicon.ico`: The icon for your app typically shown in the browser's address bar.

**`src/`**: This is where the React application code lives. All the components, styles, and logic are contained here.

  - `App.js`: The root component of your React application.
  - `index.js`: The JavaScript entry point file, where the ReactDOM renders the App component.
  - `reportWebVitals.js`: A file for measuring performance in production.
  - `setupTests.js`: Configuration file for Jest testing setup.

**`package.json`**: This file contains metadata about the project and lists its dependencies, scripts, and other configurations.

**`README.md`**: Project documentation.

### Scripts and Commands

Inside `package.json`, you'll find scripts for running tasks like starting the development server, building the app for production, and running tests.

- `npm start`: Starts the development server.
- `npm run build`: Compiles the application for production.
- `npm test`: Runs the test watcher in an interactive mode.
  
### Recommended Practices

1. **Component Organization**: It is a good practice to keep related components together inside a folder, often with their own styles and tests.

    ```
    src/
    └── components/
        └── MyComponent/
            ├── MyComponent.js
            ├── MyComponent.css
            └── MyComponent.test.js
    ```

2. **Utility Functions**: Reusable logic can be moved to a `utils/` folder.

3. **Constants**: Shared constants can be organized into a `constants/` folder.

4. **State Management**: If using Redux or any other state management library, you can include folders like `actions/`, `reducers/`, and `middleware/`.
