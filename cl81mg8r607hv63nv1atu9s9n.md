## React Cheat Sheet (with React 18)

Fret not my friend, now you no longer need to stumble around in the dark! This article is a memory aid for all things **React** (focusing on **Functional Components** only).

# Create a React App

```
// Initialize a new app
npx create-react-app my-app-name
// or
yarn create react-app my-app-name

// Run the app (default port is 3000)
cd my-app-name
npm start
// or
yarn start
```

# Render a React Component

```jsx
import ReactDOM from "react-dom/client";
import App from "./App";
// ...
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```

# Functional Components

```jsx
const Component = () => {
  return <div>Hello World</div>;
};
```

## Pre-requisites:

1. Must have an **uppercase first letter**
2. Must return **JSX**

Since **React 17**, there is no need to `import React from 'react'`

# Importing Components

`Components` can be **exported** & **imported** from other files, thus promoting **Code splitting** and **reusability**.

**Default Export**

```jsx
function Component = () => 
    <div>Hello World</div>
export default Component
```

and in another file:
```jsx
import Component from './Component'
function App = () => <Component />
```

**Named Export**

```jsx
export function Component = () => 
    <div>Hello World</div>
```

and in another file:
```jsx
import { Component } from './Component'
function App = () => <Component />
```

**Lazy Loading**

```jsx
function Component = () => 
    <div>Hello World</div>
export default Component
```

and in another file:
```jsx
import { lazy, Suspense } from 'react'
const Component = lazy(() => import('./Component'))
function App = () => (
  <Suspense fallback={<div>Loading...</div>}>
    <Component />
  </Suspense>
)
```

# JSX Rules

## 1. Must return a single element

```jsx
const Component = () => {
  // INVALID: return <div>Hello</div><div>World</div>;
  return <div>Hello World</div>;
};

// or

const Component = () => {
  // `<React.Fragment>` can be replaced with just `<>`

  // On wrapping the children with any element,
  // you can create as many levels of nesting as you want
  return (
    <React.Fragment>
      <div>Hello</div>
      <div>World</div>
    </React.Fragment>
  );
};
```

## 2. Opening tags need to be closed (can use self-closing tags)

```jsx
const Component = () => {
  // INVALID: return <input>;
  return <input />;
};
```

## 3. Use React attributes instead of HTML attributes

```jsx
const Component = () => {
  // INVALID: return <div class="foo">Hello World</div>;
  return <div className="foo">Hello World</div>;
};
```

# Styling

To use styling you do need to add `css-loader` & `style-loader` to your `webpack.config.js` if you are manually building your **React** app. Luckily, `create-react-app` comes **pre-configured** to enable styling.

## CSS Imports

```css
/* app.css */
.redText {
  color: red;
}
```

```jsx
import "./app.css";

function App() {
  return <h1 className="redText">
    Hello World
  </h1>;
}
```

## Inline CSS

```jsx
const Component = () => {
  return <div style={{ color: "red" }}>
    Hello World
  </div>;
};
```

## CSS Modules

```css
/* app.css */
.redText {
  color: red;
}
```

```jsx
import classes from "./app.css";

function App() {
  return <h1 className={classes.redText}>
    Hello World
  </h1>;
}
```

# Embedding JavaScript

## Prerequisites:

1. Must be an **expression** with a return value (can be **JSX** too)
2. Must be wrapped in **curly braces** (`{}`)

```jsx
const Component = () => {
  const isLoggedIn = true;
  return <div>
    {isLoggedIn ? "User is Authenticated" : <LogIn />}
  </div>;
};
```

## Component Properties

These are the **values with which the component is initialized**. `props` are accepted as the function parameter.

```jsx
// no props
function App() {
  return <Person name="Mike" age={29} />;
}

// with props
const Person = (props) => {
  return (
    <h1>
      Name: {props.name}, Age: {props.age}
    </h1>
  );
};

// with destructured props
const Person = ({ name, age }) => {
  return (
    <h1>
      Name: {name} Age: {age}
    </h1>
  );
};
```

## Children

`children` is a special `prop` passed to a component that is rendered inside the component.

```jsx
const Component = ({ children }) => {
  return <div>{children}</div>;
};

const App = () => {
  return (
    <Component>
      <h1>Hello World</h1>
    </Component>
  );
};
```

## Default Props

```jsx
// JavaScript-ish syntax
const Component = ({ name = "Mike" }) => {
  return <div> {name} </div>;
};

// or React-ish syntax
const Component = ({ name }) => {
  return <div> {name} </div>;
};

Component.defaultProps = {
  name: "Mike",
};
```

## Lists

```jsx
const people = [
  { id: 1, name: "Mike" },
  { id: 2, name: "Peter" },
  { id: 3, name: "John" },
];
```

```jsx
function App() {
  return people.map((person) => (
    <div key={person.id}>{person.name}</div>;
  ));
}
```

The `key` is an optional `prop` available on all elements, it is used internally by **React** to keep track of which elements have changed. For lists, it is highly recommended that you do add a `key`.

## Prop Destructuring

`Person` is a component that accepts a `name` prop.

```jsx
function App() {
  return people.map(({id, ...person}) => (
    <Person key={id} {...person} />;
  ));
}
```

# Events

