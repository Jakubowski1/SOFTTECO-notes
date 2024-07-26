_JSX_ is a syntax extension for JavaScript that lets you write HTML-like markup inside a JavaScript file.
- Every JSX tag is converted to `React.createElement` call and its object representation.
- JSX Expressions, which are written inside curly brackets, allow only things that evaluate to some value like string, number, array map method and so on.
- `undefined`, `null`, and `boolean` are not displayed on the UI when used inside JSX.

### ==Note==

JSX and React are two separate things. They’re often used together, but you _can_ use them independently of each other. JSX is a syntax extension, while React is a JavaScript library.

#### Rules of JSX

1. Returning a single root element
2. All tags must be closes
3. camelCase for all names like className instead of class 

Important cheat sheet https://transform.tools/html-to-jsx

#### Fun remarks

- You must wrap every JSX tag because they are are transformed into JS objects. 
- JSX turns into JavaScript and attributes written in JSX become keys of JavaScript objects.
-  `<> </>` this is called Fragment and does not leave a trace in DOM tree

### How to convert JSX to React.createElement 
```js
React.createElement(type, [props], [...children])
```

```js
{   
 type: 'h1',   
 props: {     
   children: 'This is JSX'   
 }
}
```

Below a simple example"

```jsx
<h1 id="jsx">This is JSX</h1>
```

Same as

```js
React.createElement("h1", { id: "jsx" }, "This is JSX");
```

Same as
```js
{ 
  type: 'h1', 
  props: { 
   id: 'jsx',
   children: 'This is JSX'
  } 
}
```

Now with a function inside
```jsx
    <button id="btn" onClick={this.handleOnClick}>
        Click Here
      </button>
```

```js
React.createElement("button", {
  id: "btn", 
  onClick: function() {}
}, "Click Here")
```


`React.Fragment`

> _Fragments_ let you group a list of children without adding extra nodes to the DOM.

