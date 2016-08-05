# UNMAINTAINED

This project is no longer being maintained. It's suggested that an alternative be used instead.

# Principles of writing consistent, idiomatic HTML

The following document outlines a reasonable style guide for HTML development.
These guidelines strongly encourage the use of existing, common, sensible
patterns. They should be adapted as needed to create your own style guide.

This is a living document and new ideas are always welcome. Please
contribute.


## Table of contents

1. [General principles](#general-principles)
2. [Whitespace](#whitespace)
3. [Format](#format)
4. [Attribute order](#attribute-order)
5. [Naming](#naming)
6. [Practical example](#example)

[License](#license)


<a name="general-principles"></a>
## 1. General principles

* All code in any code-base should look like a single person typed it, no
  matter how many people contributed.
* Strictly enforce the agreed upon style.
* If in doubt when deciding upon a style, use existing, common patterns.


<a name="whitespace"></a>
## 2. Whitespace

Only one style should exist across the entire source of your code-base. Always
be consistent in your use of whitespace. Use whitespace to improve
readability.

* Never mix spaces and tabs for indentation.
* Always use soft tabs ( spaces )
* Use 4 space tabs
* `<html>`, `<head>`, and `<body>` tags should all be indented at the same level.

Tip: configure your editor to "show invisibles". This will allow you to
eliminate end of line whitespace, eliminate unintended blank line whitespace,
and avoid polluting commits.


<a name="format"></a>
## 3. Format

* Always use lowercase tag and attribute names.
* Write one discrete element per line.
* Use one additional level of indentation for each nested element.
* Use valueless boolean attributes (e.g. `checked` rather than
  `checked="checked"`).
* Always use double quotes to quote attribute values.
* Omit the `type` attributes from `link` stylesheet, `style` and `script`
  elements.
* Always include closing tags.
* Don't include a trailing slash in self-closing elements.

(Keep line-length to a sensible maximum, e.g., 80 columns.)

Example:

```html
<div class="tweet">
    <a href="path/to/somewhere">
        <img src="path/to/image.png" alt="">
    </a>
    <p>[tweet text]</p>
    <button disabled>Reply</button>
</div>
```

### Exceptions and slight deviations

Elements with 4 or more attributes must have attributes arranged across multiple
lines in an effort to improve readability and produce more useful diffs.

Example:

```html
<a class="[value]"
    data-action="[value]"
    data-id="[value]"
    href="[url]">
        <span>[text]</span>
</a>
```

Additionally, nested container elements may be allowed to be placed on the same line.

Example:

```html
<li><a href="">
    ...
</a></li>
```


<a name="attribute-order"></a>
## 4. Attribute order

HTML attributes should be listed in an order that reflects the fact that class
names are the primary interface through which CSS and JavaScript select
elements.

1. `class`
2. `id`
3. `data-*`
4. Element specific attributes ( `src`, `href`, `name`, etc )
5. Everything else

Example:

````html
<a class="[value]" id="[value]" data-name="[value]" href="[url]">[text]</a>
````


<a name="naming"></a>
## 5. Naming

Naming is hard, but very important. It's a crucial part of the process of
developing a maintainable code base, and ensuring that you have a relatively
scalable interface between your HTML and CSS/JS.

* Use [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) syntax for class and ID names.
* Avoid _systematic_ use of abbreviated class names. Don't make things
  difficult to understand.

Example with bad names:

```html
<div class="cb s-scr"></div>
```

```css
.s-scr {
  overflow: auto;
}

.cb {
  background: #000;
}
```

Example with better names:

```html
<div class="column-body is-scrollable"></div>
```

```css
.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```

Prototype only `data` attribute tags should be namespaced to `data-proto-`. Additionally, any datuUI specific `data` targets should be namespaced to the function they're used for.

Exmaple of bad data attributes:

```html
<span data-target="some-throwaway-target"></span>
<span data-target="multiSelect"></span>
```

Example of good data-attributes:

```html
<span data-proto-target="open-message"></span>
<span data-tooltip-title="Watch out!"></span>
```

You should try not to use IDs. If you need to, it should only be a case where you need a unique name. Do not use it in CSS.

<a name="example"></a>
## 6. Practical example

An example of various conventions.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Document</title>
        <link rel="stylesheet" href="main.css">
        <script src="main.js"></script>
    </head>
    <body>
        <article class="post" id="1234">
            <time class="timestamp">March 15, 2012</time>
            <a data-id="1234"
             data-analytics-category="[value]"
             data-analytics-action="[value]"
             href="[url]">[text]</a>
            <ul>
                <li>
                    <a href="[url]">[text]</a>
                    <img src="[url]" alt="[text]">
                </li>
                <li>
                    <a href="[url]">[text]</a>
                </li>
            </ul>

            <a class="link-complex" href="[url]">
                <span class="link-complex__target">[text]</span>
                [text]
            </a>

            <input value="text" readonly>
        </article>
    </body>
</html>
```


<a name="license"></a>
## License

_Principles of writing consistent, idiomatic HTML_ by Nicolas Gallagher is
licensed under the [Creative Commons Attribution 3.0 Unported
License](http://creativecommons.org/licenses/by/3.0/). This applies to all
documents and translations in this repository.

Based on a work at
[github.com/necolas/idiomatic-html](https://github.com/necolas/idiomatic-html).
