---
title: JS Sorting and Filtering - Ponder activities.
description: Practice sorting and filtering
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

<!-- Make sure you read through the Prepare section for this topic. -->

You will need your editor open with some HTML and the code:

### HTML

```html
<!-- sorting.html -->
<html>
  <head>
    <title>Sorting Activities</title>
    <script src="sorting.js"></script>
  </head>
  <body></body>
</html>
```

### Javascript

```javascript
// sorting.js
const hikes = [
  {
    name: "Bechler Falls",
    stub: "bechler_falls",
    imgSrc:
      "https://wdd131.netlify.app/examples/hikes/images/bechler-falls.jpg",
    imgAlt: "Image of Bechler Falls",
    distance: "3 miles",
    tags: ["Easy", "Yellowstone", "Waterfall"],
    description:
      "Beautiful short hike in Yellowstone along the Bechler river to Bechler Falls",
    directions:
      "Take Highway 20 north to Ashton. Turn right into the town and continue through. Follow that road for a few miles then turn left again onto the Cave Falls road.Drive to the end of the Cave Falls road. There is a parking area at the trailhead.",
    trailhead: [44.14457, -110.99781]
  },
  {
    name: "Teton Canyon",
    stub: "teton_canyon",
    imgSrc: "https://wdd131.netlify.app/examples/hikes/images/teton-canyon.jpg",
    imgAlt: "Image of Bechler Falls",
    distance: "3 miles",
    tags: ["Easy", "Tetons"],
    description: "Beautiful short (or long) hike through Teton Canyon.",
    directions:
      "Take Highway 33 East to Driggs. Turn left onto Teton Canyon Road. Follow that road for a few miles then turn right onto Staline Raod for a short distance, then left onto Alta Road. Veer right after Alta back onto Teton Canyon Road. There is a parking area at the trailhead.",
    trailhead: [43.75567, -110.91521]
  },
  {
    name: "Denanda Falls",
    stub: "denanda_falls",
    imgSrc:
      "https://wdd131.netlify.app/examples/hikes/images/denanda-falls.jpg",
    imgAlt: "Image of Bechler Falls",
    distance: "7 miles",
    tags: ["Moderate", "Yellowstone", "Waterfall"],
    description: "Beautiful hike through Bechler meadows to Denanda Falls",
    directions:
      "Take Highway 20 north to Ashton. Turn right into the town and continue through. Follow that road for a few miles then turn left again onto the Cave Falls road. Drive to until you see the sign for Bechler Meadows on the left. Turn there. There is a parking area at the trailhead.",
    trailhead: [44.14974, -111.04564]
  },
  {
    name: "Coffee Pot Rapids",
    stub: "coffee_pot",
    imgSrc: "https://wdd131.netlify.app/examples/hikes/images/coffee-pot.jpg",
    imgAlt: "Image of Bechler Falls",
    distance: "2.2 miles",
    tags: ["Easy"],
    description:
      "Beautiful hike along the Henry's Fork of the Snake River to a set of rapids.",
    directions:
      "Take Highway 20 north to Island Park. Continue almost to Mack's in. From Highway 20, turn west on Flatrock Road for 1 mile then turn off on Coffee Pot Road and travel one-half mile to the campground entrance road. There is a parking lot right outside the campground.",
    trailhead: [44.49035, -111.36619]
  },
  {
    name: "Menan Butte",
    stub: "menan_butte",
    imgSrc: "https://wdd131.netlify.app/examples/hikes/images/menan-butte.jpg",
    imgAlt: "Image of Menan Butte",
    distance: "3.4 miles",
    tags: ["Moderate", "View"],
    description:
      "A steep climb to one of the largest volcanic tuff cones in the world. 3.4 miles is the full loop around the crater, can be shortened.",
    directions:
      "Take Highway 33 West out of Rexburg for about 8 miles. Turn left onto E Butte Road, the right onto Twin Butte road after about a mile. Follow that road for about 3 miles. You will see the parking lot/trailhead on the left.",
    trailhead: [43.78555, -111.98996]
  }
];
 const simpleList = ["oranges", "grapes", "lemons", "apples", "Bananas", "watermelons", "coconuts", "broccoli", "mango"];


```

