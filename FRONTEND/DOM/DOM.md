next  up [[Node interface]]
DOM is simply an object-based model of an HTML document.

![[Pasted image 20240626124641.png]]


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
