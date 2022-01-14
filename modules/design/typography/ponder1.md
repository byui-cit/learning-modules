---
title: Typography on the Web - Ponder activities.
description: Implement Web typography principles.
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic. You will also need your editor open with some html and the code:

### html

[starter HTML](https://byui-cit.github.io/advcss/modules/examples/syllabus/index.html) (right click - save as)

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

Open the file you downloaded above in your editor, then create a .css file (or .scss if you have studied that). Copy the provided CSS above into that file and add a `link` to the html to attach the CSS.

when you open the HTML you will see that it is the text for a Syllabus. It currently has a lot of important information. Some hierarchy has been provided with the semantics of the HTML, but more should be provided to make the page more effective at delivering it's message.

https://fonts.google.com/specimen/Archivo#standard-styles
https://fonts.googleapis.com/css2?family=Archivo:ital,wdth,wght@1,62..125,100..900&display=swap

1. Start with the font. We will use the [Recursive font](https://fonts.google.com/specimen/Recursive?vfaxis=slnt#standard-styles) from Google fonts. Select the font and then take the URL that google provides to look at the `@font-face` declarations it provides. You will see something like this:

```css
@font-face {
  font-family: "Recursive";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/recursive/v26/8vJN7wMr0mhh-RQChyHEH06TlXhq_gukbYrFMk1QuAIcyEwG_X-dpEfaE5YaERmK-CImKsvxvU-MXGX2fSqasNfUvz2xbXfn1uEQadCCk317tQtBCYCK6v8.woff)
    format("woff");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
    U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
    U+FEFF, U+FFFD;
}
```

This is a variable font and we would like to use those extra features, but the code Google automatically generates is missing the required elements to enable us to use it as a variable font.

Poking around on the Google Fonts site produces this article on [variable fonts](https://web.dev/variable-fonts/). Reading through it we find this: "To use all the available axes, or ranges of values, you will have to [manually compose](https://developers.google.com/fonts/docs/css2) the URL to the Google Fonts API. " Finally if we follow that link it takes us to a place where we can figure out how to use a variable font from Google. Read through the article and see if you can compose the URL needed to use the Recursive font as a variable font.

<details>
<summary>Solution</summary>

```css
@import url("https://fonts.googleapis.com/css2?family=Recursive:wght@-300..800&display=swap");
```

</details>

2. Check out [recursive.design](https://www.recursive.design/).

If we read the **About** section on google Fonts for Recursive it tells us that we can do far more with the font than is exposed on Google. Visiting that site shows a nice interactive playground where we can change all the axis of the font. If you click on the 'Get Recursive' button you will also find a nice wizard that generates the same URL we made manually in the last step...only now we can include all the features of the font. Change all the values to "Range" Notice though how the font size gets larger with each feature we enable. This is important to note!

Normally you would only want to include the features of the font that you will use. We want to explore what we can do with this font and so will enable all the features at the cost of a larger file size.

Get a new url that allows us access to all of the font's features

<details>
<summary>Solution</summary>

```css
@import url("https://fonts.googleapis.com/css2?family=Recursive:slnt,wght,CASL,CRSV,MONO@-15..0,300..800,0..1,0..1,0..1&display=swap");
```

</details>

3. In order to modify the font on a web page we will need some CSS. Add the `@import` above to your stylesheet. It should be at the top. Then add the following:

```css
:root {
  /* set variation axis values */
  --mono: "MONO" 0; /* Monospace: Sans (natural-width) or Mono (fixed-width) */
  --casl: "CASL" 0; /* Casual: Linear to Casual */
  --wght: "wght" 600; /* Weight: Light to ExtraBlack; usually set with `font-weight` */
  --slnt: "slnt" 0; /* Slant: 0 to -15 degrees, auto cursive at -14 */
  --CRSV: "CRSV" 0.5; /* Cursive: always roman (0), auto substitution (.5), or always cursive (1) */
}
* {
  font-variation-settings: var(--mono), var(--casl), var(--wght), var(--slnt),
    var(--crsv);
}

body {
  font-family: Recursive, sans-serif;
}
```

Spend some time experimenting with changing the values in our custom properties.

4. It would be nice to have your headlines look different from the body copy. Apply the following settings to our headlines:

- wght 600
- CASL 1

5. The tables for grade scale and the Overall grading would look better monospaced, and slightly more bolded. Make this happen.

6. Finally lets apply one more set of font styles to the Title of the page. We want it to look like this ultimately:

![Page title](../../../../img/typography-ponder-title.png)

To get the vertical text to look right, the characters should really all be the same width. Make the font monospaced, then get rid of the casual styling and set the weight to 800.

<details>
<summary>Solution 1</summary>

```css
@import url("https://fonts.googleapis.com/css2?family=Recursive:slnt,wght,CASL,CRSV,MONO@-15..0,300..800,0..1,0..1,0..1&display=swap");

:root {
  /* set variation axis values */
  --mono: "MONO" 0; /* Monospace: Sans (natural-width) or Mono (fixed-width) */
  --casl: "CASL" 0; /* Casual: Linear to Casual */
  --wght: "wght" 300; /* Weight: Light to ExtraBlack; usually set with `font-weight` */
  --slnt: "slnt" 0; /* Slant: 0 to -15 degrees, auto cursive at -14 */
  --crsv: "CRSV" 0.5; /* Cursive: always roman (0), auto substitution (.5), or always cursive (1) */
}

* {
  font-variation-settings: var(--mono), var(--casl), var(--wght), var(--slnt),
    var(--crsv);
}

body {
  font-family: Recursive, sans-serif;
}

h1,
h2,
h3 {
  --wght: "wght" 600;
  --casl: "CASL" 1;
}

.mono {
  --mono: "mono" 1;
  --wght: "wght" 400;
}

.header-banner h1,
.header-banner h2 {
  --mono: "MONO" 1;
  --casl: "CASL" 0;
  --wght: "wght" 800;
}
```

</details>

NOTE! While what we have done will certainly work, the specification for variable fonts recommends that you use the regular CSS properties to set the registered axes, and only use `font-variations-settings` for any custom axes. Making this change to our CSS would look like the following:

<details>
<summary>Solution 1a</summary>

```css
@import url("https://fonts.googleapis.com/css2?family=Recursive:slnt,wght,CASL,CRSV,MONO@-15..0,300..800,0..1,0..1,0..1&display=swap");

:root {
  /* set variation axis values */
  --mono: "MONO" 0; /* Monospace: Sans (natural-width) or Mono (fixed-width) */
  --casl: "CASL" 0; /* Casual: Linear to Casual */
  --wght: 300; /* Weight: Light to ExtraBlack; usually set with `font-weight` */
  --slnt: 0deg; /* Slant: 0 to -15 degrees, auto cursive at -14 */
  --crsv: "CRSV" 0.5; /* Cursive: always roman (0), auto substitution (.5), or always cursive (1) */
}

* {
  font-weight: var(--wght);
  font-style: oblique var(--slnt);
  font-variation-settings: var(--mono), var(--casl), var(--crsv);
}

body {
  font-family: Recursive, sans-serif;
}

h1,
h2,
h3 {
  --wght: 600;
  --casl: "CASL" 1;
}

.mono {
  --mono: "mono" 1;
  --wght: 400;
}

.header-banner h1,
.header-banner h2 {
  --mono: "MONO" 1;
  --casl: "CASL" 0;
  --wght: 800;
}
```

</details>

## Activity 2

Using a scale to establish harmony with our spacing can make a huge difference in the overall look and feel of a site. [The Article](https://every-layout.dev/rudiments/modular-scale/) you were asked to read from Every Layout suggested using CSS custom properties to make it easy to apply a scale. They provided this code:

```css
--ratio: 1.5;
--s-5: calc(var(--s-4) / var(--ratio));
--s-4: calc(var(--s-3) / var(--ratio));
--s-3: calc(var(--s-2) / var(--ratio));
--s-2: calc(var(--s-1) / var(--ratio));
--s-1: calc(var(--s0) / var(--ratio));
--s0: 1rem;
--s1: calc(var(--s0) * var(--ratio));
--s2: calc(var(--s1) * var(--ratio));
--s3: calc(var(--s2) * var(--ratio));
--s4: calc(var(--s3) * var(--ratio));
--s5: calc(var(--s4) * var(--ratio));
```

1.  Add the code above to the existing `:root` section of our CSS.
2.  More and more the default font size of browsers is not big enough. Set the root font size (rem) to 20px. (hint: set it at the HTML element)
3.  Begin by making sure that our headlines are all sized according to our new scale. Set the sizes as follows:

- H1 to `--s3`
- H2 to `--s2`
- H3 to `--s1`

3.  Set the line-height and margin for the paragraphs (and other elements...) to establish a good flow. The articles [section 2.2.1](http://webtypography.net/2.2.1) and [section 2.2.2](http://webtypography.net/2.2.2) that we read earlier suggested that a value of 1.5 times the font size was usually a good amount for line height. It also tends to work well for the space between paragraphs as well.

4.  Set the spacing for our headlines. We would really like the title to be slightly closer to the paragraph that follows it than the one that precedes it. Since we used 1.5 times (--s1) the base font size for our gap (margin) between paragraphs, try the next step up on our scale (--s2) for the gap above the Headlines. For the bottom margin we can set it to `0` so that the top-margin of the element that follows will have control over that gap.

5.  Measure: set the measure for our elements, again the recommendation from [section 2.1.2](http://webtypography.net/2.1.2) from _The Elements of Typographic Style Applied to the Web_ was that 45 to 75 characters was ideal. Use the `ch` unit to set the width of our text elements to be `70ch`.

<details>
<summary>Solution 2</summary>

```css
@import url("https://fonts.googleapis.com/css2?family=Recursive:slnt,wght,CASL,CRSV,MONO@-15..0,300..800,0..1,0..1,0..1&display=swap");

:root {
  --ratio: 1.5;
  --s-5: calc(var(--s-4) / var(--ratio));
  --s-4: calc(var(--s-3) / var(--ratio));
  --s-3: calc(var(--s-2) / var(--ratio));
  --s-2: calc(var(--s-1) / var(--ratio));
  --s-1: calc(var(--s0) / var(--ratio));
  --s0: 1rem;
  --s1: calc(var(--s0) * var(--ratio));
  --s2: calc(var(--s1) * var(--ratio));
  --s3: calc(var(--s2) * var(--ratio));
  --s4: calc(var(--s3) * var(--ratio));
  --s5: calc(var(--s4) * var(--ratio));

  --font-color: #333;
  /* set variation axis values */
  --mono: "MONO" 0; /* Monospace: Sans (natural-width) or Mono (fixed-width) */
  --casl: "CASL" 0; /* Casual: Linear to Casual */
  --wght: 300; /* Weight: Light to ExtraBlack; usually set with `font-weight` */
  --slnt: 0deg; /* Slant: 0 to -15 degrees, auto cursive at -14 */
  --crsv: "CRSV" 0.5; /* Cursive: always roman (0), auto substitution (.5), or always cursive (1) */
}

* {
  font-weight: var(--wght);
  font-style: oblique var(--slnt);
  font-variation-settings: var(--mono), var(--casl), var(--crsv);
}
html {
  font-size: 20px; // Set the Root EM value
}
body {
  color: var(--font-color);
  font-family: Recursive, sans-serif;
}

h1 {
  font-size: var(--s3);
}
h2 {
  font-size: var(--s2);
}
h3 {
  font-size: var(--s1);
}
h1,
h2,
h3 {
  --wght: 600;
  --casl: "CASL" 1;
  margin-top: var(--s2);
  margin-bottom: 0;
}

p,
ul,
ol,
dd {
  line-height: var(--s1);
  margin: var(--s1);
  max-width: 66ch;
}

.mono {
  --mono: "mono" 1;
  --wght: 400;
}

.header-banner h1,
.header-banner h2 {
  --mono: "MONO" 1;
  --casl: "CASL" 0;
  --wght: 800;
}
```

</details>

## Activity 3 - Stretch!

an example of what we would like the title to look like was given earlier:

![Page title](../../../../img/typography-ponder-title.png)

We should finish styling that now.

1. Use `writing-mode: vertical-rl` to style the html for the header to match the image above.

<details>
<summary>Solution 3</summary>

```css
.header-banner {
  height: 4em;
  padding: var(--s-1);
  background-color: #ddd;
 }
  .header-banner h1,
  .header-banner h2 {
    --mono: "MONO" 1;
    --casl: "CASL" 0;
    --wght: 800;
  }
  .header-banner > div {
    display: flex;
    flex-direction: row-reverse;
    justify-content: flex-end;
    gap: var(--s-1);
  }
  .header-banner h2 {
    writing-mode: vertical-rl;
    height: 4em;
    line-height: 0.8;
    margin: 0;
  }
  .header-banner h1 {
    margin: 0;
  }
}

/* If you wanted to use SCSS it could look like this:
.header-banner {
  height: 4em;
  padding: var(--s-1);
  background-color: #ddd;
  & h1,
  & h2 {
    --mono: "MONO" 1;
    --casl: "CASL" 0;
    --wght: 800;
  }
  > div {
    display: flex;
    flex-direction: row-reverse;
    justify-content: flex-end;
    gap: var(--s-1);
  }
  h2 {
    writing-mode: vertical-rl;
    height: 4em;
    line-height: 0.8;
    margin: 0;
  }
  h1 {
    margin: 0;
  }
} */
```

</details>

Here is also a [link to the finished example](https://byui-cit.github.io/advcss/modules/examples/syllabus/)!
