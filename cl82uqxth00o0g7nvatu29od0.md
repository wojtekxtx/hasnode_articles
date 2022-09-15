## React Hooks...

![react hooks](https://cdn.hashnode.com/res/hashnode/image/upload/v1663233877551/vacdYIrhf.png)

The introduction of **Hooks** in **React** 16.8.0 was initially met with a dose of skepticism. The developers soon found it an outstanding addition that allowed for a much more declarative and efficient solution to writing code.

Currently, two years later, **Hooks** have become a standard part of the **React** ecosystem, and there is a push to use **Hooks** over **Class Components**.

# How Hooks Replace Class Components

The primary purpose of using the **Class Component** was to obtain access to the state and the life cycle methods, which were unavailable in the **Functional Components**. **Hooks** allows the use of these features in the **Functional Components** , without using the less performant **Class Component** counterparts.

Let’s look at the **Hooks** that ship with **React**. It is assumed that you are familiar with the basics of **React**

# useState

The `useState` hook is used to create thing called `state variable`.

The syntax is `const [<varName>, set<varName>] = useState(initialState)`.

```tsx
function Counter() {
	const [count, setCount] = useState(0);
	return (
		<div>
			<h2>{count}</h2>
			<button onClick={() => setCount(count + 1)}>Increment</button>
		</div>
	);
}
```

We can use the `setCount` function to update the **state** of the `count` **variable**. Just compare it to the **Class Component** counterpart:

```tsx
class Counter extends React.Component {
	state = {
		count: 0,
	};

	render() {
		return (
			<div>
				<h2>{this.state.count}</h2>
				<button
					onClick={() =>
						this.setState({
							count: this.state.count + 1,
						})
					}
				>
					Increment
				</button>
			</div>
		);
	}
}
```

Not only does **Functional Components** are more performant, but they are also easier to read and understand.

# useEffect

`useEffect` is another standard **Hook**. Its principal purpose is to execute life cycle methods in a **Functional Component**.

Let’s explore the **life cycle methods** you can replace:

## componentDidMount

`componentDidMount` runs when the **component is mounted**. It is typically used to fetch data through _API calls_ and update the state. The **Hook** alternative is:

```tsx
useEffect(() => {
	// execute when component is mounted
}, []);
```

## componentDidUpdate

`componentDidUpdate` runs when a piece of **state** or **prop data** is updated. It is used to update associated data once a piece of data is updated. The **Hook** alternative is:

```tsx
useEffect(() => {
	// execute when `count` is updated
}, [count]);
```

You can also omit the **dependency array** ([count] in this case) if you only want to run the `useEffect` callback run on every render.

## componentWillUnmount

`componentWillUnmount` runs before the **component is unmounted**. It is used as a **clean-up function**, with the primary focus on removing `timers` or `listeners`

The **Hook** alternative is:

```tsx
useEffect(() => {
	return () => {
		// execute when component will be unmounted
	};
}, []);
```

## useContext

The `useContext` **Hook** allows you to access the context, the **state management solution** that ships with **React**. The syntax is const `<varName> = useContext(<Context>)`.

```tsx
function Counter() {
	const { count, setCount } = useContext(CounterContext);
	return (
		<div>
			<h2>{count}</h2>
			<button onClick={() => setCount(count + 1)}>Increment</button>
		</div>
	);
}
```

**NOTE:** The Component needs to be wrapped in a `Context.Provider Component` as it looks up the **React Virtual DOM** for the Context

## useRef

`useRef` is a **Hook** that allows you to store a **variable that persists** between the re-renders.

The main difference between a **state** and **ref** variables is when a **state** variable is updated, the UI is re-rendered, whereas, it does not do the same for a **ref**. It is generally used to store a reference to DOM elements.

The syntax is `const <varName> = useRef(initialValue)` and the value is accessible through the current property.

```tsx
function FancyDiv() {
	const div = useRef();

	const handleClick = () => {
		// `div.current` is a reference to the DOM element
		div.current.style.color = "red";
	};

	return (
		<>
			<div ref={div}>{/* ... */}</div>
			<button onClick={handleClick}>Click me</button>
		</>
	);
}
```

## useCallback

`useCallback` is a **Hook** that allows you to memorize (an optimization practice in Computer Science) a function. It is useful when you want to prevent unnecessary renders.

The syntax is `const <varName> = useCallback(<function>, [<dependencies>])`;

```tsx
function Component() {
   const memoizedCallback = useCallback(() => {
      doSomething(a, b);
   }, [a, b]);

   return (
      /* ... */
   );
}
```

## useMemo

`useMemo` is a **Hook** that allows you to **memoize any value**. Just like `useCallback`, it is beneficial to prevent unnecessary renders. It is generally used to memoize expensive computations.

The syntax is `const <varName> = useMemo(<function>, [<dependencies>])`;

```tsx
function Component() {
   const memoizedValue = useMemo(() => {
      return computeExpensiveValue(a, b);
   }, [a, b]);

   return (
      /* ... */
   );
}
```

## useReducer

`useReducer` is a **Hook** that allows you to manage the state of a component. It serves the same purpose as the `useState` **Hook** , but it follows the **Redux** pattern to _manage & update the state_.

The syntax is `const [<varName>, dispatch] = useReducer(<reducer>, initialState)`;

```tsx
const initialState = { count: 0 };

function reducer(state, action) {
	switch (action.type) {
		case "increment":
			return { count: state.count + 1 };
		default:
			throw new Error();
	}
}

function Counter() {
	const [state, dispatch] = useReducer(reducer, initialState);
	return (
		<div>
			<h2>{state.count}</h2>
			<button onClick={() => dispatch({ type: "increment" })}>
				Increment
			</button>
		</div>
	);
}
```

# Custom Hooks

**React** also allows developers to create their own **Hooks** from scratch.

Let’s create a custom **Hook** called `useFetch`, which will fetch data from an **API** and return it along with `loading` & `error` states.

```tsx
function useFetch(url) {
	const [data, setData] = useState(null);
	const [loading, setLoading] = useState(true);
	const [error, setError] = useState(null);

	useEffect(() => {
		(async () => {
			setLoading(true);
			try {
				const response = await fetch(url);
				const jsonData = await response.json();
				setData(jsonData);
			} catch {
				setError(error);
			}
			setLoading(false);
		})();
	}, [url]);

	return { data, loading, error };
}
```