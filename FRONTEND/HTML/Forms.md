### Form controls 

A **form control** is an element that enables user interaction and data entry or selection: an `<input>`, `<select>`, `<textarea>` or `<button>`.
### Form fields

Sometimes **form field** is used to refer to form controls, in particular elements for text entry: `<input>` and `<textarea>`.

By default, form data is sent as a `GET` request, with the submitted data appended to the URL. If a user submits 'frog' in the example above, the browser makes a request to the following URL. 
```
https://example.com/animals?animal=frog
```

```html
<form> 
<label for="animal">What is your favorite animal?</label> 
<input type="text" id="animal" name="animal">
<button>Save</button>
</form>
```

This doesn't look good how about hiding this?
Instruct the form to use a `POST` request by changing the method attribute

```html
<form method="post">...</form>
```

 The data is encrypted (if you use HTTPS).
 If the data is shareable, you can use the `GET` method.

`action`

The `action` attribute defines where the `<form>` is processed.

```html
<form action="/action_page.php" method="get">  
  <input type="text" id="lname" name="lname"><br><br>  
  <input type="submit" value="Submit">  
</form>
```

### Label 

Important is that label is connected to input/textarea/checkbox and others by id. 
```html
<label for="color">What is your favorite color</label>
<input type="text" id="color" name="color">
```

### Pick from a list

```html
<label for="color">Color</label>
<select id="color" name="color">  
	<option value="orange">Orange</option> 
	<option selected value="pink">Pink</option>
</select>
```

With the `selected` attribute you can pre-select one option.

### Grouping form controls

Sometimes you need to group form controls. You can use the `<fieldset>` element to do that.
```html
<fieldset>  
<legend>What is your favorite web technology</legend>  
<label for="html">HTML</label>  
<input type="radio" name="webfeature" value="html" id="html">  
<label for="css">CSS</label>  
<input type="radio" name="webfeature" value="css" id="css">
</fieldset>
```

### Submit a form

Just use a button.

**Warning:** Every `<button>` element inside a form works as a **Submit** button by default.

### The autocomplete attribute

Just helps the browser with finding a proper autofill

```html
<main>
  <div class="wrapper">
    <form>
      <div>
        <label for="name">Name</label>
<input type="text" name="name" id="name" autocomplete="name">
      </div>
      <button>Save</button>
    </form>
  </div>
</main>
```
### Hopeless user...
#### required
A simple attribute that won't le you submit until you fill required fields.

#### type
The browser also tests if the entered data matches the format of the `type`. So validation can extend there. 

#### minlength and aria-describedby

Okey so I need 8 characters. It is good to let the user know if failed why it failed. So I connect description with input with aria-describedby.

```html
<label for="password">Password (required)</label>
<input required minlength="8" type="password" id="password"  name="password" aria-describedby="password-minlength">
<div id="password-minlength">Enter at least eight characters</div>
```

### pattern attribute

A bit more advanced validation

```html
<label for="animal">What is your favorite animal? (required)</label>
<input required pattern="[a-z]{2,20}" type="text" id="animal" name="animal">
```

### Custom validation with JS

```js
const nameInput = document.querySelector('[name="name"]');
nameInput.addEventListener('invalid', () => {    nameInput.setCustomValidity('Please enter your name.'); });
```

## Testing

- PageSpeed Insights
- Lighthouse (Performance, search optimization)
- Form troubleshooter extension

### Tags

```html
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
```