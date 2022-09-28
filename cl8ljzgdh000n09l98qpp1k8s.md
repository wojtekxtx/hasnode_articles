## 11 Advanced React Interview questions (with detailed answers)

# Questions
## What is the **React Virtual DOM**?

**Virtual DOM** is a concept where a **virtual representation** of the **real DOM** is kept inside the **memory** and is **synced with the actual DOM** by a library such as **ReactDOM**.

The **virtual DOM** is an **object** that represents the **real DOM** in the memory. Since **DOM** updates are an integral part of any web app but are the **costliest operation** in the world of **frontend**, the **virtual DOM** is utilized to check for parts of the app that need to be updated & update only those parts, thus **significantly boosting performance**.

## Why do we need to `transpile` **React** code?

**React** code is written in **JSX**, but no browser can execute **JSX** directly as they are built to read only regular **JavaScript**.

Thus we require to use tools like **Babel** to transpile **JSX** to **JavaScript** so that the browser can execute it.

## What is the significance of `keys` in **React**?

`Keys` in **React** is used to identify unique **VDOM** Elements with their corresponding data driving the **UI**; having them helps **React** optimize rendering by recycling existing **DOM** elements.

`Key` helps **React** identify which items have **changed**, are **added**, or are **removed**, enabling it to reuse already existing **DOM** elements, thus providing a **performance boost**.

For example:

```jsx
const Todos = ({ todos }) => {
  return (
    <div>
      {todos.map((todo) => (
        <li>{todo.text}</li>
      ))}
    </div>
  );
};
```

This would cause new **DOM Elements** to be created everytime `todos` change, but adding the `key` prop (`<li key={todo.id}>{todo.text}</li>`) would result in "dragging" around the **DOM Elements** inside the `ul` tag & updating only the necessary `li`s.

## What is the significance of `refs` in **React**?

`Refs` are variables that allow you to **persist data between renders**, just like `state` variables, but unlike `state` variables, updating `refs` does NOT cause the **component to re-render**.

`Refs` are usually used to, but not restricted to, store reference to **DOM elements**.

## What are the most common approaches for styling a **React** application?

### CSS Classes
**React** allows class names to be specified for a component like class names are set for a **DOM** element in **HTML**.

When developers first start using **React** after developing traditional web applications, they often opt for **CSS classes** as they are already familiar with the approach.

### Inline CSS
Styling **React** elements using **inline CSS** allows styles to be completely scoped to an element. However, **certain styling features are not available with inline styles**. For example, the styling of **pseudo-classes** like `:hover`.

### Pre-processors (Sass, Stylus, and Less)
**Pre-processors** are often used on **React** projects. This is because, like **CSS**, they are well understood by developers and are often already in use if **React** is being integrated into a legacy application.

### CSS-in-JS Modules (Styled Components, Emotion, and Styled-jsx)
**CSS-in-JS modules** are a popular option for styling **React** applications because they integrate closely with **React** components. For example, they allow styles to change based on **React** props at runtime. Also, by default, **most of these systems scope all styles to the respective component being styled**.

## What are some of the performance optimization strategies for **React**?

### Using useMemo
`useMemo` is a React hook that is used for **caching CPU-Expensive functions**. A **CPU-Expensive function** called repeatedly due to **re-renders of a component**, can lead to **slow rendering**.

`useMemo` hook can be used to **cache** such functions. By using `useMemo`, the **CPU-Expensive function** gets called only when it is needed.

`useCallback` can be used to obtain a similar result.

### Lazy Loading
**Lazy loading** is a technique used to **reduce the load time of a React app**. It helps reduce the risk of web app performances to a minimum, by **loading up the components as the user navigates through the app**.

## What is prop drilling and how to avoid it?
Sometimes while developing **React** applications, there is a need to **pass data from a component that is higher in the hierarchy** to a **component that is deeply nested**. To pass data between such components, we pass props from a source component and **keep passing the prop** to the next component in the hierarchy **till we reach the deeply nested component**.

The disadvantage of using `prop drilling` is that the components that should otherwise be not aware of the data have access to the data, moreover, the **code becomes harder to maintain**.

`Prop drilling` can be avoided using the **Context API** or some form of **State Management** library.

## What is the `StrictMode` component and why would you use it?

`<StrictMode />` is a component included with **React** to provide **additional visibility of potential issues** in components. Suppose the application is running in **development mode**. In that case, any issues are logged to the **development console**, but these warnings are not shown if the application is running in **production mode**.

Developers use `<StrictMode />` to find problems such as **deprecated lifecycle methods** and **legacy patterns**, to ensure that all **React** components follow current best practices.

`<StrictMode />` can be **applied at any level of an application component hierarchy**, which allows it to be adopted incrementally within a codebase.

## What are `synthetic events` in **React**?

`Synthetic events` combine the response of different browser's native events into one **API**, ensuring that the **events are consistent across different browsers**. The application is consistent regardless of the browser it is running in.

```jsx
const Component = () => {
  const handleClick = (e) => {
    e.preventDefault(); // synthetic event
    console.log("link clicked");
  };

  return <a onClick={(e) => handleClick}>Click me</a>;
};
```

## Why is it not advisable to update `state` directly, but use the `setState` call?

The conventional way to update `state` is to use the `setState` call. Without using it, the user would still be able to modify the state, but it would not update the **DOM** to reflect the new state.

```jsx
const Component = () => {
  const [count, setCount] = useState(0);
  // let [count, setCount] = React.useState(0);

  const handleClickUpdate = () => {
    setCount((c) => c + 1);
    // count = count + 1; // will not update the DOM
  };

  return (
    <>
      {count}
      <button onClick={handleClickUpdate}>Click me</button>
    </>
  );
};
```

## What are `portals` in **React**?
**Portal** is a recommended way to render children into a **DOM** node that exists outside the **DOM hierarchy** of the parent component.

```jsx
const Portal = ({ children }) => {
  // NOTE: it is advisable to create a new DOM node for the portal
  const portalRoot = document.getElementById("portal-root");

  return ReactDOM.createPortal(children, portalRoot);
};
```