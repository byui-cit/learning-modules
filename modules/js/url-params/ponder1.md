---
title: URL Search Parameters - Practice.
description: Practice using URL search parameters
date: 2024-10-04

layout: layouts/post.njk
---

## Preparation

It is recommended to review [URL Search Params - Introduction](../prepare1) before you start. You will also need your editor open with some code. You will need to create four files for this one: `index.html`, `product.html`, `params.js`, and `params.css`. Note that the HTML below goes into `product.html`

### html

```html
<!-- product.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Product details</title>
    <script src="params.js" defer></script>
    <link rel="stylesheet" href="params.css" />
  </head>
  <body>
    <header>
      <a href="index.html" class="logo">
        <div class="logoImg"></div>
        <h1>SomeStore</h1>
      </a>
    </header>
    <main>
      <h2>Product Details</h2>
    </main>
  </body>
</html>

```

### Javascript

```javascript
// params.js
const products = [
  { id: 1, name: "Product 1", price: 3, image: "https://placehold.co/300" },
  { id: 2, name: "Product 2", price: 5, image: "https://placehold.co/300" },
  { id: 3, name: "Product 3", price: 1, image: "https://placehold.co/300" }
];
```

### CSS

```css
body {
  font-size: 18px;
  font-family: Arial, sans-serif;
}
img {
  max-width: 100%;
}
.logoImg {
  border-radius: 50% 25%;
  width: 50px;
  height: 50px;
  background-color: coral;
}
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

We need to first build out an `index.html` page. It will be very simple. It should have a header (see the product page for this), a heading saying "Featured Products", and then a list of product links.

1. Add the markup to build out the index page: head, body, header (see product.html), main, and "Featured Products" headline.
2. Link the CSS file to index.html
3. For the product links we need to send the id of the product as part of the link. This looks like a perfect job for Url Search parameters. Build out 3 links. The links should take you to the `product.html` page, and send a `productId` parameter with the id cooresponding to each product. See the `params.js` file for the product names and ids.
4. Test to make sure that your links open the `product.html` page, and that you can see the query string on the end of the URL

<details>
<summary>Solution 1</summary>

```html
<header>
      <a href="index.html" class="logo">
        <div class="logoImg"></div>
        <h1>SomeStore</h1>
      </a>
</header>
<main>
  <section>
    <h2>Featured Products</h2>
    <ul>
      <li><a href="product.html?productId=1">Product 1</a></li>
      <li><a href="product.html?productId=2">Product 2</a></li>
      <li><a href="product.html?productId=3">Product 3</a></li>
    </ul>
  </section>
</main>
```

</details>

## Activity 2

Next we need to figure out which product was requested on the `product.html` page. Then we will look up that product and output it's details.

1. In the `params.js` file start by adding `console.log(window.location)` Review the output. Note especially the `search` property.
2. Create a function called `getParams(param)` It should take a string (the parameter key we are interested in), and return a string (the value for the specified param). Using [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) complete the function.
3. Create another function called `productTemplate(product)` that takes a product object as an argument, and returns the HTML markup to output that product. You should include the name, image, and price in the HTML.
4. Create another function called `getProductDetails`. This function should attempt to get the productId from the Url search parameter, then if it found an id it should look in the `products` array for that product. If it finds a match then it should create the markup to display the product, and insert it into the `main` element.
5. Test your work to make sure the correct product shows.

<details>
<summary>Solution 2</summary>

```javascript
const products = [
  { id: 1, name: "Product 1", price: 3, image: "https://placehold.co/300" },
  { id: 2, name: "Product 2", price: 5, image: "https://placehold.co/300" },
  { id: 3, name: "Product 3", price: 1, image: "https://placehold.co/300" }
];

function getParam(param) {
  const paramString = window.location.search;
  const params = new URLSearchParams(paramString);
  return params.get(param);
}

function productTemplate(product) {
  return `<section class="product">
  <img src="${product.image}" alt="${product.name}">
  <div class="product__details">
    <h2>${product.name}</h2>
    <p>Price: $${product.price}</p>
    </div>
    </section>`;
}

function getProductDetails() {
  const id = getParam("productId");
  if (id) {
    const product = products.find((p) => p.id == id);
    if (product) {
      output("main", productTemplate(product));
    }
  }
}

function output(selector, markup) {
  const element = document.querySelector(selector);
  // using insertAdjacentHTML allows us to insert the new markup at the bottom of main...without losing the title that was already in there.
  element.insertAdjacentHTML("beforeEnd", markup);
}

getProductDetails();
```

</details>

## Activity 3 - Stretch

Take the opportunity to practice your CSS by adding some styling to the product page. Match the images below. Don't be afraid to adjust your HTML structure for a product as needed. It can often make the styling easier.

<figure>

![Figure 1: Mobile View Screenshot](../../../../img/params-sm.webp)

<figcaption>Mobile View</figcaption>
</figure>
<hr>
<figure>

![Figure 2: Wide View Screenshot](../../../../img/params-wide.webp)

<figcaption>Wide View</figcaption>
</figure>

<details>
<summary>Solution 3</summary>

```css
body {
  font-size: 18px;
  font-family: Arial, sans-serif;
}

img {
  max-width: 100%;
}
header {
  border-bottom: 1px solid coral;
}
.logo {
  display: flex;
  align-items: center;
  color: black;
}

.logoImg {
  border-radius: 50% 25%;
  width: 50px;
  height: 50px;
  background-color: coral;
}

.product {
  border: 1px solid;
  max-width: 300px;
  padding: 1em;
  margin: 1em auto;
}

@media screen and (min-width: 600px) {
  .product {
    max-width: 600px;
    display: flex;
  }
  .product__details {
    margin: 1em;
  }
}

```

</details>
