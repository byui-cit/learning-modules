---
title: JS Forms - Ponder activities.
description: Practice using Forms and Javascript
date: 2023-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic. Create a folder in your editor. Inside of that folder create four files:

1. `form-demo.html`
2. `form-demo.js`
3. `completed.html`
4. `style.css`

Copy and paste the code below into the appropriate file.

```html
<!-- form-demo.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Checkout Form</title>
    <link rel="stylesheet" href="style.css" />
    <script src="form-demo.js" defer></script>
  </head>
  <body>
    <header><h1>Checkout</h1></header>
    <main>
      <section class="errors"></section>
      <form id="checkoutForm" action="completed.html"></form>
    </main>
  </body>
</html>
```

```javascript
// form-demo.js
function validateForm(event) {
  // get a reference to the form. Because we attached a submit event listener to the form itself, we can access the form either through 'event.target', or 'this'
  const theForm = event.target;
  // the default behavior for a form submit is to try and navigate to another page where the form would be processed, if a url is not provided it will reload the current page. This sometimes is not desirable behavior. One case when we might do this is if we think there is bad data in the form.
  // To keep it from happening we can can call e.preventDefault()
  // You should always give feedback to the user about what whet wrong so they can fix it. We will store the error messages here
  const errors = [];
  // start by assuming the form is valid.
  let isValid = true;
  // add our validations here

  // if we ran into any problems above valid will be false.
  if (!isValid) {
    //stop the form from being submitted
    event.preventDefault();
    // show the errors
    showErrors(errors);
    // return false to let the browser know the form was not submitted.
    return false;
  }
}

function togglePaymentDetails(e) {
  // get a reference to the form. We can access all the named form inputs through the form element.
  const theForm = ;
  // we will also need the creditCardContainer and paypalUsernameContainer
  const creditCardContainer = ;
  const paypalContainer = ;

  // Hide all containers by adding the '.hide' class to each of them

  // Disable required for all fields...if we hide a required field the browser will throw an error when we try to submit!


  // Show the container based on the selected payment method, and add the required attribute back.

}

// helper function to display our errors.
function showErrors(errors) {
  const errorEl = document.querySelector(".errors");
  const html = errors.map((error) => `<p>${error}</p>`);
  errorEl.innerHTML = html.join("");
}
// attach a change event handler to the paymentMethod input

// attach a submit event handler to the form

```

```html
<!-- completed.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Order Complete</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h2>Thank you for your order!</h2>
  </body>
</html>

```

```css
/* style.css */
* {
  box-sizing: border-box;
}
body {
  font-family: Arial, sans-serif;
  margin: 20px;
}

main {
  max-width: 600px;
  margin: 0 auto;
}

.errors > p {
  border: 1px solid red;
  padding: 0.5em;
}
/* Style the select arrow for Safari */
select::-webkit-inner-spin-button,
select::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Style the select arrow for other browsers */
select {
  -moz-appearance: none;
  -webkit-appearance: none;
  appearance: none;
}

.hide {
  display: none; /* Initially hide the credit card input and label */
}

```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

The first thing we need to do is to build out our form in HTML. We should also take advantage of the built in HTML validation.

1. Open the starter HTML file you were provided. Review the mockup below and create the form it shows.
![example of a simple checkout form](../../../../img/form-demo-mockup.webp)
2. Make sure to have a `label` for each element as well as adding a `name` and `id` to each. Finally make each of the form inputs required.
3. Credit card numbers are always 16 digits. We can use a `pattern` to make sure the value entered it exactly 16 digits. Add `pattern="[0-9]{16}"` to the input for the creditcard number
    >The `[0-9]{16}` is a simple Regular Expression. The first part: `[0-9]` means that only the characters 0-9 are allowed. The second part: `{16}` means we should have 16 of them.
4. Initially we don't want to see the credit card number or Paypay username inputs. Use the `.hide` class to hide them.
5. Finally open up `style.css` and add the css necessary to make your form look like the mockup. You will notice that you have been given some CSS. Part of that is to handle styling of the `select` elements in the different browsers...`selects` can be stubborn.

<details>
<summary>Solution 1</summary>

```html
<form id="checkoutForm" action="completed.html">
  <label for="fullName">Full Name:</label>
  <input type="text" id="fullName" name="fullName" required />

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required />

  <label for="address">Address:</label>
  <textarea id="address" name="address" rows="4" required></textarea>

  <label for="paymentMethod">Payment Method:</label>
  <select id="paymentMethod" name="paymentMethod" required>
    <option value="">Select Payment Method</option>
    <option value="creditCard">Credit Card</option>
    <option value="paypal">PayPal</option>
  </select>

  <!-- Container for credit card details -->
  <div id="creditCardNumberContainer" class="hide">
    <label for="creditCardNumber">Credit Card Number:</label>
    <input
      type="text"
      id="creditCardNumber"
      name="creditCardNumber"
      pattern="[0-9]{16}"
      placeholder="Enter 16 digits"
      required
    />
  </div>

  <!-- Container for PayPal details -->
  <div id="paypalUsernameContainer" class="hide">
    <label for="paypalUsername">PayPal Username:</label>
    <input
      type="text"
      id="paypalUsername"
      name="paypalUsername"
      placeholder="Enter PayPal username"
      required
    />
  </div>

  <button type="submit">Place Order</button>
</form>
```

