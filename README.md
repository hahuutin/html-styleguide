# HTML coding style guide

## Table of contents

+ [Indentation](#indentation)
+ [Doctype](#doctype)
+ [Be consistent in single quote, double quote](#be-consistent-in-single-quote-double-quote)
+ [Language attribute](#language-attribute)
+ [Character encoding](#character-encoding)
+ [IE compatibility mode](#ie-compatibility-mode)
+ [CSS and JavaScript includes](#css-and-javascript-includes)
+ [Self-closing](#self-closing)
+ [Optional Closing Tags](#optional-closing-tags)
+ [Semantic tags](#semantic-tags)
+ [Attribute order](#attribute-order)
+ [Boolean Attribute](#boolean-attribute)
+ [Attribute Values](#attribute-value)
+ [IDs vs. Classes](#ids-vs-classes)
+ [Paragraphs](#paragraphs)
+ [Tables](#tables)
+ [Input Label](#input-label)
+ [Reducing markup](#reducing-markup)
+ [Accessibility](#accessibility)
+ [References](#references)


### Indentation

Use soft tabs with space - they're the only way to guarantee code renders the same in any environment (Preference: 4 spaces).


### Doctype

Enforce standards mode and more consistent rendering in every browser possible with this simple doctype at the beginning of every HTML page.


### Be consistent in single quote, double quote

Be consistence when using double quote or single quote for attributes (Preference: double quote "").


### Language attribute

Specify a lang attribute on the root html element. Help speech synthesis tools to determine what pronunciations to use, translation tools to determine what rules to use.

``` html
<html lang="en-us">
    <!-- ... -->
</html>
```


### Character encoding

Quickly and easily ensure proper rendering of your content by declaring an explicit character encoding. When doing so, you may avoid using character entities in your HTML, provided their encoding matches that of the document (generally UTF-8).

```
<head>
    <meta charset="UTF-8">
</head>
```


### IE compatibility mode

Internet Explorer supports the use of a document compatibility `<meta>` tag to specify what version of IE the page should be rendered as. Unless circumstances require otherwise, it's most useful to instruct IE to use the latest supported mode with edge mode.

``` html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```


### CSS and JavaScript includes

Per HTML5 spec, typically there is no need to specify a `type` when including CSS and JavaScript files as `text/css` and `text/javascript` are their respective defaults.


### Self-closing

Don't include a trailing slash in self-closing elements like `img`, `link`, `input`, `meta`, etc

__Bad__

``` html
<input type="text" name="input" />
<img src="logo.png" alt="Logo Company" />
```

__Good__

``` html
<input type="text" name="input">
<img src="logo.png" alt="Logo Company">
```


### Optional closing tags

Don’t omit optional closing tags like </li>, </body>


### Semantic tags

HTML5 provides us with lots of semantic elements aimed to describe precisely the content. Make sure you understand the semantics of the elements you're using

__Bad__

``` html
<div id="main">
    <div class="article">
        <div class="header">
            <h1>Blog post</h1>
            <p>Published: <span>21st Feb, 2015</span></p>
        </div>
        <p>Lorem ipsum dolor sit amet</p>
    </div>
</div>
```

__Good__

``` html
<main>
    <article>
        <header>
            <h1>Blog post</h1>
            <p>Published: <time datetime="2015-02-21">21st Feb, 2015</time></p>
        </header>
        <p>Lorem ipsum dolor sit amet</p>
    </article>
</main>
```


### Attribute order

HTML attributes should come in this particular order for easier reading of code:
    1. `class`
    2. `id`, `name`
    3. `data-*`
    4. `src`, `for`, `type`, `href`, `value`
    5. `title`, `alt`
    6. `role`, `aria-*`

``` html
<a class="..." id="..." data-toggle="modal" href="#">
    Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```


### Boolean Attribute

A boolean attribute is one that needs no declared value. XHTML required you to declare a value, but HTML5 has no such requirement.

``` html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
    <option value="1" selected>1</option>
</select>
```


### Attribute Values

Use quotes to surround all attribute values in HTML, despite quotes being optional in HTML5. This maintains consistency between attribute values that contain whitespace and those that don't.

__Bad__

``` html
<form class="registration module" action=/register method=POST>
```

__Good__

``` html
<form class="registration module" action="/register" method="POST">
```


### IDs vs Classes

HTML elements can be identified by using the id and class attributes. An ID is a unique identifier for that particular element; no other element on the page should use the same ID.

This uniqueness allows <label> elements to associate themselves with a particular input and URLs to jump to a particular scroll position on a page.

Classes are not unique. The same class can be used on multiple elements within a page, and a single element can have more than one class, in a space delimited list.

``` html
<ul id="categories">
    <li class="category">Jackets</li>
    <li class="category specials">Accessories</li>
    <li class="category">Shoes</li>
</ul>
```


### Paragraphs

Avoid using <br> tags to separate paragraphs or lines of text. Use <p> instead with proper opening and closing elements.


### Tables

Tables should not be used for page layout, only use them when you need to display tabular data.

Use the `<thead>` and `<tbody>` elements to denote which row contains column headers so when a user prints the website and the table runs onto another page, browsers can display the `<thead>` on each page for easier readability. Remember to use the `scope` attribute on the `<th>`element to indicate whether the header applies to the row or column.

``` html
<table>
    <thead>
        <tr>
            <th scope="col">Name</th>
            <th scope="col">Age</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John Doe</td>
            <td>33</td>
        </tr>
    </tbody>
</table>
```


### Input Label

All input fields should be associated with a `<label>` element. The for attribute of the `<label>` element should contain the ID of the corresponding input field. This means the input field will receive focus when a user clicks the label and also enables screen readers for sight-impaired users to read out an appropriate description of the input field.

__Bad__


``` html
<label>Home Address</label>
<input type="text">
```

__Good__

``` html
<label for="home-address">Home Address</label>
<input id="home-address" type="text">

<!-- Or -->

<label>
    <span>Home address</span>
    <inputtype="text">
</label>
```


### Reducing markup

Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML.

__Bad__

``` html
<span class="avatar">
    <img src="photo.jpg" alt="image">
</span>
```

__Good__

``` html
<img class="avatar" src="photo.jpg" alt="image">
```


### Accessibility

Accessibility shouldn't be an afterthought. You don't have to be a WCAG expert to improve your website, you can start immediately by fixing the little things that make a huge difference, such as:

+ Learning to use the alt attribute properly
+ Making sure your links and buttons are marked as such (no `<div class=button>` atrocities)
+ Not relying exclusively on colors to communicate information
+ Explicitly labelling form controls

__Bad__

``` html
<h1><img src="logo.png" alt="Logo"></h1>
```

__Good__

``` html
<h1><img src="logo.png" alt="My Company, Inc."></h1>
```


### References

+ [Code Guide by @mdo](http://codeguide.co/#html)
+ [Some HTML, CSS and JS best practices](https://github.com/bendc/frontend-guidelines)
+ [Isobar Front-end Code Standards](http://isobar-idev.github.io/code-standards/)




