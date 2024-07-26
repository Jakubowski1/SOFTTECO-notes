On the first glance it looked weird but it actually makes sense to do that. 

Analyze this code to understand why:
 ```js
 import { getImageUrl } from './utils.js';

function Avatar({ person, size }) {
  return (
    <img
      className="avatar"
      src={getImageUrl(person)}
      alt={person.name}
      width={size}
      height={size}
    />
  );
}

export default function Profile() {
  return (
    <div>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi', 
          imageId: 'YfeOqp2'
        }}
      />
      <Avatar
        size={80}
        person={{
          name: 'Aklilu Lemma', 
          imageId: 'OKS67lh'
        }}
      />
      <Avatar
        size={50}
        person={{ 
          name: 'Lin Lanying',
          imageId: '1bX5QH6'
        }}
      />
    </div>
  );
}
```

Usually you don’t need the whole `props` object itself, so you destructure it into individual props.

```js
function Avatar(props) {  

let person = props.person;  
let size = props.size;  
// ...  
}
```

### Specifying a default value for a prop

```js
function Avatar({ person, size = 100 }) {  
// ...  
}
```

### Forwarding props with the JSX spread syntax

Look at the code below it looks pretty repetitive:

```jsx
function Profile({ person, size, isSepia, thickBorder }) {  

return (  

	<div className="card">  
		<Avatar  
			person={person}  
			size={size}  
			isSepia={isSepia}  
			thickBorder={thickBorder}  
		/>  
	</div>  
);  
}
```

```jsx
function Profile(props) {  

return (  
	<div className="card">  
		<Avatar {...props} />  
	</div>  
);  
}
```

### Passing JSX as children

```jsx
import Avatar from './Avatar.js';

function Card({ children }) {
  return (
    <div className="card">
      {children}
    </div>
  );
}

export default function Profile() {
  return (
    <Card>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi',
          imageId: 'YfeOqp2'
        }}
      />
    </Card>
  );
}

```

So in my own words what I see here. Card class has a build in prop which wraps different components inside it. 