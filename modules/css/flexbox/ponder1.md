---
title: Flexbox - Ponder activities.
description: Practice using Flexbox
date: 2024-07-09

layout: layouts/post.njk
---

## Preparation

It is recommended to review [Introduction to Flexbox](../prepare1) before you start. You will also need your editor open with some html and the code from the Prepare activity. Create two files: `flexbox.html` and `flexbox.css` then copy the following HTML into the appropriate file.

### HTML

```html
<!-- flexbox.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Flexbox Exercise</title>
    <link rel="stylesheet" href="flexbox.css" />
  </head>
  <body>
    <header>
      <h1>Flexbox Exercise</h1>
      <nav>
        <ul class="main-nav">
          <li><a href="#">Home</a></li>
          <li><a href="#">One</a></li>
          <li><a href="#">Two</a></li>
          <li><a href="#">Three</a></li>
          <li><a href="#">Four</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <section class="media-card-container">
        <h2>A Media Card Example</h2>

      </section>
      <section class="gallery-container">
        <h2>A Gallery Example</h2>
        <div class="gallery">

        </div>
      </section>

    </main>
  </body>
</html>
```

### CSS

```css
* {
  box-sizing: border-box;
}

body {
  font-size: 20px;
  max-width: 1280px;
  margin: auto;
  padding: 1em;
}

img {
  max-width: 100%;
}
```

These activities will be most effective if you **try** them first before you look at the solution. And after you do look at the solution...**do not** copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

A first use case for Flexbox is to format the links in a navbar. The HTML is already in the file for this. Note that we have a `ul` inside of a `nav`. If we want to position the `li` elements with flexbox...what should we identify as the flex parent? The `ul` or the `nav`?

Review the image below to see what we are  trying to accomplish.

![Navbar](../../../../img/flexbox-nav.webp)

1. Set the flex parent to `display: flex`;
2. Notice that already our links have moved into a horizontal line, but they are all squished together and the bullets from our list makr it hard to read.
3. Remove the bullets from the list, and set the horizontal alignment to `flex-end`
4. We need to spread the links apart now. There are several ways we could do this...but in this case we will use `flex-grow`, `flex-shrink`, and `flex-basis` to control their size. Those three properties can be conmbined into one: `flex: grow shrink basis` Try adding a rule to the `li` elements that will not allow them to grow if there is available space, will allow them to shrink, and give them a starting size of `5em` (`flex: 0 1 5em`)
5. Another way we could have spaced out our links would be to add some `gap`. Try commenting out the `flex` property we added to the flex items, and add `gap: 1em;` to the flex container. Play around and notice the differences.

<details>
<summary>Solution 1</summary>

```css
.main-nav {
  display: flex;
  list-style-type: none;
  justify-content: flex-end;
}
.main-nav > li {
  flex: 0 1 5em;
  text-align: center;
}
```

</details>

## Activity 2

Another common layout task for Flexbox is to control the format of blocks of content consisting of text and images that often need to shift based on the size of the screen. The behavior we want is for the image to be to the side of the text when there is enough room on wider screens, and the image to stack above the text on narrower screens. See below for examples. Small screen is first and the large screen is second.

![Media card small](../../../../img/flexbox-media-card-sm.webp)

![Media card large](../../../../img/flexbox-media-card-lg.webp)

1. Inside of the section `media-card__container` add a `section` with a class of `media-card`. The crad is going to be made up of an image and a title and text. Add two more `div`s to hold that content.
2. Add a class of `media-card__image` to the first div, then add an `img` element to it. You can use `` for the source.
3. Add a class of `media-card__content` to the other div. Add an `h3` and a `p`. Those can really say anything. Grab some of these instructions if you can't think of anything to add.
4. Write the styles to format for the smaller screen first. Remember to identify the flex parent or container. Then add `display: flex;` to that element. Initially we want a direction of `column`, a `gap` between the flex items, and things centered horizontally.
5. Check out our component. On small screens it actually looks just like we want it to...but as the screen gets wider the elements just get bigger and bigger. The easiest way to fix this would be to use a simple media query.
6. Add a media query for screens wider than 550px. Inside of that media query, set the `flex-direction: row;` on our flex container.
7. If you check again in the browser you will see that we are getting close. The main problem now is that the image is growing a bit larger, and the text spreading wider than we want it to according to the screenshots. Again in the media query add two rules. For the image we don't want it to grow, we want it to shrink, and we want it to start at `250px`. For the content we don't want it to grow, we want it to shrink, and we want it to start at `60ch`. (If you are wondering what a `ch` is read this article: [Relative length units](https://developer.mozilla.org/en-US/docs/Web/CSS/length#relative_length_units_based_on_font))

<details>
<summary>Solution 2</summary>

```css
.media-card {
  display: flex;
  flex-direction: column;
  gap: 1em;
  align-items: center;
}

.media-card__content > h3 {
  margin-top: 0;
}

@media screen and (min-width: 550px) {
  .media-card {
    flex-direction: row;
  }
  .media-card__image {
    flex: 0 1 250px;
  }
  .media-card__content {
    flex: 0 1 60ch;
  }
}

```

</details>

## Activity 3

Finally let's take our media card from part 2 and add lots of them. We can use flexbox to either stack them on small screens, or tile them on wider screens. Check out the screenshots below.

![Cards stacked up on a small screen](../../../../img/flexbox-gallery-sm.webp)

![Cards stacked on medium screen](../../../../img/flexbox-gallery-md.webp)

![Cards in two columns on large screen](../../../../img/flexbox-gallery-lg.webp)

1. Copy/paste your media card component 4 times into the section with the `gallery` class.
2. Turn on flexbox for that same element and check the browser. What do you see?
3. By default flexbox does not wrap. Add the property that will allow out flex items to wrap. Also add a gap to space them out a bit, and center them horizontally. What happened?
4. The cards stacked up, but when the screen gets really wide we want them to form two columns. We will need to add one more rule for this to happen. Add a rule for the gallery children that will allow them to grow, and shrink, and set them to an initial width of `460px`

<details>
<summary>Solution 3</summary>

```css
.gallery {
  display: flex;
  flex-wrap: wrap;
  gap: 1em;
  justify-content: center;
}

.gallery > * {
  flex: 1 1 460px;
}
```

</details>
