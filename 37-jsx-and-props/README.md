JSX & Props
===========

## SWBAT

- Setup a new React app and play around with building things
- Understand how create-react-app works and what it offers a developer
- Learn how to identify components on a page, visually
- See what a React Component actually is (an object, made by a class)
- Build custom components and see initial JSX
- Build modular & reusable components
- See how props are to components as arguments are to functions

## Outline

### History / Context of React

- Why React?
  - React is for building UIs!
- react vs react-dom

### Project Setup

[Try React](https://reactjs.org/docs/try-react.html)
- create-react-app
  ```sh
  npm install -g create-react-app
  create-react-app app-name-here

  cd app-name-here
  npm start
  ```

- Anatomy of a `create-react-app`:
  - `public` => folder containing files served by our web server
  - `src` => all of our React code
    - `index.js` => entry point to the React app; this has `ReactDOM.render` which puts all of our code into the DOM element we tell it to put it into (in our case, `<div id="root">`)
    - `App.js` => our root React component; all apps will have it
    - `App.css`, `index.css` => css files
    - `App.test.js` => test file
    - `registerServiceWorker.js` => helper file for cache stuff
  - `.gitignore` => git ignore
  - `package.json` => your "Gemfile"
  - `README.md` => readme file
- Benefits to using it:
  - Hot Reloading
  - Easily add dependencies
  - Work all in JavaScript

### Component Hello World

The anatomy of a React app:
- `document.getElementById('root')`
- That's where we everything is rendered.

Simplest Component:

```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    return <h1>Hello World!</h1>;
  }
}

export default App;
```

- `React` import is needed in any file where you use JSX.
- `render()` method is required in a Component as that's what will be called to figure out what to eventually render in the browser.

### JSX

- It's **syntatic sugar** for `React.createElement`.
  - Note that JSX won't actually work in browser console!!
  - It's translated by Babel into regular JavaScript.
- rules, differences with HTML
  - Upper case = Component
  - Lower case = HTML to render to DOM
  - Attributes = camelCase
  - Attributes = serve double duty as `props`
  - Stuff in-between open & Close Tags = `children`
- HTML vs Components
  - Lower vs Upper case
  - What gets rendered? Let's inspect it!
- expressions = `{ }`
  - Expressions Evaluate
  - [Expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Expressions): An expression is any valid unit of code that resolves to a value.

**JSX Attributes Example:**

- Attributes we'll see are also our `props` for Components.
- They need some value assigned to them which is either a string or whatever an expression, `{}`, evaluates to.

```javascript
import logo from './logo.svg';

// ... somewhere in render

<img src={logo} alt="some image" />
```

### JSX Extras / Gotchas

Commenting in JSX
- `{/* commented */}`

Any JavaScript reserved words have special names in JSX attributes:
- `class` => `className`
- `for` => `htmlFor`

Data and aria attributes are special. They keep kebab-casing:
- `data-attribute`
- `aria-attribute`


### React.Component

- class syntax review (mod 3)
  - `extends Component` <= what is this?
- Inherits:
  - `render()` <= is required!!
    - Must always return 1 JSX, an array of JSX, or one of the things that renders as nothing (`null`, `true`, `false`, `undefined`): [See React Docs](https://reactjs.org/docs/jsx-in-depth.html#booleans-null-and-undefined-are-ignored)
  - `constructor()`
  - Among many many others.

### Modular Components

- Single Responsibility Principle is used to identify components (most of which are reusable)
- `import` / `export`
  - You can do everything in one file, but please don't!
- **Declarative vs. Imperative**
  - Declarative _declares_ what should happen.
  - Imperative is where you _instruct_ how to make things happen.
  - Abstraction, abstraction, abstraction.
    - Imperative is just abstraction on more lower level imperative stuff.
  - our renders should read like instructions on what to display to the screen

### Component Extras

`constructor()` vs `constructor(props)`
- https://github.com/facebook/react/issues/11671

### Props

- What are they?
  - They are those JSX attributes. On Components, they are called `props`.
  - _Sidenote:_ JSX attributes are still props as we can see in Babel that they are placed in the argument for `props` in `React.createElement()`.
- How do we use them?
  - Same way as attributes on JSX.
  - They are then accessible in your Component via `this.props`.
- Passing props down
  - In doing the above, we can see that `props` are passed down from the parent Component.
  - We also see that you can name your `props` **anything**!
    - You should be naming you props so they make sense within the Component as that is where they are used.
    - Remember that Components are reusable pieces of UI. When possible, they should be self-contained in a way that makes them reusable. Sometimes for different purposes.
- **My favorite analogy:** props are to components as arguments are to functions.
