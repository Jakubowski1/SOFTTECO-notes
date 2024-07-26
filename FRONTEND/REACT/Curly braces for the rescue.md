You can usually pass strings, paths and shit with quotes single or double. This sucks due to repetitiveness when I want to scale usage of such string/link. Use {} to pass JS.

```jsx
export default function Avatar() {
  const avatar = 'https://i.imgur.com/7vQD0fPs.jpg';
  const description = 'Gregorio Y. Zara';
  return (
    <img
      className="avatar"
      src={avatar}
      alt={description}
    />
  );
}
```

WATCH IT!!! "avatar" is a className whereas {avatar} is a JavaScript value. 

This can be done also like this 
```jsx
export default function TodoList() {
  const name = 'Gregorio Y. Zara';
  return (
    <h1>{name}'s To Do List</h1>
  );
}
```

#### Double Curlies

Cool but how to pass a whole object in JSX?

```jsx
person={{ name: "Hedy Lamarr", inventions: 5 }}
```

or 

```jsx
export default function TodoList() {
  return (
    <ul style={{
      backgroundColor: 'black',
      color: 'pink'
    }}>
      <li>Improve the videophone</li>
      <li>Prepare aeronautics lectures</li>
      <li>Work on the alcohol-fuelled engine</li>
    </ul>
  );
}
```

Now it makes sense finally. Style is an object. 

Here is an example with extracting stuff from object into JXS markup with a use of separate file. 

```js
export function getImageUrl(person) {
  return (
    'https://i.imgur.com/' +
    person.imageId +
    person.imageSize +
    '.jpg'
  );
}
```

```js
import { getImageUrl } from './utils.js'

const person = {
  name: 'Gregorio Y. Zara',
  imageId: '7vQD0fP',
  imageSize: 's',
};

export default function TodoList() {
  return (
    <>
      <img
        className="avatar"
        src={getImageUrl(person)}
        alt={person.name}
      />
    </>
  );
}

```