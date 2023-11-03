---
title: JS Introduction - Getting Started
description: Getting started with writing and running Javascript code
date: 2023-10-15

layout: layouts/post.njk
---

## History

In the early '90s Marc Andreessen the founder of Netscape Communications and part of the ex-Mosaic team, had the vision that the web needed a way to become more dynamic. Animations, interaction and other forms of small automation should be part of the web of the future. So the web needed a small scripting language that could interact with the DOM.

He asked an employee named Brendan Eich in 1995 during his time at Netscape Communications if he could create this language. He said yes, and 6 months later it was rolled out in the Netscape Navigator browser!

People often ask: Why 'Java'script? Does it have anything to do with Java? The code name was 'Mocha', Netscape internally called it LiveScript, but publically Javascript won. It turns out that Java was added to the name as a marketing ploy to get Java developers interested in it when it was first released. The language itself was a marriage of Java-like syntax, with elements from the Scheme and Self languages.

The purpose of Javascript from the beginning was to allow for dynamic web pages, and so it should come as no surprise that most Javascript is run in a browser. It is surprising how much of what we consider as part of Javascript is really web browser APIS to allow JS to interact with the browser better however.

While most JS is used in front-end development (code that runs in a browser), there is an increasing push to use it for back-end development (code that runs on a server) as well. That desire resulted in the NodeJS project which has become very popular.


## Executing Javascript in a Browser

A very common way to execute Javascript programs is in a browser. This requires an HTML file that will be requested by the browser and loaded. The HTML might have Javascript code embedded inside of it, or more commonly, it will links through a `script` tag to a separate Javascript file.

As soon as the browser sees some Javascript code it will stop and execute any of it that it can. This can sometimes lead to issues with Javascript code executing before the webpage has fully loaded.

One of the simplest Javascript programs that we can run in the browser is below:

```html
<!doctype html>
<head>
  <title>Javascript example1</title>
  <script>
    console.log("Hello World");
  </script>
</head>
<body></body>
</html>
```

If you were to save that as an HTML file and open it in the browser, you can open the developer tools (right-click anywere in the browser window and select "Inspect") then select the console tab. You should see our message there to verify that the script ran.

More commonly however we will place our Javascript in a separate file. see below:

```html
<!-- index.html -->
<!doctype html>
<head>
  <title>Javascript example1</title>
  <script src="main.js"></script>
</head>
<body></body>
</html>
```

```javascript
// main.js
console.log("Hello World");
```

Again we can open the html file in the browser. As it loads the browser will see the `script` tag and request the file found in the `src` attribute. It will then execute any code that it can.  When running Javascript this way we can think of each `.js` file linked in as a separate program.

## Example

For a more detailed example of executing Javascript programs continue to [Running Javascript](../ponder1/)
