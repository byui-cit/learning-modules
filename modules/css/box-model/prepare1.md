---
title: Box Model
description: Learning how to use the box model in CSS
date: 2021-12-03

layout: layouts/post.njk
---

## Box Model

**CSS Box Model** is a box that wraps around every element. It has content, padding, border and margin.

**Content** is where text and images appear

**Padding** is the area around the content.

**Border** goes around the padding and content.

**Margin** is the area outside the border.

## Example 1

Let's copy the following code into an html file. (If you've completed other learning modules you may already have these files. You can just add to them.)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Document</title>
    <link rel="stylesheet" href="styles/styles.css">
</head>
<body>
    <header>
        <nav>
            <a href="index.html">Home</a>
            <a href="https://www.churchofjesuschrist.org">Church of Jesus Christ</a>
            <a href="https://www.churchofjesuschrist.org/temples">Temples</a>
            <a href="https://www.churchofjesuschrist.org/study/scriptures">Scriptures</a>
        </nav>
    </header>
    <main>
        <h1>Brigham Young University Idaho</h1>
        <img src="https://www.byui.edu/images/service-sites/map-banner.jpg">
        <p>BYU-Idaho is a comfortable place to learn and grow as a disciple of Jesus Christ because students, faculty, and employees share a commitment to live the gospel.</p>
    </main>
    <footer>
        <p>My Web Page 20XX &copy</p>
    </footer>
</body>
</html>
```

Let's create a CSS file. Create a folder at the same level as our HTML file and call it styles. Within that folder, let's create a styles.css file. Open that styles.css in the editor. (Again, if you already have this CSS file you can just add to it.)

In this example we will give our footer some padding.

Let's give our footer a background color and change the text in our footer to white if you don't already have it that way.

```css
footer {
    background-color: navy;
    color: white;
}
```
Notice that the paragraph in the footer doesn't have a lot of breathing room. The text is right next to the edge of the background color. Let's give the paragraph in the footer 25 pixels of padding to make that look much better.

```css
footer p {
    padding: 25px;
}
```


## Example 2

In this example we will give our h1 element some margin spacing. It already has some default margins from the browser default styling but perhaps we want to give it a bit more. Let's increase the top and bottom margin to bring it further away from the navigation and the image, but let's leave the left and right margin as zero. We can always center it later if we need to. 

```css
h1 {
    margin: 50px 0;
}
```

The first value of 50px applies to the top and bottom margins and the 0 applies to the right and left.

## Example 3

In this example we will be adding padding to the nav and the list items.

Let's give our navigation a background color of navy first if it doesn't already have a background color. And make the text white here too.

```css
nav {
    background-color: navy;
}
a {
    color: white;
}
```

Our list items (li) elements need some breating room. Because I want some space around the links themselves and more of the navy blue color showing I will want padding not only on the (a) elements but also on the nav itself. 

```css
nav {
    padding: 25px;
}
```

And also padding on the links.

```css
a {
    padding: 25px;
}
```

Now they look so much better with the extra space around them. You can add some space around your main paragraphs as well if it needs some. Depending on what other modules you've done you may already have a margin: 0 auto for your paragraph. You can just change the zero to 50px. For example: margin: 50px auto; Play around with padding and margins of different elements to get it how you like it.

You may have noticed that little bit of space all around the edge of the whole page. That is default CSS margins on the body element. If you want your header and footer to start at the very top and stretch out all the way to the left and right with no gap, you can set the body element to a margin of 0.

```css
body {
    margin: 0
}
```

## Example 4

Lastly, let's add a border to our image.

```css 
img {
    border: 2px solid navy;
}
```