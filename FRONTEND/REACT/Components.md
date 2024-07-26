**Mounting** - adding a component to the page :)

React components are regular JavaScript functions, but **their names must start with a capital letter** or they won’t work!

The `export default` prefix is a standard JavaScript syntax. It lets you mark the main function in a file so that you can later import it from other files.

Define components at the top level for clarity. 

#### Named export 

```jsx
export function Profile() {  

// ...  

}
```

And this is how you import it

```jsx
import { Profile } from './Gallery.js';

export default function App() {  
	return <Profile />;  
}
```

#### Default export

```jsx
export default function Profile(){
// ...
}
```

```jsx
import Profile from './Profile.js';
```

Now let's talk about the legacy of React. When class components were a thing.

To define a React component as a class, extend the built-in `Component` class and define a `render` method.
```js
import { Component } from 'react';  

class Greeting extends Component {  
	render() {  
		return <h1>Hello, {this.props.name}!</h1>;  
	}  
}
```