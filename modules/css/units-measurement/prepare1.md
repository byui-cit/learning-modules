---
title: Units of Measurement
description: Learning how to use values and units of measurement in CSS
date: 2021-12-01

layout: layouts/post.njk
---

## Absolute vs. Relative

**Absolute** units of measurements are fixed and appear as exactly that size. A common absolute unit of measurement is px or pixels.

**Relative** units of measurement specify a size relative to another property size. Relative units are better for responsive pages, or in other words, the elements size relative to what device the user is rendering the page on. Common relative units of measurement include em and % (percentages).

## Example 1

In this example we will be adding values and units of measurement to your CSS. 

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

Right now the image of BYUI is rendering on our page in whatever size it was when it was created. If our page is narrow, like on a phone the image will get cut off and only the left edge will show. If our monitor is very large there might be a lot of space after the image to the right. If we give the image a pixel size like width: 800px it will always be 800px wide again, regardless of the width of the device.

Let's make it more responsive by giving it a percentage unit of measurement. Always put units of measurement in CSS not in HTML.

```css
img {
    width: 80%;
}
```

Notice as you resize the page the image always remains at 80% of the page. Play around with other percentages to see how it looks.

You can also give the paragraph 80% width as well.

```css
p {
    width: 80%;
}
```

## Example 2

Let's use the em unit of measurement to change the font-size of our navigation links. Since we haven't changed the font-size of our default body font-size we know that 16px is our starting point. If we want our font-size to be one and a half times as big (16 + 8 = 24px), we can use 1.5em.

```css
a {
    font-size: 1.5em;
}
```

Now the text size of our links are bigger and easier to read.

Centering elements, and giving them breathing room with margins and paddings also uses units of measurement, but those will be covered in other learning modules ('Block vs. Inline' and 'Box Model').
