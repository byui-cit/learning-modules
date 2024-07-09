---
title: Flexbox - Introduction
description: Getting started with using CSS Flexbox
date: 2024-07-09

layout: layouts/post.njk
---

## Flexbox and CSS Grid

Flexbox and CSS Grid are fairly recent additions to CSS that allow for much better control over our layouts. They are intended to work together and have different roles. They do however have several simularities. They both for example has the concept of a container or parent, and an item or child. When you enable flexbox or grid for a container it makes all of the immediate children of that container flex or grid items. Only the direct children can be manipulated!

CSS Grid gives us great control over two dimensions. We can exactly place items in both column and row. Flexbox is more one dimensional. We have good control over either the row placement or the column placement...but not both.

That does not mean that Flexbox is not powerful.  You can accomplish a lot with it. It is important to understand it's limitations however.

## Flexbox fundamentals

Core to flexbox is the concept of the primary and secondary axis.  This is controlled by the `flex-direction` property. By default it is set to `row`. It can also be set to `column`, `row-reverse`, or `column-reverse`. We are manipulating the flow of the items with the `flex-direction`.  Essentially by default block elements flow vertically top to bottom which is why paragraphs for example move vertically down the page. With flexbox we can switch that flow.  We can also control how items wrap as well as grow or shrink to fill the available space.

One other powerful feature that Flexbox brought is great alignment tools for vertical as well as horizontal alignment.  It shares some of the property names with CSS Grid. `justify-content`, `align-content`, `justify-items`, and `align-items`.  Visit [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) to learn more about all the properties we can use.

One important difference with Flexbox and Grid however, is that with Flexbox `justify` and `align` don't always behave how we would expect. We expect them to always do the same thing...horizontal or vertical. Instead they are tied to the primary and secondary axes. `justify` always aligns along the primary axis, and `align` always does the other. So if you set `flex-direction:row` then `justify` will align horizontally, but if you do `flex-direction:column` then it will adjust the vertical alignment.

## Example

Move onto the [practice activity](../ponder1) for some examples of how to use Flexbox.
