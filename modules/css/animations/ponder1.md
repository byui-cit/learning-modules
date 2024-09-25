---
title: CSS Animations - Ponder activities.
description: Practice using CSS Animations and Transitions
date: 2022-09-23

layout: layouts/post.njk
---

## Preparation

It is recommended to review [CSS Animations - Introduction](../prepare1) before you start. You will also need your editor open with some code provided below.

### html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CSS Animation Practice</title>
    <link rel="stylesheet" href="anim.css" />
  </head>
  <body>
    <header><h1>Animation Practice</h1></header>
    <main class="content">
      <div class="red"></div>
      <div class="yellow"></div>
      <button class="green">Toggle</button>
      <div class="blue"></div>
    </main>
  </body>
</html>
```

### CSS

```css
* {
  box-sizing: border-box;
}

.content {
  width: 80%;
  height: 500px;
  border: 1px solid;
}

.red {
  width: 100px;
  height: 100px;
  background-color: red;
}

.yellow {
  width: 100px;
  height: 100px;
  background-color: gold;
  border-radius: 0 0 50% 50%;
}

.green {
  width: 100px;
  height: 40px;
  background-color: green;
  border: 0;
}
.blue {
  width: 100px;
  height: 100px;
  background-color: blue;
}
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

We will start with CSS Transitions. A transition is a change that happens over time. So in order to transition something, it must undergo a change of some sort. We will take advantage of the `:hover` pseudo-class to trigger our first changes.

1. Add a rule to the CSS file that will change the color of the red square when it is hovered.
2. Add a line to the rule that will change the color of red to something else as well.
3. Hover over the red box to make sure it changes.
4. Add a transition to the red box to make the hover changes happen over 1 second.

<details>
<summary>Solution 1</summary>

```css
.red {
  width: 100px;
  height: 100px;
  background-color: red;
  transition: all 1s;
}
.red:hover {
  border-radius: 50%;
  background-color: bisque;
}
```

</details>

## Activity 2

Transitions allow us to take fairly simple changes and make them happen over time instead of instantly. If we need more complex animation we can use keyframes. In this next activity we will make the yellow shape rock back and forth.

1. Create a new set of keyframes.
    ```css
    @keyframes rock {
    }
    ```
2. Add a keyframe at 25% of the way through the animation causing a rotation of 90 degrees.
3. Add another keyframe at 50% rotating back to 0 degrees
4. Add a third keyframe at 75% rotating -90 degrees.
5. Apply the `rock` keyframes using the `animation` property to the yellow shape.
6. Note that the animation will only play once when the page loads. To make it repeat forever you can add `infinite` to the end of the animation property.

<details>
<summary>Solution 2</summary>

```css
.yellow {
  width: 100px;
  height: 100px;
  background-color: gold;
  border-radius: 0 0 50% 50%;
  animation: rock 2s infinite;
}

@keyframes rock {
  25% {
    transform: rotate(90deg);
  }
  50% {
    transform: rotate(0deg);
  }
  75% {
    transform: rotate(-90deg);
  }
}
```

</details>

## Activity 3

The next exercise will simulate the hiding and showing of a menu. We will have the blue shape fade into visibility when the green shape is hovered.

1. Hide the blue shape by setting the `height` to 0 and the `opacity` also to 0
2. Write a CSS rule that will set `height: 100px` and `opacity:1` on the blue shape *when the green shape is hovered*
   >How can we do this?
   >
   >We can take advantage of the [sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Next-sibling_combinator): `+`
3. Add a transition to the blue shape so that the changes happen over time instead of instantly.

<details>
<summary>Solution 3</summary>

```css
.green {
  width: 100px;
  height: 40px;
  background-color: green;
  border: 0;
}
.blue {
  width: 100px;
  height: 100px;
  background-color: blue;
  height: 0;
  opacity: 0;
  transition: all 0.5s;
}
.green:hover ~ .blue {
  height: 100px;
  opacity: 1;
}
```

</details>

## Activity 4

The way we caused the blue shape in activity 3, by hovering on green, is not great. What if someone visits our page on a mobile device? Pretty hard to hover on a phone. It would be much better if the blue shape showed up when the green shape was clicked instead.

1. Add a `script` element to the bottom of the `body` in your HTML
2. Add an event listener to the green shape (button). When the button is clicked the blue shape should be shown. When the button is clicked again it should be hidden.

>Hint:
>
>Remember the rule we added in part 3 with the crazy selector: `.green:hover ~ .blue`. That rule is what causes the blue shape to be shown. If we change that selector to be a simple class, we can use Javascript to add and remove that class to the blue element.
>
>Also, remember that we can use the `classList` property (that all elements have) to add, remove or toggle classes on an element.

<details>
<summary>Solution 4</summary>

### CSS

```css
.green {
  width: 100px;
  height: 40px;
  background-color: green;
  border: 0;
}
.blue {
  width: 100px;
  height: 100px;
  background-color: blue;
  height: 0;
  opacity: 0;
  transition: all 0.5s;
}
.show {
  height: 100px;
  opacity: 1;
}
```

### Javascript

```javascript
// get the green button
const greenButton = document.querySelector('.green');
// get the blue shape
const blueShape = document.querySelector('.blue');
// add an event listener to the green button
greenButton.addEventListener('click', () => {
  // toggle the show class on the blue shape
  blueShape.classList.toggle('show');
  });
```

</details>
