---
title: Media Queries - What are Media Queries?
description: Learn what a media qury is and how to use them.
date: 2023-10-15
layout: layouts/post.njk
---

## Overview

Over the last few years we have had an explosion in screen sizes for devices used to view websites. This has meant that we have had to build these sites so that they could *respond* to the screen size to reformat itself so that it was still usable. One of the important tools we have to make our pages responsive is [CSS Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries).

CSS Media Queries are used to provide alternative CSS declarations for rendering content in different viewports (screen sizes). Web designers use media queries to decide when a design or layout change/transformation is needed based upon the site content. Web developers code breakpoints based upon conditions such as a minimum viewport width to meet the intent of the design.

>"Do NOT define breakpoints based on device classes. Defining breakpoints based on specific devices, products, brand names, or operating systems that are in use today can result in a maintenance nightmare. Instead, the content itself should determine how the layout adjusts to its container."
>[How to choose breakpoints](https://web.dev/articles/responsive-web-design-basics) - Responsive Web - Google Web Fundamentals

## Viewport Meta

Sometimes when a webpage is wider than the available viewport, or size of the window in which web content can be seen, the browser will zoom out to show all the content...often at a very small size.  For a webpage that has been designed in such a way to accomodate large and small viewports, this is a bad thing.

We can control the behavior of the browser in this case to keep it from zooming in or out...by adding a viewport meta tag. A typical tag will look like the following:

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

>To learn more about options with the viewport meta you can read about the [Viewport meta tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag) on MDN.

You should begin adding this tag to the `<head>` of all your pages moving forward!

## Media Query Syntax

CSS media queries are essential to responsive web design. The @media at-rule specifies condition(s) to create a block of CSS rules that are applied if the condition(s) evaluates to true. This is extremely useful as selected elements can be repositioned, resized, hidden, exposed, etc. based upon the user's viewport size.
Here is the general syntax is setting up a CSS @media query:

```css
@media not|only mediatype and (expressions) {
  /* CSS rules go here inside the @media query's opening and closing curly brackets {} */
}
```

Here is an example CSS media query which could be embedded in a CSS file or be the entire contents of a CSS file if wanted. This example only has one CSS rule.

```css
@media screen and (min-width: 640px) {
  h1 {
    font-size: 2.5rem;
    margin: 1rem;
    color: navy;
  }
}
```

>Note that curly brackets { } are used to contain a specific media query and are also used to define CSS Rules. Be sure to keep track of your bracket scope (start and end). Using automatic VS Code Format Document features will help you recognize issues with your structure.

### Sample code explanation

1️⃣ The `@media screen and (min-width: 640px) {` is the signature line of the @media query block of CSS rules to be applied if the conditions are met. In this case the conditions are if the media type is a screen and the viewport minimum width is at least 640 pixels wide.

2️⃣ The `h1 {` is a heading 1 (`<h1>`) element selector which starts the defined CSS rule.

3️⃣-5️⃣ The @font-size: 2.5rem; margin: 1rem; color: navy; are declarations to be applied to any `<h1>` elements if the @media query conditions are met.

6️⃣ The first `}` closes the CSS rule for `<h1>` code elements.

7️⃣ The last `}` closes the media query.

>🎦 [Media Query Demonstration](https://video.byui.edu/media/t/0_oacos9ak)