These activities will be most effective if you *try* them first before you look at the solution. And after you do look at the solution, **do not** copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1: Sorting a list of strings



1. Declare a new variable called `simpleSort`. Set it equal to `simpleList.sort()`. Log out the results...any surprises?

    >This illustrates the simplest type of sort: strings descending. Notice the 'B' got sorted before anything else. The sort is case sensitive.
    >
    > To do anything more complex we need to provide a `compareFunction`. MDN gives the following definition for that function:
    >
    >```javascript
    >compareFunction(a, b)
    > return value         sort order
    >    > 0	             sort a after b, e.g. [b, a]
    >    < 0	             sort a before b, e.g. [a, b]
    >    === 0             keep original order of a and b
    >```

2. So another way to sort our list descending would be to provide the following compare function:

    ```javascript
    function compareFunction(a,b) {
      if (a < b) {
        return -1;
      } else if (a > b) {
        return 1;
      }
     // a must be equal to b
     return 0;
    }
    const anotherSort = simpleList.sort(compareFn)
    ```

3. If we wanted to sort our list the opposite direction what would you change?

>It is important to understand that `sort()` sorts the list *in place*. That means that we are changing the original array each time we re-sort it!

<details>
<summary>Solution 1</summary>

```javascript
    function compareFn(a,b) {
      if (a > b) {
        return -1;
      } else if (a < b) {
        return 1;
      }
     // a must be equal to b
     return 0;
    }
    const anotherSort = simpleList.sort(compareFn)
```

</details>

## Activity 2: Filtering a list of strings

Instead of sorting, sometimes we need to reduce a list by some criteria. Unlike `sort()`, there is no simple version of `filter()`. We always have to provide a callback function that returns a "truthy" value if we want to keep an item in the array, or a "falsy" value if we want to get rid of it. `filter()` returns a new array and does not change the original, unlike `sort`.

1. We want to be able to search our list. Begin by writing a function called `searchList` that will take a list and a query string. We need to check to see if the query string can be found inside of each string in the list.
2. *Inside* of the `searchList` function, declare another function called `stringContains`. It should expect a string and a query string. It should return true if the query string is inside of the string, false otherwise.  [String.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) will be very helpful here.
3. As you test your `searchList` function, try using "b" as the query string. What do you get?
4. Fix your callback function so that character case does not matter.


<details>
<summary>Solution 2</summary>

```javascript
  function searchList(list, query) {
    function searchCallback(string) {
      return string.toLowerCase().includes(query.toLowerCase());
    }
    return list.filter(searchCallback);
  }
  console.log(searchList(simpleList, "b"));
  console.log(searchList(simpleList, "an"));
```

</details>

## Activity 3: Sorting and Filtering a list of objects.

You have been given a list of hikes in no particular order. We can use them to learn to sort and filter lists of objects.

1. Start with the `searchList` function from the last activity. Call it passing in the `hikes` list and use "al" as the query.
2. Make the following changes: instead of a string we will pass an object into the `searchCallback`. Start by getting the search "by name" working again.
3. After you can search by the hike name, modify it again to search for the query in the name **or** description.
4. Finally add `tags` into the search so that if the query string shows up in a tag the hike should be included. Since `tags` is an array we cannot simply use `includes` like we did before. We must check each element of that array to see if it includes our query. Check out [Array.find()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find) to help you do this.
5. Sort the filtered list by length. Try passing in "al" as the search query. How do the results look? Why are they in the order that they are? How could you fix this?

<details>
<summary>Solution 3</summary>

```javascript
  function searchList(list, q) {
    function searchCallback(item) {
      return (
        item.name.toLowerCase().includes(q.toLowerCase()) ||
        item.description.toLowerCase().includes(q.toLowerCase()) ||
        item.tags.find((tag) => tag.toLowerCase().includes(q.toLowerCase()))
      );
    }
    const filtered = list.filter(searchCallback);

    const sorted = filtered.sort((a, b) => a.distance > b.distance);
    return sorted;
  }
  console.log(searchList(hikes, "yellowstone"));
  console.log(searchList(hikes, "moderate"));
  console.log(searchList(hikes, "al"));
```

</details>
