---
title: CSS Selectors
description: Learning new ways to Select elements in CSS
date: 2021-12-02

layout: layouts/post.njk
---

## CSS Selectors

**Selectors** are patterns used in CSS to select the elements you want to style. There are number of different ways to select elements.

## Example 1

In this example we will look at selecting a number of different elements at the same time.

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

If I wanted to apply the same style declaration to multiple elements, I could use a comma between selectors.

For example if we want to have a background color of navy and a font color of white for both our nav and our header we can use a comma between them to say that we can both selectors to have the rule applied to them.

```css
nav, footer {
    background-color: navy;
    color: white;
}
```

Notice that both the nav and footer were styled with the one rule set.

## Example 2

In this example we will look at selecting elements that are decendants of other elements.

We have two paragraphs in our HTML. But we want to target only the paragraph that is inside the footer, not the paragraph in main. We want to make it a different  font-size. If we target the p element, both paragraphs will change. We could give one of them a class or ID as well and target that, but let's use a descendant selector instead.

We can write our selector with the parent element first and then the child (or descendant next). 

```css
footer p {
    font-size: 18px;
}
```

So the descendant selector is only targeting the p that is inside footer. It could be a child p, a grandchild p, etc. as long as it's inside footer.

## Example 3

In this example we will be adding a selector for a pseudo-class. 

Pseudo-classes require some interaction by the user in order for the style to be applied. For example with the :hover pseudo-class the styles will only be applied if the user is hovering their mouse pointer over the element. 

Let's change the background and font color of our menu links when the user hovers over them.

```css
a:hover {
    background-color: white;
    color: navy;
}
```
Now when your mouse pointer rests on top (or hovers over) the links in the nav the background and text colors should change.