```css
/* style.css */

label {
  display: block;
  margin-bottom: 8px;
}

input,
select,
textarea {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  box-sizing: border-box;
  border: 1px solid #ccc; /* Add a border to make it visually consistent */
  border-radius: 4px;
}
button {
  background-color: #4caf50;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
```

</details>

## Activity 2

If you try submitting the form you will see that it prompts us to fill in all of the required elements before it will proceed. If you fill it all out and submit we get an error however. We currently have 2 hidden required fields. The browser considers this an error...as it should. We need to add some Javascript to first hide and show the appropriate fields, and remove the `required` attribute from the one that stays hidden.

Open the `form-demo.js` file. It contains several incomplete functions. Start with the `togglePaymentDetails` function. Follow the comments to complete it.

Here are a few tips:

1. You can add and remove classes to elements through `element.classList.add("classname")` and `element.classList.remove("classname")`
2. `required` is a bit of a funny attribute since it doesn't have a value. You can actually remove it by doing `element.required = false` OR by using `element.removeAttribute("required")`. You can add it back with either `element.required = true` OR `element.setAttribute("required", "")`
3. Remember that when working with form inputs the stuff typed into the input can be found in `element.value`

One you have finished writing the function, add a `change` event listener to the `paymentMethod` form input that will call our `togglePaymentDetails` function on change.

<details>
<summary>Solution 2</summary>

```javascript
function togglePaymentDetails(e) {
  // get a reference to the form. We can access all the named form inputs through the form element.
  const theForm = document.querySelector("#checkoutForm");
  // we will also need the creditCardContainer and paypalUsernameContainer
  const creditCardContainer = document.getElementById(
    "creditCardNumberContainer"
  );
  const paypalContainer = document.getElementById("paypalUsernameContainer");

  // Hide all containers
  creditCardContainer.classList.add("hide");
  paypalContainer.classList.add("hide");
  // Disable required for all fields...if we hide a required field the browser will throw an error when we try to submit!
  theForm.creditCardNumber.required = false;
  theForm.paypalUsername.required = false;

  // Show the container based on the selected payment method
  if (theForm.paymentMethod.value === "creditCard") {
    creditCardContainer.classList.remove("hide");
    theForm.creditCardNumber.required = true;
  } else if (theForm.paymentMethod.value === "paypal") {
    paypalContainer.classList.remove("hide");
    theForm.paypalUsername.required = true;
  }
}

// attach a change event handler to the paymentMethod input
document
  .querySelector("#paymentMethod")
  .addEventListener("change", togglePaymentDetails);

```

</details>

## Activity 3 - Stretch!

We can go quite far with the built in HTML form validation...but it has it's limits. For example we made sure that our credit card number was 16 digits...but not all 16 digit numbers are valid credit card numbers. For that we need to add another layer of validation. For this we will use the incomplete `validateForm` function.

1. Add an event listener to the form that will call `validateForm` on submit.
2. By default when a form is submitted, it looks at the `action` attribute on the form and sends the data from the form to that URL. If it does not find an action it reloads the current page. Normally the URL in the `action` would be a server somewhere that would be able to process the form. We don't have a server to work with, and so our form is just pointing to a normal HTML page, which means it won't really do anything when we submit.
3. Look carefully through the provided code in the `validateForm` function. Notice that if the `isValid` variable ever becomes `false` we will go into the if statement and do a couple of things...call `event.preventDefault()` (this stops the form from calling the action and reloading the page) and then we call a provided `showErrors` function. Finally it returns `false` to let the browser know the form did not finish it's submission.
4. Let's add a couple of validations to see how this works. First let's assume that only people named "Bob" can submit the form. Write a validation that will stop the form from being submitted if the name is not "Bob". Make sure to let the user know what went wrong.
5. Second we will "validate" the credit card number. We can't really do this without access to a credit card company...but we can still write a use case for testing. Only allow one number as valid: `1234123412341234`. Anything else should throw an error. Again add a message. Test your validations.

<details>
<summary>Solution 3</summary>

```javascript
function validateForm(event) {
  // get a reference to the form. Because we attached a submit event listener to the form itself, we can access the form either through 'event.target', or 'this'
  const theForm = event.target;
  // the default behavior for a form submit is to try and navigate to another page where the form would be processed, if a url is not provided it will reload the current page. This sometimes is not desirable behavior. One case when we might do this is if we think there is bad data in the form.
  // To keep it from happening we can can call e.preventDefault()
  // You should always give feedback to the user about what whet wrong so they can fix it. We will store the error messages here
  const errors = [];
  // start by assuming the form is valid.
  let isValid = true;
  // add our validations here
  if (theForm.paymentMethod.value === "creditCard") {
    // normally we would need contact the credit card company to verify the number...we are only going to allow one number as valid to keep things simple.
    if (theForm.creditCardNumber.value !== "1234123412341234") {
      isValid = false;
      errors.push("Invalid Credit Card Number");
    }
  }
  if (theForm.fullName.value !== "Bob") {
    isValid = false;
    errors.push("Your name is not Bob");
  }
  // if we ran into any problems above valid will be false.
  if (!isValid) {
    //stop the form from being submitted
    event.preventDefault();
    // show the errors
    showErrors(errors);
    // return false to let the browser know the form was not submitted.
    return false;
  }
}
// attach a submit event handler to the form
document
  .querySelector("#checkoutForm")
  .addEventListener("submit", validateForm);
```

</details>
