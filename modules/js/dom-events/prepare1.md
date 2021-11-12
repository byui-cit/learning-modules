---
title: Dom Events - Event Driven Programming
description: Browsers operate by events. Most of the time they sit waiting for something to happen. We can take advantage of this to make the things we need to happen.
date: 2021-10-15

layout: layouts/post.njk
---

## Event driven programming.

Browsers operate by events. Most of the time they sit waiting for something to happen. They notice everything that does happen, and there are a lot of possible events...but they won't do anything about it unless we tell them to.

The next section is taken directly from MDN...

<div class=callout>

The [Event Reference](https://developer.mozilla.org/en-US/docs/Web/Reference/Events) attempts to maintain a list of the standard Events used in modern web browsers.

In general, we can distinguish events of different kinds based on the object emitting the event including:

- the `window` object, such as due to resizing the browser,
- the `window.screen` object, such as due to changes in device orientation,
- the `document` object, including the loading, modification, user interaction, and unloading of the page,
- the objects in the DOM (document object model) tree including user interactions or modifications,
- the `XMLHttpRequest` objects used for network requests, and
- the media objects such as `audio` and `video`, when the media stream players change state.

Some notable events are:

- the global object [window](https://byui-cse.github.io/en-US/docs/Web/API/Window) emits an event called ['load'](<https://byui-cse.github.io/en-US/docs/Web/Reference/Events/load_(ProgressEvent)>) when the page has finished rendering, meaning that all resources have been downloaded and acted upon, so that the scripts have been run and the images displayed,
- the global object [window](https://byui-cse.github.io/en-US/docs/Web/API/Window) emits an event called ['resize'](https://byui-cse.github.io/en-US/docs/Web/Reference/Events/resize) when the height or the width of the browser window is changed by a user,
- the DOM object [document](https://byui-cse.github.io/en-US/docs/Web/API/Document) representing the HTML document emits an event called ['DOMContentLoaded'](https://byui-cse.github.io/en-US/docs/Web/Reference/Events/DOMContentLoaded) when the document has finished loading,
- the DOM node objects such as [div](https://byui-cse.github.io/en-US/docs/Web/HTML/Element/div) or [button](https://byui-cse.github.io/en-US/docs/Web/HTML/Element/button) emit an event called ['click'](https://byui-cse.github.io/en-US/docs/Web/Reference/Events/click) when the user presses the mouse button while the mouse pointer is on top of the DOM node in the HTML page.

</div>

## addEventListener

```javascript
target.addEventListener(type, listener [, options]);
```

How do we make something happen when a specific event happens? addEventListener. Let's say we had a button in our HTML. When the user clicks on that button with the mouse, we would like it to read the value of an input, and output it to another element.

<div class="callout">

### Callbacks

We have mentioned that in Javascript functions are special objects...but since they are objects we can do anything with functions that we can a normal object. This includes assigning functions to variables, and passing functions into other functions as arguments, as well as returning functions from functions.

When we pass a function into another function we call it a 'callback'. `addEventListener` is a good example. The second parameter (`listener`) that it is expecting should be a function. This function will get called when the event we are listening for happens.

</div>

### HTML

```html
<input id="inputBox" type="text" />
<button id="submitButton">Submit</button>
<p id="output"></p>
```

### Javascript

```javascript
const buttonElement = document.getElementById("submitButton");

function copyInput() {
  const inputElement = document.getElementById("inputBox");
  const outputElement = document.getElementById("output");
  outputElement.innerHTML = inputElement.value;
}
buttonElement.addEventListener("click", copyInput);
```

## The Event object

`addEventListener` will always pass an object containing information about the event that happened into your callback function. It contains a lot of very useful information. Run the code below and inspect the event that got logged out to the console.

```javascript
// modify the copyInput callback to receive the event object
function copyInput(event) {
  // take a look at the event!
  console.log(event);
  const inputElement = document.getElementById("inputBox");
  const outputElement = document.getElementById("output");
  outputElement.innerHTML = inputElement.value;
}
```

A few properties of particular interest would be `event.target`, `event.currentTarget`, and `event.type`

## Another example

We saw how to respond to a 'click' event above. What about a key event? If you refer back to the [Event Reference](https://developer.mozilla.org/en-US/docs/Web/Reference/Events) document from earlier we can find `keydown` and `keyup` events. With something like a click, we usually want to know if a specific thing has been clicked. A keyboard event however often is not specific to a particular element, so we will listen at the `document` level.

```html
<p id="log"></p>
```

```javascript
const log = document.querySelector("#log");

document.addEventListener("keydown", logKey);

function logKey(e) {
  // how do we know which key was pressed?
  console.log(e);
  // checkout e.code, e.key, and e.keyCode
  // what is the difference?
}
```

Did you note the difference between e.code and e.key? [Here](https://javascript.info/keyboard-events) is a hint.
