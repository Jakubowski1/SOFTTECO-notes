### This note represents tags I might not remember

```html
#### Basic HTML Structure Tags

- `<!DOCTYPE>`: Defines the document type
- `<html>`: Root element
- `<head>`: Container for metadata
- `<title>`: Title of the document
- `<meta>`: Metadata about the document
- `<link>`: Links external resources
- `<style>`: Embedded CSS
- `<script>`: Embedded JavaScript
- `<body>`: Document body

#### Content Sectioning

- `<header>`: Introductory content or navigational links
- `<nav>`: Navigation links
- `<section>`: Thematic grouping of content
- `<article>`: Independent content
- `<aside>`: Content aside from the main content
- `<footer>`: Footer for a section or page
- `<h1>` to `<h6>`: Headings
- `<main>`: Main content
- `<address>`: Contact information

#### Text Content

- `<p>`: Paragraph
- `<hr>`: Thematic break
- `<pre>`: Preformatted text
- `<blockquote>`: Quoted section
- `<ol>`: Ordered list
- `<ul>`: Unordered list
- `<li>`: List item
- `<dl>`: Description list
- `<dt>`: Description term
- `<dd>`: Description detail
- `<figure>`: Self-contained content
- `<figcaption>`: Caption for `<figure>`
- `<div>`: Generic container
- `<a>`: Anchor/link
- `<em>`: Emphasis
- `<strong>`: Strong importance
- `<small>`: Small print
- `<s>`: Strikethrough text
- `<cite>`: Citation
- `<q>`: Inline quotation
- `<dfn>`: Definition term
- `<abbr>`: Abbreviation
- `<data>`: Machine-readable data
- `<time>`: Date/time
- `<code>`: Code snippet
- `<var>`: Variable
- `<samp>`: Sample output
- `<kbd>`: User input
- `<sub>`: Subscript
- `<sup>`: Superscript
- `<i>`: Italic text
- `<b>`: Bold text
- `<u>`: Underlined text
- `<mark>`: Highlighted text
- `<bdi>`: Bi-directional isolation
- `<bdo>`: Bi-directional override
- `<span>`: Generic inline container
- `<br>`: Line break
- `<wbr>`: Word break opportunity

#### Forms

- `<form>`: Form container
- `<input>`: Input field
- `<textarea>`: Multi-line text input
- `<button>`: Clickable button
- `<select>`: Drop-down list
- `<optgroup>`: Group of options
- `<option>`: Option in a drop-down
- `<label>`: Label for form element
- `<fieldset>`: Group of related elements
- `<legend>`: Caption for `<fieldset>`
- `<datalist>`: List of predefined options
- `<output>`: Result of a calculation

#### Embedded Content

- `<img>`: Image
- `<iframe>`: Inline frame
- `<embed>`: External interactive content
- `<object>`: External resource
- `<param>`: Parameters for `<object>`
- `<video>`: Video content
- `<audio>`: Audio content
- `<source>`: Media source
- `<track>`: Text tracks for media
- `<map>`: Image map
- `<area>`: Area in an image map
- `<canvas>`: Drawable region
- `<svg>`: Scalable Vector Graphics
- `<math>`: Mathematical notation

#### Table Content

- `<table>`: Table
- `<caption>`: Table caption
- `<colgroup>`: Group of columns
- `<col>`: Column
- `<tbody>`: Table body
- `<thead>`: Table head
- `<tfoot>`: Table footer
- `<tr>`: Table row
- `<td>`: Table data cell
- `<th>`: Table header cell

#### Scripting

- `<script>`: Embedded or external JavaScript
- `<noscript>`: Fallback content for no JavaScript
- `<template>`: Client-side template
- `<slot>`: Placeholder inside Web Component
```

`<> </>` this is called Fragment and does not leave a trace in DOM tree

```jsx
import { Fragment } from 'react';  
// ...  
const listItems = people.map(person =>  
<Fragment key={person.id}>  
<h1>{person.name}</h1>  
<p>{person.bio}</p>  
</Fragment>  
);
```