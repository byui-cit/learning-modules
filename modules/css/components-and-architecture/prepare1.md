---
title: CSS @import - introduction
description: As your codebase and teams grow, it becomes more and more important to apply some sort of organization to your CSS. @import is one way this can be done.
date: 2021-10-15

layout: layouts/post.njk
---

<ol class="bigSteps>

1. ## Review BEM

   One issue we run into very early on with components is that CSS has global scope. What this means is that all CSS is visible EVERYWHERE! For something like a component that is designed to be reusable this can cause problems. You might include the component into the HTML and CSS and find out that you had the same class names in the component that you had in the existing CSS and something breaks.

   CSS naming conventions are designed to help with the global nature of CSS. One popular convention is called BEM - Block, Element, Modifier. Take a few minutes to familiarize yourself with [BEM's basic conventions](http://getbem.com/introduction/).
