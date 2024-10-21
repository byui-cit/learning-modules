---
title: UX - Ponder activities.
description: Practice improving User Experience
date: 2024-10-08

layout: layouts/post.njk
---

## Preparation

It is recommended to review [UX - Introduction](../prepare1) before you start. You will also need your editor open with some html and the code from the Prepare activity:

### html

```html
<!-- badUx.html -->
<!DOCTYPE html>
<html>
  <head>
    <title>A Terrible Website</title>
    <link rel="stylesheet" href="badUx.css" />
  </head>
  <body>
    <h1>Welcome to our Terrible Website!</h1>
    <p>
      We're really bad at web design. We're really bad at web design. We're
      really bad at web design. We're really bad at web design. We're really bad
      at web design. We're really bad at web design.We're really bad at web
      design.We're really bad at web design.We're really bad at web design.
      We're really bad at web design. We're really bad at web design. We're
      really bad at web design. We're really bad at web design.
    </p>
    <img src="https://byui-cit.github.io/learning-modules/img/ux-bad.jpg" />
    <div>
      <ul>
        <li>This</li>
        <li>is</li>
        <li>a</li>
        <li>very</li>
        <li>long</li>
        <li>list</li>
        <li>that</li>
        <li>never</li>
        <li>ends</li>
        <li>This</li>
        <li>is</li>
        <li>a</li>
        <li>very</li>
        <li>long</li>
        <li>list</li>
        <li>that</li>
        <li>never</li>
        <li>ends</li>
      </ul>
    </div>
    <form>
      <input type="text" placeholder="Enter your name" />
      <button type="submit">Submit</button>
    </form>
  </body>
</html>

```

### css

```css
/* badUx.css */
body {
  font-family: Comic Sans MS, sans-serif;
  background-color: hotpink;
  width: 1000px;
  color: #aaa;
}

h1 {
  color: green;
  text-align: center;
  font-size: 80px;
}

img {
  width: 100%;
  height: auto;
}

form {
  background-color: white;
}
ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 10px;
  font-size: 20px;
}

form {
  margin-top: 20px;
}


```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

The code you were provided intentionally showcases several common user experience mistakes to illustrate how they can negatively impact a website's usability. A well-designed website should be visually appealing, easy to navigate, and accessible to all users.

Make a list of all the issues you see with the page. After making your list review the list below.

<details>
<summary>UX Issues</summary>

- Overly large heading: The large h1 element can be overwhelming and difficult to read.
- Poor color choices: The combination of hot pink background and green text creates a visually jarring experience.
- Overall text readability: Text size is small, measure (length of a line of text) is too long, contrast is poor, and Comic Sans. 🤦‍♂️
- Lack of Whitespace: Text is pressed up close to the hard edges of the color changes.
- Not responsive: The layout only works for one screen width
- Blurred image: The blurred image provides no value and can be distracting. It is also very large leading to the user potentially missing the content below the image
- Image size: the image is overly large causing loading to be slow.
- Long list: The excessively long list without any structure or pagination is difficult to navigate.
- No clear call to action: The form doesn't have a clear label or explanation of its purpose.
- Lack of accessibility: The website doesn't consider accessibility features like alt text for images, proper heading structure, or language settings.

</details>

## Activity 2

Fix the issues identified in activity 1. Run the Lighthouse tool on the site when you are done...try for 100%

- There is a cleaned up image that you can use: `ux-good.jpg`
- The most common way to fix the really long list would be to introduce some pagination. We can make some UI changes to indicate that there are multiple pages, but making the links work is beyond the scope of this activity.

## Activity 3

One commonly used way to assess the quality of the user experience of a site is by doing user testing and surveys. User testing generally asks people to perform tasks or scenarios. The user is watched carefully while they attempt the task, and feedback about how it went is collected. To get a taste of what this might look like, this activity will ask you to run through a couple of tasks with the [Church of Jesus Christ website](https://www.churchofjesuschrist.org/?lang=eng)

For each task record the following:

- How long it took
- Any issues you encountered
- Whether you used the site navigation or the search function
- Any observations you made about the user experience
- Any suggestions you have for improvement

1. Find out the time and location of a church service in Dijon France.
2. You have recently been called as a Primary teacher. Find resources to help you plan a lesson for Sunday.
3. Find information about what your role is in supporting your Primary children with their personal development goals.
4. Find information about the church's stance on the environment.
