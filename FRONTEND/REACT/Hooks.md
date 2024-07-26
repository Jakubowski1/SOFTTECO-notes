CAN ONLY BE CALLED IN FUNCTIONAL COMPONENTS
CAN NOT BE CALLED CONDITIONALLY
### State Hooks

- Use useState whenever you manage a JS primitive
- Use useReducer whenever you manage an object or array

#### useState()

 Every time this function is called, React re-renders the component to render the new state.

```js
function ImageGallery() {  

const [index, setIndex] = useState(0);  

// ...
```

An example with an asynchronous touch
```js
const App = () => {
  const [count, setCount] = React.useState(0);
  const handleIncrease = () => {
    setTimeout(() => setCount(count + 1), 1000);
  };
  const handleDecrease = () => {
    setTimeout(() => setCount(count - 1), 1000);
  };
  return (
    <div>
      Count: {count}
      <hr />
      <div>
        <button type="button" onClick={handleIncrease}>
          Increase
        </button>
        <button type="button" onClick={handleDecrease}>
          Decrease
        </button>
      </div>
    </div>
  );
};
```



A good rule of thumb may be: always use a function in useState's update function if your state update depends on your previous state.

#### useReducer()

Powerful way to manage complex state logic in functional components.

```js
const [state, dispatch] = useReducer(reducer, initialArg, init?)
```

`init?` An optional function that can be used to create the initial state lazily.

Pretty complex example:

```js
import React from 'react';

const initialTodos = [...];

const todoReducer = (state, action) => {
  switch (action.type) {
    case 'DO_TODO':
      return state.map(todo => {
        if (todo.id === action.id) {
          return { ...todo, complete: true };
        } else {
          return todo;
        }
      });
    case 'UNDO_TODO':
      return state.map(todo => {
        if (todo.id === action.id) {
          return { ...todo, complete: false };
        } else {
          return todo;
        }
      });
    default:
      return state;
  }
};

const App = () => {
  const [todos, dispatch] = React.useReducer(
    todoReducer,
    initialTodos
  );
  const handleChange = todo => {
    dispatch({
      type: todo.complete ? 'UNDO_TODO' : 'DO_TODO',
      id: todo.id,
    });
  };
  return (
    <ul>
      {todos.map(todo => (
        <li key={todo.id}>
          <label>
            <input
              type="checkbox"
              checked={todo.complete}
              onChange={() => handleChange(todo)}
            />
            {todo.task}
          </label>
        </li>
      ))}
    </ul>
  );
};
```
### Context Hooks
#### useContext()

Syntax:
```js
const value = useContext(SomeContext)
```

Allows you to read and write to context. 

Exemplary usage:

```js
import { createContext, useContext } from 'react';

const ThemeContext = createContext(null);

export default function MyApp() {
  return (
    <ThemeContext.Provider value="dark">
      <Form />
    </ThemeContext.Provider>
  )
}

function Form() {
  return (
    <Panel title="Welcome">
      <Button>Sign up</Button>
      <Button>Log in</Button>
    </Panel>
  );
}

function Panel({ title, children }) {
  const theme = useContext(ThemeContext);
  const className = 'panel-' + theme;
  return (
    <section className={className}>
      <h1>{title}</h1>
      {children}
    </section>
  )
}

function Button({ children }) {
  const theme = useContext(ThemeContext);
  const className = 'button-' + theme;
  return (
    <button className={className}>
      {children}
    </button>
  );
}

```
### Ref Hooks
#### useRef()

**Does not trigger a re-render**

`useRef` is a React Hook that lets you reference a value that’s not needed for rendering. It returns an object with one current property. 

By using a ref, you ensure that:

- You can store information between re-renders (unlike regular variables, which reset on every render).
- Changing it does not trigger a re-render (unlike state variables, which trigger a re-render).
- The information is local to each copy of your component (unlike the variables outside, which are shared).

```js
const ref = useRef(initialValue)
```

So I read about this and it kinda doesn't make much sense to use it XD
But it is useful for manipulating the DOM.

```js

import { useRef } from 'react';
function MyComponent() { 

const inputRef = useRef(null); 
// ...
return <input ref={inputRef} />;

function handleClick() { 
	inputRef.current.focus();
}
```
#### useImperativeHandle()

`useImperativeHandle` is a React Hook that lets you customize the handle exposed as a ref
```js
useImperativeHandle(ref, createHandle, dependencies?)
```
### Effect Hooks
#### useEffect()

This hook let's you synchronize a component with an external system.
Some components need to stay connected to the network, some browser API, or a third-party library, while they are displayed on the page. These systems aren’t controlled by React, so they are called external.

```js
useEffect(setup, dependencies?)
```

```js
useEffect(() => {
	//The code that we want to run as a side effect
	// The optional return funtion
}, []); // The dependency array (what I want to listen to)
```


1. A _setup function_ with setup code that connects to that system.
    - It should return a _cleanup function_ with cleanup code that disconnects from that system.
2. A list of dependencies including every value from your component used inside of those functions.

```js
import { useEffect } from 'react';  
import { createConnection } from './chat.js';  
  
function ChatRoom({ roomId }) {  
	const [serverUrl, setServerUrl] = useState('https://localhost:1234');  
	useEffect(() => {  
		const connection = createConnection(serverUrl, roomId);  
		connection.connect();  
		return () => {  
			connection.disconnect();  
		};  
	}, [serverUrl, roomId]);  
// ...  
}
```
### Performance Hooks
#### useMemo()

This helps us with caching outputs from functions that are working pretty slow. 
It can also be used in referential equality. So the situation works like that, objects change they reference (which is used to equalization of them) every time the page renders. 

On the initial render, `useMemo` returns the result of calling `calculateValue` with no arguments.

During next renders, it will either return an already stored value from the last render (if the dependencies haven’t changed), or call `calculateValue` again, and return the result that `calculateValue` has returned.

```js
const cachedValue = useMemo(calculateValue, dependencies)
```

The code below allows us to cache a calculation between re-renders.

```js
import { useMemo } from 'react';

function TodoList({ todos, tab }) {
  const visibleTodos = useMemo(
    () => filterTodos(todos, tab),
    [todos, tab]
  );
}
```
#### useCallback()

React's useCallback Hook can be used to **optimize the rendering behavior**

Freezes a function if dependencies are not changed. 

```js
const cachedFn = useCallback(fn, dependencies)
```

```js
import { useCallback } from 'react';

export default function ProductPage({ productId, referrer, theme }) {
  const handleSubmit = useCallback((orderDetails) => {
    post('/product/' + productId + '/buy', {
      referrer,
      orderDetails,
    });
  }, [productId, referrer]);
```

The fn parameter is the function you want to cache. It can take any arguments and return any values. Here's a concise breakdown of its behavior:

- Initial Render: React returns your function to you without calling it.
- Subsequent Renders:
- Unchanged Dependencies: React returns the same function as before.
- Changed Dependencies: React returns the new function you passed in the current render and stores it for future use.

Use call  back return a function you have frozen. 