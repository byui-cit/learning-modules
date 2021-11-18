---
title: CSS - Fonts
description: Using Google Font @import with CSS
date: 2021-11-17

layout: layouts/post.njk
---

## CSS: Cascading Style Sheets

**Fonts** let us display our text characters in a specific style. We will often want to choose our own font for the text in our web page. It's always best to keep the different styles of fonts to 2 or at the most 3 per web page. Title, or heading fonts that are larger can have a more unique looking font. But keep your paragraph text or smaller fonts with a more common, easy-to-read, type of font.

The following video introduces different ways to change your font style and a few font properties you might use..

## CSS Fonts

<figure class="video-container">

<iframe width="560" height="315" src="https://www.youtube.com/embed/e59Ll82X6Vk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>

## Example 1

In this example we will be looking at Google Fonts and how to use the @import rule you can copy from there to style your web page text.

Let's copy the following code into an html file.

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
Right now, any font styling on this page is from browser default CSS styles. 

Let's create a CSS file. Create a folder at the same level as our HTML file and call it styles. Within that folder, let's create a styles.css file. Open that styles.css in the editor. (If you've completed other learning modules you may already have these files. You can just add to them.)

Let's change the font-family property of the body. We'll use a very different style of font so you can see easily see it change.

```css
body {
    font-family: 'Brush Script MT';
}
```

Notice that all the fonts on the page changed because the child of body inherited that property value. The font Brush Script MT is not very readable for a large amount of text like a paragraph, so it's not a great choice. Let's try 'Georgia' instead. Notice, I don't have to put quotes around Georgia because there are not spaced in the font name.

```css
body {
    font-family: Georgia;
}
```

Let's add another CSS rule set for the font of just our h1 tag.

```css
h1 {
    font-family: 'Arial Black';
}
```

Now when you look at the rendered page in the browser, you will see one font style for most text is Georgia and the h1 has a different font of Arial Black.

Brush Script MT, Georgia, and Arial Black are all web-safe fonts. This means that all browsers recognize these fonts and they can be used safely as a value for the font-family at any time. 

But what if you wanted a font style that is not included in the list of web-safe fonts? You would need to either download or import the font to be available to use on your web page.

Let's look at importing fonts from a very common font library, Google Fonts, that contains over a thousand free licensed fonts. The following shows how you can choose and get an @import rule to use different styles of fonts. The video shows getting two font styles for a page.

<figure class="video-container">

<iframe width="560" height="315" src="https://www.youtube.com/embed/fK79MA4Mwc8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>

Where the video left off we can now use that copied @import rule and paste it in the very top of our CSS file.

At the top of the file let's paste our @import we copied from Google Fonts.

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto&family=Rock+Salt&display=swap');
```

Bringing in the @import rule doesn't change our fonts, we have to now select which fonts on our page to apply the fonts to. We can use the font names as the values in a font-family property throughout our CSS. Let's style the body with Roboto and our h1 with the Rock Salt font.

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto&family=Rock+Salt&display=swap');
body {
    font-family: Roboto;
}
h1 {
    font-family: 'Rock Salt';
}
```

Now take a look at your page rendered in the browser and you should see that the fonts have changed.

If for some reason Google Fonts was down or our web page was being viewed offline (no internet connection), our reference to fonts.googleapis.com would not work and our imported font styles would not work. The way we have it right now our browser would then use its default font styles. We might want to choose our own backup fonts styles and not leave it to the browser. So let's type in some backup web-safe fonts that would be available to all computers. And then a final backup of a generic font that fits our style the best.

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto&family=Rock+Salt&display=swap');
body {
    font-family: Roboto, Helvetica, sans-serif;
}
h1 {
    font-family: 'Rock Salt', 'Bradley Hand', cursive;
}
```

This is 'best practice' to have a few font backups for the font-family property. 

## Example 2

In this example we will be using Font Squirrel to download actual font files that you can use in your web project. With this example your font styles would work even if your web pages are viewed without an internet connection (offline) because you have the actual font files downloaded in your project and you don't have to rely on a Content Delivery Network font library (like Google Fonts) that is only available if you have an Internet connection. 

Using the same HTML file code available above in Example 1, make a CSS file. If you already have a CSS file or did Example 1, delete the @import rule and font-family property values. We won't need them when we download fonts in this example.

Visit <a href="https://www.fontsquirrel.com/" target='_blank'>Font Squirrel</a> and watch this video to follow along with downloading and using your fonts.

<figure class="video-container">

<iframe width="560" height="315" src="https://www.youtube.com/embed/KXvJa0dU2RQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>
