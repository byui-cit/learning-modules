---
title: CSS - Understanding CSS
description: Getting started with CSS
date: 2021-11-01

layout: layouts/post.njk
---

## CSS: Cascading Style Sheets

**CSS** stands for cascading style sheets. It is a style sheet language used to layout and style web pages.

The following video introduces more CSS and the rule-sets you can make and how precedence and inheritance works.

## CSS Syntax, Precedence, and Inheritance

<figure class="video-container">

<iframe width="560" height="315" src="https://www.youtube.com/embed/TdhDY2cx66s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>

## Example

Let's copy the following code into an html file.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document</title>
  </head>
  <body>
    <header>
      <nav>
        <a href="https://www.churchofjesuschrist.org">Church of Jesus Christ</a>
        <a href="https://www.churchofjesuschrist.org/temples">Temples</a>
        <a href="https://www.churchofjesuschrist.org/study/scriptures"
          >Scriptures</a
        >
      </nav>
    </header>
    <main>
      <h1>Brigham Young University Idaho</h1>
      <img src="https://www.byui.edu/images/service-sites/map-banner.jpg" />
      <p>
        BYU-Idaho is a comfortable place to learn and grow as a disciple of
        Jesus Christ because students, faculty, and employees share a commitment
        to live the gospel.
      </p>
    </main>
    <footer>
      <p>My First Web Page 20XX &copy</p>
    </footer>
  </body>
</html>
```

Right now, any styling on this page is from browser default CSS styles. For example the h1 element is styled as bigger and bolder. If we want to add our own styles to this page we will use an external CSS file that will link up to the HTML page. We use the link tag inside the HTML to tell which CSS file will be used with that HTML page.

Inside the head element, let's add the link tag to the HTML page

```html
<head>
  <<<<<<< HEAD
  <title>My Web Page</title>
  <link rel="stylesheet" href="styles.css" />
  =======
  <title>My Web Page</title>
  <link rel="stylesheet" href="styles/styles.css" />
  >>>>>>> 7d48584df6d086fc5a508176ac20c856fae7570a
</head>
```

The link tag has two attributes. The rel specifies the relationship between the current document and the linked document. The href or hypertext reference shows where the document is located. It is inside a styles folder and is called styles.css.

Let's create the folder called styles with a CSS file called styles.css inside that folder. The styles folder will be at the same level as our HTML file. Open the styles.css and let's add our first rule-set to the CSS file:

```css
body {
  text-align: center;
}
```

The selector is body and inside the curly braces are all the declarations, or property value pairs, that will affect that selector.
If we look at our rendered HTML page now in a browser window, all the body and all the children of the body inherited the alignment of center.

Let's add another CSS declarations.

```css
nav {
  background-color: steelblue;
  padding: 10px;
}
```

Now when you look at the rendered page in the browser You will see the background of the nav changed colors and a little bit of space, or padding, is added all around the links in the nav. But the links are still really close together and they are hard to read because there is not a good contrast between the text color and the background color. Let's fix that by adding another declaration.

```css
a {
  color: white;
  margin: 40px;
}
```

The color refers to the font color and the margin gives some space between the a elements.

Let's add the rest of the CSS declarations.

```css
h1 {
  color: steelblue;
}
img {
  width: 80%;
  border: 4px solid steelblue;
}
p {
  padding: 10px;
}
footer {
  background-color: steelblue;
  color: white;
}
```

Don't worry if you don't understand some of the units of measurement like px or the % sign. We will learn more about units of measurement in a different learning module. What we see from this activity is the proper syntax for creating rule-sets in our CSS file and how a little CSS styling can make a different in how our page looks.
