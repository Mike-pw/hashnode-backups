## HTML Essentials

**HyperText Markup Language** organizes the structure of content, and along with **CSS** and **JavaScript**, it is one of the main building blocks of the web. HTML deals with **meaning** and **content** rather than styling or functionality, though it plays an important role in both.

HTML is made up of **elements** which tell the browser additional information about the content using a system of opening and closing **tags**. While content is often text based, HTML also allows for the usage of links, scripts, images, audio, video and more.

### HTML Boilerplate
When you open up a new `.html` file in  [Visual Studio Code](https://code.visualstudio.com/) , you can generate **HTML boilerplate** by typing a single exclamation mark and pressing enter/return.

This template contains the basic structure that an HTML document should follow. It is a good practice to include all of these tags, and only a single html, head, title, and body tag.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

The `<!DOCTYPE>` declaration tells the browser what version of HTML to expect. The `<head>` tag contains the page title and metadata, and is also the place to link to styles, and certain scripts. The `<body>` tag is where the content of the HTML document lives, and where JavaScript files are commonly added.

### Block vs. Inline
HTML elements generally fall into two categories, inline or block. Block level elements will automatically fill to 100% the width of their parent container, while inline elements are only as wide as the content they hold.

HTML has a general use container for block and inline content. Block level content can be wrapped in a `<div>` tag, while inline content can be wrapped in a `<span>` tag.

These generic containers don't provide the browser any information about the content's purpose, and therefore you should *always use more appropriate semantic elements*, if at all possible.

### Headings and Paragraphs
Text content in HTML is often either a **heading** or a **paragraph**. Headings are titles and subtitles that are numbered in order of importance. There are six level's of headings which are shown by the tags; `<h1>` to `<h6>`.

`<h1>` is the most important heading, and provides the main title or subject of the page. Only one `<h1>` tag should be used per page, and tags should exist in order, i.e. `<h2>` comes after `<h1>` and so on.

Paragraph's are block level elements which are wrapped in a `<p>` tag. The main purpose of a `<p>` tag is to denote a block of text content.

### Semantics and Accessibility
One of the best ways to ensure your site is accessible to the largest population of users, is to ensure you *always use the correct element* for the content you are displaying. HTML includes many descriptive semantic tags such as:

- `<main>`
- `<section>`
- `<header>`
- `<footer>`
- `<nav>`
- `<article>`
- `<aside>`
- `<figure>`

Someone might be viewing your website with a screen reader, or navigating with only a keyboard. It is important that you keep this in mind when creating any HTML document for use by the general public.

### Attributes, IDs and Classes
HTML elements often have settings or options that can be changed by their attributes. Attributes generally follow the `name="value"` format. Some attributes are required for certain elements, and others are optional.

Two commonly used attributes are `id` and `class`. These are names you can assign to elements in order to reference them later, often using CSS or JavaScript. Id's are unique and *should not be re-used* on different elements, while classes may be used on multiple elements.

### Images, Links, and Lists
It's hard to find a website that doesn't have a single image on it. Images can be added to HTML by using the `<img>` tag. The image element requires a `src` attribute that points to the images location. It is highly recommended for accessibility to always include a descriptive `alt` attribute.

The H in HTML (and http) stands for **Hypertext**, text that contains links. Hypertext was in usage before the invention of the World Wide Web, and has long been a core part of the internet. Text can be wrapped in an `<a>` or "Anchor" tag which accepts an `href` attribute as a location.

Lists in HTML can either be ordered `<ol>` or unordered `<ul>`. The main difference is the default styling for `<ol>` uses numbers , while `<ul>` uses bullets. Use `<ol>` when the order is important, for example a sequence of events such as a cooking recipe. Both types of lists are made up of `<li>` elements.

### Forms and Input
An important part of HTML is the ability to accept a user's input. The `<form>` element tells a browser this part of the page is for gathering user input. Forms often contain;

- `<input>`
- `<label>`
- `<button>`
- `<textarea>`
- `<select>`

`<input>` elements are differentiated by their type attribute. Some commonly used input types are text, checkbox, button, password, radio, and submit. Associated `<labels>` are used to add captions to input elements.