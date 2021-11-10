---
title: ES Modules - Ponder activities.
description: Practice using ES Modules
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic. You will also need your editor open with some html and JS code. This is the finished code from the Ponder section of the [Objects module](../../objects). Create two files: `modules.html` and `modules.js`, then copy paste the code below into them.

### html

```html
<!-- modules.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Courses and sections</title>
    <script src="courses.js" defer></script>
  </head>
  <body>
    <h1 id="courseName"></h1>
    <h2 id="courseCode"></h2>
    <label for="sectionNumber">Section Number</label>
    <input id="sectionNumber" />
    <button id="enrollStudent">Enroll Student</button>
    <button id="dropStudent">Drop Student</button>

    <table>
      <thead>
        <tr>
          <th>Section#</th>
          <th>Room#</th>
          <th>#Enrolled</th>
          <th>Days</th>
          <th>Instructor</th>
        </tr>
      </thead>
      <tbody id="sections"></tbody>
    </table>
  </body>
</html>
```

### Javascript

```javascript
//modules.js
const aCourse = {
  code: "CSE121b",
  name: "Javascript Language",
  sections: [
    {
      sectionNum: 1,
      roomNum: "STC 353",
      enrolled: 26,
      days: "TTh",
      instructor: "Bro T",
    },
    {
      sectionNum: 2,
      roomNum: "STC 347",
      enrolled: 25,
      days: "TTh",
      instructor: "Sis A",
    },
  ],
  changeEnrollment: function (sectionNum, add = true) {
    // find the right section...Array.findIndex will work here
    const sectionIndex = this.sections.findIndex(
      (section) => section.sectionNum == sectionNum
    );
    if (sectionIndex >= 0) {
      if (add) {
        this.sections[sectionIndex].enrolled++;
      } else {
        this.sections[sectionIndex].enrolled--;
      }
      renderSections(this.sections);
    }
  },
};

function setCourseInfo(course) {
  const courseName = document.querySelector("#courseName");
  const coursecode = document.querySelector("#courseCode");
  courseName.textContent = course.name;
  coursecode.textContent = course.code;
}

function renderSections(sections) {
  const html = sections.map(
    (section) => `<tr>
    <td>${section.sectionNum}</td>
    <td>${section.roomNum}</td>
    <td>${section.enrolled}</td>
    <td>${section.days}</td>
    <td>${section.instructor}</td></tr>`
  );
  document.querySelector("#sections").innerHTML = html.join("");
}

document.querySelector("#enrollStudent").addEventListener("click", function () {
  const sectionNum = document.querySelector("#sectionNumber").value;
  aCourse.changeEnrollment(sectionNum);
});
document.querySelector("#dropStudent").addEventListener("click", function () {
  const sectionNum = document.querySelector("#sectionNumber").value;
  aCourse.changeEnrollment(sectionNum, false);
});

setCourseInfo(aCourse);
renderSections(aCourse.sections);
```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

The object created with the javascript above contains most of the functionality we would need to create and manage a course. This seems like a good candidate for encapsulating into a module.

1. Create a new file to hold our module. Name it `Course.js`
2. Copy the `aCourse` object and the `setCourseInfo` and `renderSections` functions into the new file. Leave the addEventListeners and everything below them.
3. Make the `aCourse` object the `default export`
4. Import `aCourse` into the `modules.js` file
5. Make sure to change the line in your HTML that looks like this:

   ```html
   <script src="courses.js" defer></script>
   ```

   to this:

   ```html
   <script src="courses.js" type="module"></script>
   ```

   This will allow the browser to load our module. It will give you an error if you forget this step!

6. Remove the lines at the bottom of `modules.js` that look like this:
   ```javascript
   setCourseInfo(aCourse);
   renderSections(aCourse.sections);
   ```
   Since we moved those functions we will get an error if we don't. We will add that back in later.
7. Use the LiveServer extension to view your page. You should notice that we do not see the course name, or the sections. But if you put 1 in the section number input and click enroll or drop student the sections will show up and the number of enrolled should change.

<details>
<summary>Solution 1</summary>

