---
title: Class and ID Selectors
description: Learning how to use Class and ID attributes in HTML and select them in CSS
date: 2021-12-01

layout: layouts/post.njk
---

## Classes

**Class** attributes are used to give a class name to an HTML element. Many different elements can use the same class.

**ID** attributes are used to give a unique id to an HTML element. You cannot have more than one element with the same ID value in one HTML page.

## Example 1

In this example we will be adding classes and IDs to our HTML and selecting them using CSS. 

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

Let's change the font size and line-height of the paragraph in the main section of our page, but we don't want it to effect the footer paragraph. So we can give our paragraph a class or ID attribute to differentiate it from all other paragraphs on the page.

```html
<p class='main-para'>BYU-Idaho is a comfortable place to learn and grow as a disciple of Jesus Christ because students, faculty, and employees share a commitment to live the gospel.</p>
```

Then in CSS we can target just that class by using a dot selector. Classes are specified with a dot or period before the class name in CSS.


```css
.main-para {
    font-size: 1.5em;
    line-height: 1.5em;
}
```

Notice that just the paragraph in the main section is bigger and has more line-height. The paragraph in the footer has not changed because only the paragraph in the main section has that class name.


## Example 2

Perhaps we want to show our users which page is the active page in the navigation, or in other words, which is the current page that they are on. We will only ever have on active page at a time. Let's use an ID this time for our home page link.

```html
<nav>
    <a id="active" href="http://index.html">Home</a>
    <a href="https://www.churchofjesuschrist.org">Church of Jesus Christ</a>
    <a href="https://www.churchofjesuschrist.org/temples">Temples</a>
    <a href="https://www.churchofjesuschrist.org/study/scriptures">Scriptures</a>
</nav>
```

Now we can target that ID in CSS using a hashtag preceding the id value. Remember we can't use the id of 'active' anywhere else on the page, but we can use another id with a different value if we needed to. 

```css
#active {
    background-color: white;
    color: navy;
}
```

Now our home page link has a different back-ground color and text color to show what page they are on. 



