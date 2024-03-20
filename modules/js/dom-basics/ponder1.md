---
title: DOM Basics - Ponder activities.
description: Practice using the document object model (DOM)
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

First thing...the Document Object Model is *not* Javascript. But Javascript can interact with the DOM with a bunch of built in functions that are available in all browsers.

The DOM is the representation of the nodes or elements of a web page in code. The DOM is exposed through a special object to Javascript: document.

Create a new html file in your sandbox directory for this activity. Call it `dom-basics.html`. Enter the following HTML into it:

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
    <section>
      <h2>Section 1</h2>
      <p>This is a paragraph</p>
      <p id="p2">This is a paragraph with an ID</p>
    </section>
    <section>
      <h2>Section 2</h2>
      <div>
        <p>This is a paragraph in section 2</p>
        <p class="green">This is a paragraph with an class</p>
      </div>
    </section>
  </body>
</html>
```

Open the page in the browser, then open the developer tools (right-click&rarr;inspect), go to the console tab, and enter `document` in the prompt, then hit 'return'. Quickly scan through the large object returned.

## Activity 1

>For these exercises you should actually type out the commands instead of copy/pasting them.  The commands are all short, and some of what you need to see will happen as the console auto-suggests things.

1. Type `document.` (don't forget the period at the end) in the prompt area of the console (should be at the bottom of the console) in the browser developer tools. But don't hit 'enter/return'. Notice the long list of options that pops up. Those are all things we can do with the document. Review the list.
2. Since all of the elements the user sees are found in the `body` element, we are provided a shortcut to it: try typing `document.body` in the console and see what it returns.
3. Notice that we can also look at the `children` and `parentElement` of body. If we wanted we could traverse anywhere in our page by using these...it's a bit tedious though, so we have been given shortcuts: `document.getElementById` and `document.querySelector`
4. Type `document.body.innerText` then 'enter', then try `document.body.innerHTML` and 'enter'. Notice the difference.
5. Try typing this: `document.body.innerHTML = 'Hello World'` What happened?
6. Refresh your browser to get the page back.
7. Now type this: `document.getElementById('p2').innerText = 'Hello World'` That worked a bit better.
8. `querySelector` is more flexible than `getElementById`. It uses any valid CSS selectors to target elements. To get the element with id='p2' with querySelector we would need to add a '#' like this:
   `document.querySelector('#p2')`
9. You can also get elements with classes. Try `document.querySelector('.green')` The '.' tells the browser to look for a class.
10. What if we wanted figure out which section a particular paragraph belonged to? Refer to the HTML code. Notice that in the first section, since the &lt;section&gt; is the parent of the paragraphs we could do `document.querySelector('#p2').parent`, but that won't work for the second. The paragraphs in the second section are inside of an additional `div`. Since the markup is more complex, instead we could do something like this:

    ```javascript
    const greenP = document.querySelector(".green");
    const parentSection = greenP.closest("section");
    ```

    That will traverse up the DOM starting with the green P until it finds an ancestor that is a section. Very useful!

11. To get all paragraphs we could do this: `document.querySelector('p')`
12. Did you notice that there is also a `document.querySelectorAll`? Try it with 'p'

## Activity 2

We can modify the elements in the DOM as we saw above. We can also add new elements.

### Step 1

Lets add some content to the body. This will be much easier in a javascript file. Create a file called `dom-basics.js`. and enter the following:

```javascript
const newParagraph = document.createElement("p");
newParagraph.innerText = "Added with Javascript!";
document.body.appendChild(newParagraph);
```

You will also need to attach the script to our HTML. Add the following line to the `<head>` of your html file, right below the `<title>`:

```html
<script src="dom-basics.js"></script>
```

Check the page in the browser. Did the new paragraph show? Check the console. You should see an error like this: "TypeError: null is not an object (evaluating 'document.body.appendChild')"

When the browser finds a `script` element on a page, it will stop processing the HTML, download the resource, and run any Javascript it can. The problem is that `<body>` hasn't been built yet, so when we tried to access `document.body.appendChild(newParagraph);`, it could not be found. We need to tell the browser to wait to execute the code until **after** the DOM has been built. There are two ways we can do this:

1. Place the `<script>` element at the bottom of the body. This works, and has been done for years, but these days option 2 is better...
2. Add the keyword `defer` to your script...ie `<script src="dom-basics.js" defer></script>`

Add `defer` to your script, then check to make sure it worked.

### Step 2

Try adding an image. We would need to create the `img` element, then set the `src` and `alt` attributes, and finally append the image to the body. You should use the [setAttribute](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute) method to set those attributes. Try it. You can use
   `https://picsum.photos/200` for the image path.

<details><summary>Solution</summary>

```javascript
const newImage = document.createElement("img");
newImage.setAttribute("src", "https://picsum.photos/200");
newImage.setAttribute("alt", "Random image from picsum.");
document.body.appendChild(newImage);
```

</details>

### Step 3

If we have more complex HTML to add we can insert a whole string in at once:

```javascript
const newDiv = document.createElement("div");
newDiv.innerHTML = "<ul><li>One</li><li>Two</li><li>Three</li></ul>";
document.body.appendChild(newDiv);
```

### Step 4

Try it on your own.

   1. Create a new `section` element.
   2. Add an `h2` element with the content "DOM Basics"
   3. Add a paragraph `p` that says: "This was added through Javascript"
   4. Add your `section` to the `body`.

<details>
<summary>Solution</summary>

There are two common ways this could be done:

```javascript
const newSection = document.createElement("section");
const newH2 = document.createElement("h2");
newH2.innerText = "DOM Basics";
newSection.appendChild(newH2);
const newP = document.createElement("p");
newP.innerText = "This was added through Javascript";
newSection.appendChild(newP);

document.body.appendChild(newSection);
```

OR you could do it this way:

```javascript
const newSection = document.createElement("section");
newSection.innerHTML = "<h2>DOM Basics</h2><p>This was added through Javascript</p>";
document.body.appendChild(newSection);
```

</details>
