[[Node interface]]
[[Important Properties]]

DOM is simply an object-based model of an HTML document.

#### HTML DOM classes

| Class                      | Purpose                               |
| -------------------------- | ------------------------------------- |
| **`HTMLElement`**          | Represents an HTML element node.      |
| **`HTMLHtmlElement`**      | Represents the `<html>` element node. |
| **`HTMLHeadElement`**      | Represents the `<head>` element node. |
| **`HTMLBodyElement`**      | Represents the `<body>` element node. |
| **`HTMLDivElement`**       | Represents a `<div>` element node.    |
| **`HTMLSpanElement`**      | Represents a `<span>` element node.   |
| **`HTMLParagraphElement`** | Represents a `<p>` element node.      |
| **`HTMLFormElement`**      | Represents a `<form>` element node.   |
| **`HTMLInputElement`**     | Represents an `<input>` element node. |
| **`HTMLAudioElement`**     | Represents an `<audio>` element node. |
| **`HTMLVideoElement`**     | Represents a `<video>` element node.  |

#### The `document` object

It's the root node in the DOM tree of every single document — everything else in the tree originates from it.

For instance, creating a new element node for an HTML document is meaningless if we don't have a document — the DOM API asks us to write `document.createElement()`.

#### The **`getElementById()`** method

This is the easiest to show on the example I think. We want to change the name "Learning the DOM" to "Hello, from JavaScript"

```html
<!DOCTYPE html>
<html>
<head>
   <meta charset="utf-8">
   <title>Working with the DOM</title>
</head>
<body>
   <h1 id="heading">Learning the DOM</h1>

   <script>
      // First, select the element.
      var h1Element = document.getElementById('heading');

      // Next, change its content.
      h1Element.innerHTML = 'Hello, from JavaScript!';
   </script>
</body>
</html>
```

#### The `innerHTML` & The `innerText`

Technically, `innerHTML` is an accessor property with a getter and setter function.

```js
// First, select the element.
var h1Element = document.getElementById('heading');

// Next, change its content.
h1Element.innerHTML = 'Hello, from JavaScript!';
```

**Text Content**: `innerText` retrieves or sets the text content of an element, including all text that is visible to the user.

```js
var element = document.getElementById('example');
element.innerText = 'New text content'; // Sets plain text

```

Differences:

| Feature             | `innerText`                               | `innerHTML`                                 |
|---------------------|-------------------------------------------|---------------------------------------------|
| **Content Type**    | Retrieves or sets the text content, excluding HTML tags | Retrieves or sets the HTML content, including HTML tags |
| **CSS Influence**   | Influenced by CSS styles, such as `display: none` | Not influenced by CSS styles |
| **Performance**     | May cause a reflow for accurate text representation | Does not cause a reflow |
| **Use Cases**       | Use when working with plain text and concerned with visible content | Use when manipulating HTML content and working with tags |
| **Example Output**  | `This is some text.`                       | `<p>This is <em>some</em> text.</p>`        |
| **Setting Content** | `element.innerText = 'New text content';`  | `element.innerHTML = '<p>New <strong>HTML</strong> content</p>';` |



