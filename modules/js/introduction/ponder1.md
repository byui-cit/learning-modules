---
title: JS Introduction - Ponder activities.
description: Running Javascript
date: 2023-10-15

layout: layouts/post.njk
---

## Preparation

<!-- Make sure you read through the Prepare section for this topic. -->

These activities will be most effective if you **try** them first before you look at the solution. And after you do look at the solution...**do not** copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

1. Open up your editor. This example will use VS Code.
2. Create two new files called `running.html` and `running.js`
3. In the `running.html` file add the HTML markup you would need for a valid document. (Hint: in VS Code you can enter a '!' then press the 'tab' key)
4. In the `head` of the document add a `script` tag with the `src` pointing to the `running.js`
5. In the `running.js` file add the following code:
    ```javascript
    const apples = 5;
    const oranges = 3;
    let total = apples + oranges;
    console.log("total:", total);
    ```
    >Even if you have never seen Javascript before, as long as you have done some programming the code above should feel somewhat familiar. We start by declaring two variables and setting values to them.
    >Then we add the values in the variables together and store the total in another variable.
    >`console.log()` is a builtin Javascript browser tool for outputting (logging) values to a console. It is used mostly for debugging or error handling purposes. Here we are using it to output our total to check if the program is working correctly.
6. Open the HTML file in a browser. In VS Code it is recommended to use something like the Live Server extension to do this. You will notice that there is nothing showing in the browser window. This is expected as we had nothing in the `body` of our HTML file.
7. Open up the developer tools in the browser (Right-click anywhere in the browser window and select the "Inspect" option.) and switch to the "Console" tab. You should see something like this: `total:8`. If you do not, check to make sure that your `script` tag in the HTML file has the correct filename in it. Second make sure that you have no errors in your code in the JS file.

<details>
<summary>Solution 1</summary>

```html
<!-- running.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Running JS solution</title>
    <script src="running.js"></script>
  </head>
  <body></body>
</html>
```

```javascript
// running.js
const apples = 5;
const oranges = 3;
let total = apples + oranges;
console.log("total:", total);
```

</details>

## Activity 2

Repetition is good when learning new things, and so the next activity will have you repeat what you did before.

1. Create another HTML file and another JS file. Name them whatever you would like
    >Be aware that when naming things for use on the web you should only use letters (a-z), numbers (0-9), and the underscore (_), or dash (-). Avoid all other characters, especially the space!...they will cause you problems. It is also highly recommended that you stick to all lowercase letters. Web servers are case-sensitive.
2. Add the HTML you need for a valid document. Make sure to add a `script` element!
3. This time add a headline to your page. The headline should read something like "Javascript example 2". Below that headline add a paragraph that looks like this:
    ```html
    <p>If you have <span id="myAppleElement"></span> apples, and your friend has
      <span id="friendAppleElement"></span>. Then together you have
      <span id="totalApplesElement"></span> apples!</p>
    ```
3. Add the following code to your JS file:
    ```javascript
    const myApples = 4;
    const friendApples = 2;
    let total = myApples + friendApples;

    document.getElementById("myAppleElement").textContent = myApples;
    document.getElementById("friendAppleElement").textContent = friendApples;
    document.getElementById("totalApplesElement").textContent = total;
    ```
    >This code is similar to the code earlier, but this time we are using `document.getElementById()` to grab part of our HTML in order to modify it. For example, we should get the element with the id of `myAppleElement` and change the `textContent` of that element to be whatever is in the `myApples` variable.
    >Then we do the same for the other elements.

5. Open your HTML page in a browser. Do you see what you expected? There are no values! If you look in the console you will see and error that looks something like this: `null is not an object (evaluating 'document.getElementById("myAppleElement").textContent = myApples')`. This illustrates a common Javascript error. The problem is that when the browser downloads the HTML file, it starts to parse through the file to be able to build and render the page.
Well, as soon as it hits the `script` element it stops what it is doing, downloads the JS file, and runs any code it finds. The problem is that the `script` element was *before* the `body` element, and so the elements we are trying to grab in our Javascript don't exist yet!
We need to tell the browser to wait to run the Javascript it finds until *after* it finishes building the whole page. The easiest way to do that is to add `defer` to our `script` element.
    ```html
    <script src="myjsfile.js" defer></script>
    ```
Get used to using that `defer` command. We will do it with every `script` we load.

<details>
<summary>Solution 2</summary>

```html
<!-- HTML file -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Running JS solution</title>
    <script src="running.js" defer></script>
  </head>
  <body>
    <p>
      If you have <span id="myAppleElement"></span> apples, and your friend has
      <span id="friendAppleElement"></span>. Then together you have
      <span id="totalApplesElement"></span> apples!
    </p>
  </body>
</html>
```

```javascript
// Javascript file
const myApples = 4;
const friendApples = 2;
let total = myApples + friendApples;

document.getElementById("myAppleElement").textContent = myApples;
document.getElementById("friendAppleElement").textContent = friendApples;
document.getElementById("totalApplesElement").textContent = total;
}
```

</details>
