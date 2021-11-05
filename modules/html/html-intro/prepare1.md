---
title: HTML - Understanding HTML
description: Getting started HTML
date: 2021-11-01

layout: layouts/post.njk
---

## HTML: Hypertext Markup Language

**HTML** stands for hypertext markup language. Hypertext refers to the way we can place hypertext links in our document that allows our users to move from one page to another. Markup is a set of symbols or codes for displaying content on the Internet. HTML tells web browsers the structure of a web page's words and images. This markup language allows you to code around the content, the browser will use this code to display or render our pages correctly. The code or tags we use are the markup.

The following video introduces more HTML elements and attributes you use with elements.

## HTML Elements and Attributes

<figure class="video-container">

<iframe width="560" height="315" src="https://www.youtube.com/embed/GpZmiD8WlFo" title=
"YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>

## Example

Let's copy the following code into an html file.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>BYUI</title>
  </head>
  <body>
    <header></header>
    <main></main>
    <footer></footer>
  </body>
</html>
```

This is the framework of a beginning HTML page. Notice inside the body tag we have 3 general areas. The body tag has 3 children tags of header, main and footer. Let's start with the header. Let's type in a common element you'd find in the header a nav element.

```html
<header>
  <nav></nav>
</header>
```

The nav element will contain menu links. These links are created with an a tag.

```html
<nav>
  <a>Church of Jesus Christ</a>
  <a>Temples</a>
  <a>Scriptures</a>
</nav>
```

If we look at our rendered page now in a browser window, the content of the a tag shows but they are not links. When we click on the content text, nothing happens. We have to add an attribute to the opening a tag that shows where to take the user when they click on the content. Add attributes to each opening a tag as follows.

```html
<a href="https://www.churchofjesuschrist.org">Church of Jesus Christ</a>
<a href="https://www.churchofjesuschrist.org/temples">Temples</a>
<a href="https://www.churchofjesuschrist.org/study/scriptures">Scriptures</a>
```

Now when you look at the rendered page in the browser you can click the text content and it will take you to the right place because we added the href or hypertext reference value for each a link.

## Note

Note that the links here are not going to internal website pages but to external website pages. Your navigation link would usuallly be going to other pages in your website not to outside web pages like this.

## Example Continued

Let's move on to the main part of our web page with a header level one title for our page using an h1 tag and a paragraph beneath the title using a p tag. Then let's add an img tag. There are two attributes needed for an image. First where is the image located or what is the source (src) and, second what is some alternative text (alt) that can be used if the image can't be seen.

```html
<main>
  <h1>My Favorite University</h1>
  <p>BYUI is a great place to learn and grow.</p>
  <img
    src="https://www.byui.edu/images/service-sites/map-banner.jpg"
    alt="BYUI Campus"
  />
</main>
```

## Note

Again, we are using an attribute value for the src propertly that is taking us to an image that is located externally to our site. Normally you would want to use an internal path to your own images folder where your website images are located. Something like src="images/map-banner.jpg" This would assume that you have a folder called images with a jpg image called 'map-banner.jpg' located in that images folder of your site. But for ease of this prepare practice we will use the external image.

## Example Continued

Lastly, let's add a p tag to our footer with a bit of information for the bottom of our page.

```html
<footer>
  <p>My First Web Page 20XX &copy</p>
</footer>
```

The &copy will create an HTML symbol copyright entity for us. See <a href="https://www.w3schools.com/html/html_symbols.asp">HTML Symbols</a>for more examples.

There we have our first simple HTML page. If we had multiple page that we created for the same website, the header and footer section that would remain the same for every page our our website and the main section would change from page to page of our website.

We've practiced with some of the elements that make up the structure of a simple web page. And we see that some elements need attributes within their opening tags to display and function properly.
