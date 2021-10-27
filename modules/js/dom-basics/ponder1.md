---
title: DOM Basics - Ponder activities.
description: Practice using the document object model (DOM)
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

First thing...the Document Object Model is NOT Javascript. But Javascript can interact with the DOM with a bunch of built in functions that are available in all browsers.

The DOM is the representation of the nodes or elements of a web page in code. The DOM is exposed through a special object to Javascript: document.

Create a new html file in your sandbox directory for this activity. Call it `dom-basics.html`. Enter the following HTML into it (remember if you are in VS Code you can type '!' then hit the tab key to get some HTML boilerplate as a starting point):

### html

```html
<!-- dom-basics.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Week 2</title>
  </head>
  <body>
    <h1>Week 2</h1>
    <p>This is a paragraph</p>
    <p id="p2">This is a paragraph with an ID</p>
    <script src="dom-basics.js"></script>
  </body>
</html>
```

Open the page in the browser, then open the developer tools (right-click->inspect), goto the console tab, and enter `document` in the prompt, then hit 'return'.

## Activity 1

1. Type `document.` (don't forget the . at the end) in the prompt area of the console (should be at the bottom of the console) in the browser developer tools. But don't hit 'enter/return'. Notice the long list of options that pops up. Those are all things we can do with the document. Review the list.
2. Since all of the elements the users sees live in the `body` element, we are provided a shortcut to it: `document.body`.
3. Notice that we can also look at the `children` and `parentElement` of body. We could if we wanted traverse anywhere in our page by using these...it's a bit tedious though, so we have been given shortcuts: `document.getElementById` and `document.querySelector`
4. Type `document.body.innerText` then 'enter', then try `document.body.innerHTML` and 'enter'. Notice the difference.
5. Try doing this: `document.body.innerHTML = 'Hello World'` What happened?
6. Refresh your browser to get the page back.
7. Now try this: `document.getElementById('p2').innerText = 'Hello World'` That worked a bit better.
8. `querySelector` is more flexible that `getElementById`. It uses valid CSS selectors. To get the element with id='p2' with quertSelector we would need to add a '#' like this:
   `document.querySelector('#p2')`
9. to get all parapgraphs we could do this: `document.querySelector('p')`
10. Did you notice that there is also a document.querySelectorAll? Try it with 'p'

## Activity 2

We can modify the elements in the DOM as we saw above. We can also add new elements.

1. Lets add some content to the body. This will be much easier in a javascript file. Create a file called dom-basics.js and enter the following:

```javascript
const newParagraph = document.createElement("p");
newParagraph.innerText = "Added with Javascript!";
document.body.appendChild(newParagraph);
```

2. Try adding an image. We would need to create the `img` element, then set the `src` and `alt` attributes, and finally append the image to the body. You should use
   `element.setAttribute('src', 'path/to/image')` to set those attributes. Try it. You can use
   `https://placeimg.com/200/200/animals` for the image path.

<details><summary>Solution</summary>

```javascript
const newImage = document.createElement("img");
newImage.setAttribute("src", "https://placeimg.com/200/200/animals");
newImage.setAttribute("alt", "Description of image");
document.body.appendChild(newImage);
```

</details>

3. If we have more complex HTML to add we can insert a whole string in at once:

```javascript
const newDiv = document.createElement("div");
newDiv.innerHTML = "<ul><li>One</li><li>Two</li><li>Three</li></ul>";
document.body.appendChild(newDiv);
```

4. Try it on your own.

   1. Create a new `section` element.
   2. Add an `h2` element with the content "CSE 121b"
   3. Add a paragraph `p` that says: "Welcome to Javascript Language"
   4. Add your `section` to the `body`.

<details>
<summary>Solution</summary>

There are two common ways this could be done:

```javascript
const newSection = document.createElement("section");
const newH2 = document.createElement("h2");
newH2.innerText = "CSE 121b";
newSection.appendChild(newH2);
const newP = document.createElement("p");
newH2.innerText = "Welcome to Javascript Language";
newSection.appendChild(newP);

document.body.appendChild(newSection);
```

OR you could do it this way:

```javascript
const newSection = document.createElement("section");
newSection.innerHTML = "<h2>CSE 121b</h2><p>Welcome to Javascript Language</p>";
document.body.appendChild(newSection);
```

</details>
