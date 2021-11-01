---
title: JS Operators - Ponder activities.
description: Practice using Operators
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic. You will also need your editor open with some html and JS.

### html

```html
<!-- operators.html -->
<html>
  <head>
    <title>Operator Activities</title>
    <script src="operators.js"></script>
  </head>
  <body></body>
</html>
```

### Javascript

```javascript
// operators.js
let shipHealth = 3;
let shipAmmo = 3;
let targetHealth = 3;

function fireShip() {
  if (shipCanFire()) {
    shipAmmo--;
    if (isHit()) {
      targetHealth--;
      console.log("hit - targetHealth:", targetHealth);
    } else {
      console.log("miss");
    }
  } else {
    reloadShip();
    console.log("reloading, shipHealth:", shipHealth);
  }
}

function encounter() {
  console.log("You see a target");
  if (!isDestroyed(targetHealth) && !isDestroyed(shipHealth)) {
    fireShip();
    if (isDestroyed(targetHealth)) {
      console.log("Target eliminated");
    }
    if (isDestroyed(shipHealth)) {
      console.log("ship destroyed");
    }
  }
}
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

Above you will find part of the code for a simple game. Several functions are missing however. Our task will be to write those.

1. Review the code and make a list of the missing functions we will need to write to get it to work.

<details>
<summary>Function List</summary>

```javascript
function isHit() {
  // should return true if a randomly generated number is greater than .5, false if it is less than .5
}

function shipCanFire() {
  // return true if the ships health is above 0 AND ammo is above 0 false otherwise
}
function isDestroyed(health) {
  // return true if health is zero or less
}
function reloadShip() {
  // reduce ship health by 1 and increase ammo by 3
}
```

  </details>

2. Write the code for the `isHit()` function. Note that `Math.random()` will generate a number between 0 and 1.
3. Write the code for the `shipCanFire()` function. It should return true if the ship's health is above 0 AND ammo is above 0, return false otherwise
4. Write the code for `isDestroyed(health)`. It should return true if health is zero or less
5. Write the `reloadShip()` function. If the ship runs out of ammo before destroying the target, it will suffer damage. This function sohuld reduce ship health by 1 and increase ammo by 3.
6. Test your program by opening the HTML file in the browser, then open the console.
7. In the console prompt (at the bottom of the console window) enter `encounter()` and press enter. Do this until either you or the target are destroyed!

<details>
<summary>Solution 1</summary>

```javascript
let shipHealth = 3;
let shipAmmo = 3;
let targetHealth = 3;

function isHit() {
  return Math.random() > 0.5;
}

function shipCanFire() {
  return shipAmmo > 0 && shipHealth > 0;
}
function isDestroyed(health) {
  return health <= 0;
}
function reloadShip() {
  shipHealth--;
  shipAmmo += 3;
}

function fireShip() {
  if (shipCanFire()) {
    shipAmmo--;
    if (isHit()) {
      targetHealth--;
      console.log("hit - targetHealth:", targetHealth);
    } else {
      console.log("miss");
    }
  } else {
    reloadShip();
    console.log("reloading, shipHealth:", shipHealth);
  }
}

function encounter() {
  console.log("You see a target");
  if (!isDestroyed(targetHealth) && !isDestroyed(shipHealth)) {
    fireShip();
    if (isDestroyed(targetHealth)) {
      console.log("Target eliminated");
    }
    if (isDestroyed(shipHealth)) {
      console.log("ship destroyed");
    }
  }
}

encounter();
```

</details>
