---
title: CSS - Colors
description: Using Google Font @import with CSS
date: 2021-11-18

layout: layouts/post.njk
---

## CSS: Cascading Style Sheets

**Colors** can be applied to many different HTML elements through CSS. Appling background colors and text colors are very common. To represent colors in CSS you will see different values that can be used like color names, hexidecimal codes, and rgb (red, green, blue) notation.

The following video introduces different ways apply colors to your web elements.

## CSS Fonts

<figure class="video-container">

<iframe width="560" height="315" src="https://www.youtube.com/embed/Hexcy9aYoTk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>

## Example 1

In this example we will be adding colors to our HTML using CSS. 

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
Right now, any colors on this page is from browser default CSS styles. Usually headings and paragraph text is black, background colors are white, and links are a bright blue or purple.

Let's create a CSS file. Create a folder at the same level as our HTML file and call it styles. Within that folder, let's create a styles.css file. Open that styles.css in the editor. (Again, if you already have this CSS file you can just add to it.)

Let's change the color of the text of our h1 tag.

```css
h1 {
    color: navy;
}
```

Notice that the h1 text is now a darker blue navy color instead of black. 

Let's change the nav background color to the same navy blue.

```css
nav {
    background-color: navy;
}
```

Because our links text was bright blue or purple, it's very hard to read the text now. The contrast is very low. Let's change the link colors to white. We could type the color name 'white' just like we did 'navy', but this time let's use a hexidecimal value. The hexidecimal for white is #FFFFFF

```css
a {
    color: #FFFFFF;
}
```

We could even give our whole body a background color. This time let's use rgb values.

```css
body {
    background-color: rgb(227, 240, 246);
}
```

There are many different elements that you can apply color to. We have just chosen a few. It is important to get colors that look good together. This is a great video talking about color and choosing the right ones for your project.

<figure class="video-container">

<iframe width="560" height="315" src="https://www.youtube.com/embed/_2LLXnUdUIc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>