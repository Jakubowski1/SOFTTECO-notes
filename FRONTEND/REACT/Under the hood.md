
#

				`# React Renderer

```jsx
import ReactDOM from "react-dom/client";
ReactDOM.render(<App />, container)
```
ReactDOM in turn, recursively creates nodes depending on their 'type' property and appends them finally to the DOM.

React Native uses React library, but not ReactDOM as the render. Instead, the package react-native itself is a renderer.

Reactive variables are those which can be used as dependencies. Mutable values (including global variables) aren’t reactive.

### Reconcilation

React's way of diffing the virtual DOM tree with the updated virtual DOM to determine the most efficient way to update the real DOM.