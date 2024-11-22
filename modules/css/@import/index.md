---
title: CSS @import
description: As your codebase and teams grow, it becomes more and more important to apply some sort of organization to your CSS. @import is one way this can be done.
date: 2024-11-22
order: 20
tags:
  - css
  - import

layout: layouts/post.njk
---

## Description

CSS, if left to itself will tend to turn into a big unorganized mess. If you are working alone on a project this can make it hard to find things, when on a team the problems get even bigger. Most teams will track changes in their code with something like `git`. If four teammates are making changes to one CSS file trouble will ensue.

Luckily there are some easy things we can do to remedy this situation, simply put we need to enforce some level of organization to our code. Much has been written about this topic, and many many opinions exist about the best way to do this.  We however are going to keep it simple. Really what we need is a way to break our large messy CSS file into smaller pieces, where the code in each piece is related somehow.

## Where this knowledge is utilized

- WDD 231
- WDD 330
- WDD 331
- WDD 360
- CSE 340

## Prerequisites

- Understanding of [CSS](../css-intro)

<!-- ## Prepare

- [Using @import](prepare1)

## Ponder

- [Design a simple component](ponder1). A well built component should be easily re-usable, and should fit in well with the rest of the layout the component will be placed in. This requires a bit of thought as you plan out your components. -->

## Example

Let's say you are building a website that is made up of several pages. A home page, an about page, and a contact page. Our file structure might look like this:

```bash
css/
   styles.css
about.html
contact.html
index.html
```

Inside each of the HTML files we would expect to see a link: `<link rel="stylesheet" href="css/styles.css">`. All of the pages get all of the CSS, even though some of the CSS applies global styles (styles that are the same everywhere) and some CSS is for specific content sections on each page. This CSS file could easily be hundreds of lines long making it hard to find specific rules when we need to.

A simple change we can make to our CSS to organize the CSS according to some set of rules. We can then add comments to show where one section starts and another ends.  Most people agree that this is a good idea, but they start disagreeing about what the *best* set of rules is. The reality is that is doesn't really matter. What matters is that you and your teammates use the *same* set of rules.

In this case we might decide to organize our code like this:

- variables
- global styles
- header or navigation
- footer
- typography (font families, font sizes, line heights, default amounts of padding or margin around paragraphs/headlines/etc)
- page specific styles

We can create a section in our CSS file for each of these categories, with bold comments marking where each section begins and ends. This is a good start. This will make it easier to find a certain rule, but it does not address the issues of multiple people working together on the same file. Conflicts will ensue!

## @import

What we need for the next level of organization is a way to break our large single CSS file into multiple parts. Enter [@import](https://developer.mozilla.org/en-US/docs/Web/CSS/@import). This feature has been a part of CSS for many years, and it's purpose is to do exactly what we want to do: break our code down into smaller parts.  Using `@import` we might make this change to our project structure:

```bash
css/
  partials/
    footer.css
    global.css
    header.css
    typography.css
    variables.css
  about.css
  base.css
  contact.css
  home.css
about.html
contact.html
index.html
```

The contents of `base.css` would look like this:

```css
@import 'partials/variables.css'
@import 'partials/typography.css'
@import 'partials/global.css'
@import 'partials/header.css'
@import 'partials/footer.css'
```

Essentially it would contain all the CSS that should apply to **all** pages.

Then the `home.css`, `about.css`, and `contact.css` would contain the CSS that applies to only those pages. Our `link` elements will need to change as well. In `index.html` for example we would add:

```html
<link rel="stylesheet" href="css/base.css">
<link rel="stylesheet" href="css/home.css">
```

And in `about.html` we would add:

```html
<link rel="stylesheet" href="css/base.css">
<link rel="stylesheet" href="css/about.css">
```

We could even break things up further. Maybe we design our page as a collection of blocks, and make a CSS partial for each block. This approach would make our work even more reusable as often we find similar patterns used across many pages in a site.

## Disclaimer

We have solved the problems of having a large, unorganized CSS file and made our jobs as developers easier. We have introduced a new problem however with our solution. We may have made our web pages load slower!  This is a negative side effect that sometimes shows up when `@import` is used.

When the browser requests an HTML file it starts parsing through it as soon as it can. When it hits a `link` it immediately stops parsing and requests the resource and then begins working on the CSS it contains. If that resource has requests for other resources it can stall things even more. There are some things that can make this less severe. For example the fact that we only had import statements in our `base.css` file and no actual CSS will speed it up a bit, but it would still be better if we only had one CSS file. Turns out that requesting and downloading one large CSS file is usually faster than multiple small CSS files.

Because of this possible performance hit, other solutions have been created to accomplish this splitting of code that we have done. We could use a CSS preprocessor for example like [Sass](https://sass-lang.com), a tool like [postCSS](https://postcss.org), or if we are using a Javascript framework like React, Vue, Angular, or Svelte then the framework will probably allow us to add CSS in our Javascript, and the framework will gather it all up for us. We could also use a build tool like a bundler. A bundler is a piece of software used to help manage all the resources that make up a web application. A popular one right now is [Vite](https://vite.dev).

If your project is using Vite as the bundler then we can do something like the following to fix our `@import` problem.

```bash
css/
  partials/
    footer.css
    global.css
    header.css
    typography.css
    variables.css
  about.css
  base.css
  contact.css
  home.css
js/
  about.js
  index.js
  contact.js
about.html
contact.html
index.html
```

We would first add some JS files. Then in `index.js` we would do the following:

```javascript
import '../css/base.css';
import '../css/home.css';
```

In `index.html` we would *remove* the `link` element. Vite will insert it back in for us when it needs it. When we build our project, Vite will see those `import` statements and recognize that they don't look like normal ESModules imports. It will then go and grab the CSS from the files, including the @imports! Then it will add all the CSS into a new file, and create a `link` element inside the `index.html` file to the new CSS file. All of this happens automatically for us, handled by our bundler.

This allows us to take advantage of the built in feature of CSS to break up our large CSS file into small organized partials, while minimizing the potential bad side effects.