```javascript
// Course.js
const aCourse = {
  code: "CSE121b",
  name: "Javascript Language",
  sections: [
    {
      sectionNum: 1,
      roomNum: "STC 353",
      enrolled: 26,
      days: "TTh",
      instructor: "Bro T",
    },
    {
      sectionNum: 2,
      roomNum: "STC 347",
      enrolled: 25,
      days: "TTh",
      instructor: "Sis A",
    },
  ],

  changeEnrollment: function (sectionNum, add = true) {
    // find the right section...Array.findIndex will work here
    const sectionIndex = this.sections.findIndex(
      (section) => section.sectionNum == sectionNum
    );
    if (sectionIndex >= 0) {
      if (add) {
        this.sections[sectionIndex].enrolled++;
      } else {
        this.sections[sectionIndex].enrolled--;
      }
      renderSections(this.sections);
    }
  },
};

function setCourseInfo(course) {
  const courseName = document.querySelector("#courseName");
  const coursecode = document.querySelector("#courseCode");
  courseName.textContent = course.name;
  coursecode.textContent = course.code;
}

function renderSections(sections) {
  const html = sections.map(
    (section) => `<tr>
      <td>${section.sectionNum}</td>
      <td>${section.roomNum}</td>
      <td>${section.enrolled}</td>
      <td>${section.days}</td>
      <td>${section.instructor}</td></tr>`
  );
  document.querySelector("#sections").innerHTML = html.join("");
}
export default aCourse;
```

```javascript
// modules.js
import aCourse from "./Course.js";

document.querySelector("#enrollStudent").addEventListener("click", function () {
  const sectionNum = document.querySelector("#sectionNumber").value;
  aCourse.changeEnrollment(sectionNum);
});
document.querySelector("#dropStudent").addEventListener("click", function () {
  const sectionNum = document.querySelector("#sectionNumber").value;
  aCourse.changeEnrollment(sectionNum, false);
});
```

</details>

## Activity 2

We need to fix the rest of our app. When the page loads we should see the course name, and the list of all sections that are part of the course. Because those are not part of the `aCourse` object, and we did not export them, they are not visible outside of the `Course.js` module. There are two ways we could fix this.

1. We could add the functions to our object. This would make them visible.
2. We could add another method to the object to run them both as needed.

Which way we go becomes somewhat of a philisophical debate. Should those functions belong to the course?

The activity had you leave them out of the Object because they felt different than the other things we were doing. The other methods we added to the object were responsible for changing parts of the Object. `setCourseInfo` and `renderSections` were not changing anything, but just displaying the information in the Object. That felt different enough that the functions were placed outside.

You might argue though that they are related to the Object and should just be packaged up with it...and you might be right. That would make those functions public however...and someone using our module could call them anytime they wanted. Sometimes that can cause problems. It is good to expose only what is necessary and no more when creating modules.

To complete this activity we will go with option 2.

1. Add a new method to `aCourse` called `init()`
2. In the `init` method call both `setCourseInfo` and `renderSections` (Remember `this`!)
3. In `modules.js` call `aCourse.init()`

<details>
<summary>Solution 2</summary>

```javascript
// Course.js
const aCourse = {
  code: "CSE121b",
  name: "Javascript Language",
  sections: [
    {
      sectionNum: 1,
      roomNum: "STC 353",
      enrolled: 26,
      days: "TTh",
      instructor: "Bro T",
    },
    {
      sectionNum: 2,
      roomNum: "STC 347",
      enrolled: 25,
      days: "TTh",
      instructor: "Sis A",
    },
  ],
  init() {
    setCourseInfo(this);
    renderSections(this.sections);
  },
  changeEnrollment: function (sectionNum, add = true) {
    // find the right section...Array.findIndex will work here
    const sectionIndex = this.sections.findIndex(
      (section) => section.sectionNum == sectionNum
    );
    if (sectionIndex >= 0) {
      if (add) {
        this.sections[sectionIndex].enrolled++;
      } else {
        this.sections[sectionIndex].enrolled--;
      }
      renderSections(this.sections);
    }
  },
};

function setCourseInfo(course) {
  const courseName = document.querySelector("#courseName");
  const coursecode = document.querySelector("#courseCode");
  courseName.textContent = course.name;
  coursecode.textContent = course.code;
}

function renderSections(sections) {
  const html = sections.map(
    (section) => `<tr>
      <td>${section.sectionNum}</td>
      <td>${section.roomNum}</td>
      <td>${section.enrolled}</td>
      <td>${section.days}</td>
      <td>${section.instructor}</td></tr>`
  );
  document.querySelector("#sections").innerHTML = html.join("");
}
export default aCourse;
```

```javascript
// modules.js
import aCourse from "./Course.js";

aCourse.init();
document.querySelector("#enrollStudent").addEventListener("click", function () {
  const sectionNum = document.querySelector("#sectionNumber").value;
  aCourse.changeEnrollment(sectionNum);
});
document.querySelector("#dropStudent").addEventListener("click", function () {
  const sectionNum = document.querySelector("#sectionNumber").value;
  aCourse.changeEnrollment(sectionNum, false);
});
```

</details>