```jsx
const clickHandler = () => alert("Hello World");

function App() {
  return (
    <>
      <h1>Welcome to my app</h1>
      <button onClick={clickHandler}>
        Say Hi
      </button>
    </>
  );
}
```

or inline...

```jsx
function App() {
  return (
    <>
      <h1>Welcome to my app</h1>
      <button onClick={() => alert("Hello World")}>
        Say Hi
      </button>
    </>
  );
}
```

We can also pass arguments to the handler

```jsx
const clickHandler = (message) => alert(message);
function App() {
  return (
    <>
      <h1>Welcome to my app</h1>
      <button onClick={() => clickHandler("Hello World")}>
        Say Hi
      </button>
    </>
  );
}
```

The **events** by default pass the **event object** as the first argument.

```jsx
const clickHandler = (event) => console.log(event.target);
function App() {
  return (
    <>
      <h1>Welcome to my app</h1>
      <button onClick={clickHandler}>
        Say Hi
      </button>
    </>
  );
}
```

You can even **pass on a handler from a parent** and execute it inside the child

```jsx
function Todo({item, onDelete}) {
    return (
      <div>
        {item}
        <button onClick={() => onDelete(item)} />
      </div>
    )
}

function Todos() {
  const handleDelete = (todo) => {
    const newTodos = todos.filter(item => item !== todo)
    setTodos(() => newTodos)
  }

  return (
    {todos.map((todo) => (
       <Todo item={todo} onDelete={handleDelete}/>
    ))}
  )
}
```

# Hooks

**Hooks** are functions that let you “hook into” **React** state and lifecycle features from function components.

Prerequisites:

1. **Hook** always starts with the 'use' prefix
2. Must be invoked only in a **React** **functional component**
3. Must be called only at the top level of a **functional component**
4. Declaration CAN NOT be called conditionally

## useState

`useState` is a **hook** that lets you **manage the state** in a **functional component**.

```jsx
function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

## useEffect

`useEffect` is a hook that lets you access **lifecycle methods** in a **functional component**.

```jsx
function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Initialized");
    // clean up function runs before the component is unmounted
    return () => {
      console.log("Cleaned up");
    };
  }, []); // empty array: run during mount only

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]); // array with count: run everytime `count` changes

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

## useContext

`useContext` is a **hook** that returns the data for the given `context` (the **state management tool** that ships with **React**)

```jsx
const ThemeContext = createContext("light");

function App() {
  return (
    <ThemeContext.Provider value="light">
      <Component />
    </ThemeContext.Provider>
  );
}
```

```jsx
function Component() {
  const theme = useContext(ThemeContext); // returns 'light'
  return (
    <div>
      <p>The current theme is: {theme}</p>
    </div>
  );
}
```

## useReducer

`useReducer` is a **hook** that lets you manage state in **functional components**, but unlike `useState` it uses the **Redux** pattern

```jsx
function App() {
  const [count, dispatch] = useReducer((state, action) => {
    switch (action) {
      case "increment":
        return state + 1;
      case "decrement":
        return state - 1;
      default:
        throw new Error();
    }
  }, 0);

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => dispatch("increment")}>
        +
      </button>
      <button onClick={() => dispatch("decrement")}>
        -
      </button>
    </div>
  );
}
```

## useCallback

The `useCallback` **hook** returns a **memoized version of the callback**, with the sole purpose of **optimizing performance**.

```jsx
function App() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => 
        setCount((c) => c + 1), []);

  return (
    <div>
      <p>{count}</p>
      <button onClick={increment}>+</button>
    </div>
  );
}
```

## useMemo

The `useMemo` **hook** returns a **memoized version of the value** produced by the **callback**. Just like `useCallback`, `useMemo` is a **performance optimization hook**.

```jsx
function App() {
  const [count, setCount] = useState(0);

  const memoizedIncrement = useMemo(() => {
    return () => setCount((c) => c + 1);
  }, []);

  return (
    <div>
      <p>{count}</p>
      <button onClick={memoizedIncrement}>+</button>
    </div>
  );
}
```

## useRef

The `useRef` **hook** returns a `mutable ref object` whose `.current` property is initialized to the passed argument (`initialValue`). The returned object will persist for the **full lifetime of the component** unless manually changed.

```jsx
function App() {
  const inputRef = useRef(null);
  const onButtonClick = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={onButtonClick}>
        Focus on the input
      </button>
    </div>
  );
}
```

## useTransition

The `useTransition` **hook** lets you **mark less-urgent actions as transitions**.

```jsx
function App() {
  const [input, setInput] = useState("");
  const [data, setData] = useState([...items]);
  const [isPending, startTransition] = useTransition();

  useEffect(() => {
    // input change is prioritized over filtering a long list
    startTransition(() => {
      setData(items.filter((i) => i.includes(input)));
    });
  }, [input]);

  const updateInput = (e) => setInput(e.target.value);

  return (
    <div>
      <input value={input} onChange={updateInput} />
      <ul>
        {data.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </div>
  );
}
```

## useDeferredValue

The `useDeferredValue` **hook** lets you **intentionally defer updating** values so they don't slow down other parts of the page

```jsx
function App() {
  const deferredValue = useDeferredValue(value);
  return <MyComponent value={deferredValue} />;
}
```

That's all folks! If you think I have missed something, please add them in the comments 👇

**Happy Developing!**