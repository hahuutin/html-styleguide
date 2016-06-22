## HTML coding style guide
---

### Table of contents

+ [Doctype](#doctype)
+ [Indentation](#indentation)
+ [Be consistent in single quote, double quote](#be-consistent-in-single-quote-double-quote)
+ [Self-closing](#self-closing)
+ [CSS and JavaScript includes](#css-and-javascript-includes)
+ [Attribute order](#attribute-order)
+ [Boolean Attribute](#boolean-attribute)
+ [Reducing markup](#reducing-markup)
+ [Semantic tags](#semantic-tags)
+ [References](#references)

#### Doctype

Enforce standards mode and more consistent rendering in every browser possible with this simple doctype at the beginning of every HTML page.

#### Indentation

Use soft tabs with two spaces - they're the only way to guarantee code renders the same in any environment (Preference: 4 spaces).

#### Be consistent in single quote, double quote

Be consistence when using double quote or single quote for attributes (Preference: double quote "")

#### Self-closing

Don't include a trailing slash in self-closing elements like img, link, input, meta...

**Bad**

``` html
<input type="text" name="input" />
<img src="logo.png" alt="Logo Company" />
```

**Good**

``` html
<input type="text" name="input">
<img src="logo.png" alt="Logo Company">
```

#### CSS and JavaScript includes

Per HTML5 spec, typically there is no need to specify a type when including CSS and JavaScript files as text/css and text/javascript are their respective defaults.

#### Attribute order

HTML attributes should come in this particular order for easier reading of code:
    1. class
    2. id, name
    3. data-*
    4. src, for, type, href, value
    5. title, alt
    6. role, aria-*

``` html
<a class="..." id="..." data-toggle="modal" href="#">
    Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

#### Boolean Attribute

A boolean attribute is one that needs no declared value. XHTML required you to declare a value, but HTML5 has no such requirement.

``` html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
    <option value="1" selected>1</option>
</select>
```

#### Reducing markup

Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML.

**Bad**

``` html
<span class="avatar">
    <img src="photo.jpg" alt="image">
</span>
```

**Good**

``` html
<img class="avatar" src="photo.jpg" alt="image">
```

#### Semantic tags

HTML5 provides us with lots of semantic elements aimed to describe precisely the content. Make sure you understand the semantics of the elements you're using

**Bad**

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

**Good**

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

### References
---

+ [Code Guide by @mdo](http://codeguide.co/#html)
+ [Some HTML, CSS and JS best practices](https://github.com/bendc/frontend-guidelines)
+ [Isobar Front-end Code Standards](http://isobar-idev.github.io/code-standards/)




