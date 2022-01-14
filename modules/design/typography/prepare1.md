---
title: Typography for the Web - Fundamentals
description: The Principles behind good typography for the web.
date: 2021-10-15

layout: layouts/post.njk
---

## Fonts

If you search online about typography on the web, you will find a lot of information. The purpose of most websites is to deliver information. Most of that information comes in the form of text. Typography is a vast subject and so it is common to see attempts to simplify it into lists of best practices. Most of these give good advice. Here is an example of what you will commonly see on these lists: (https://blog.hubspot.com/website/website-typography)

1. Limit the number of typefaces per website.
2. Use a sans serif font for body text.
3. Stick to standard fonts at first.
4. Size your text appropriately.
5. Don’t use all caps.
6. Use colors carefully and intentionally.
7. Stay between around 40 and 80 characters per line.
8. Provide sufficient spacing between lines.
9. Eliminate text animations.

Here are some more [guidelines on Web Typography](https://cdn2.hubspot.net/hubfs/2799924/Design-Infographics/Infographic-Guide-to-Web-Typography-Toptal.pdf) from [Toptal](https://www.toptal.com/designers/typography/web-typography-infographic)

### Choosing a font

The list above lists some general guidelines about font usage. Read the section starting with "How to choose the perfect font" from [Elementor: Web Typography](https://elementor.com/blog/guide-to-web-typography/) for some additional tips.

For the advice of respected designer Massimo Vignelli, read pages 54-72 of [The Vignelli Canon](../../../../img/VignelliCanon.pdf). The whole document is great. He has some very strong opinions!

### @font-face

Once you have found that perfect font for your project, you often must make that font available in your CSS before you can use it. This is the role of `@font-face`

Most of you have used this before, even if you don't realize it. For example if you have included a font from Google fonts you might have added a line like this to your CSS: `@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;800&display=swap');` Have you ever looked at the .CSS file that you imported? If you do that now you will see something like this:

```css
@font-face {
  font-family: "Open Sans";
  font-style: normal;
  font-weight: 400;
  font-stretch: 100%;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/opensans/v27/memvYaGs126MiZpBA-UvWbX2vVnXBbObj2OVTS-mu0SC55I.woff2)
    format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
    U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
    U+FEFF, U+FFFD;
}
```

`@font-face` is what really does the magic of making a custom font available to your page.

For more information about the specifics of writing your own `@font-face` rules read [Using @font-face](https://css-tricks.com/snippets/css/using-font-face-in-css/) (CSS Tricks)

### Variable fonts

Variable Fonts are an exciting new addition to CSS. They help us solve the problem of excessive weight added to a page when several styles of custom fonts are required (bold, italic, etc).

Review the following resources on CSS Variable Fonts

- [Variable Fonts Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Fonts/Variable_Fonts_Guide) MDN
- [Introduction to Variable Fonts](https://24ways.org/2019/an-introduction-to-variable-fonts/) 24 Ways

Note especially that the 5 registered axes are: weight (wght), width (wdth), italic (ital), slant (slnt), and optical size (opsz). They can be set either though built in CSS properties (font-weight: 400, font-stretch: 60%, font-style: italic, font-style: oblique 10deg, and font-optical-sizing: none|auto), and custom axes would have to be set using the `font-variation-settings` property.

## Scale with Harmony

Read about the principle of Scale and Harmony with typography in [section 3.1.1](http://webtypography.net/3.1.1) of [The Elements of Typographic Style Applied to the Web](http://webtypography.net/toc/). Then continue with a very nice article about how one might implement a [modular scale](https://every-layout.dev/rudiments/modular-scale/) with CSS

## Measure

The width of a line of text, in characters, is known as its **measure**. If you read [section 2.1.2](http://webtypography.net/2.1.2) from _The Elements of Typographic Style Applied to the Web_, it suggests that a measure of 45 - 75 characters is good, with 66 being ideal. How can we best apply that to our designs? Read about [Axioms](https://every-layout.dev/rudiments/axioms/) on _Every Layout_ for some great ideas.

## Whitespace and flow

As stated earlier, a websites main purpose is very often to distribute information, and type is the medium by which this is usually done. **Whitespace** is the space between design elements, and is very important. If we go back and consult [The Vignelli Canon](../../../../img/VignelliCanon.pdf) again, this time around page 92. We learn about several elements that make up the whitespace in a design. We should know how to modify each of these in CSS:

- **leading**: this controlled by [line-height](https://developer.mozilla.org/en-US/docs/Web/CSS/line-height) in our css.
- tight or loose **type setting**: would be controlled with [word-spacing](https://developer.mozilla.org/en-US/docs/Web/CSS/word-spacing)
- **padding**: the internal space on an element is controlled with [padding](https://developer.mozilla.org/en-US/docs/Web/CSS/padding)
- **margin**: the external spacing of an element is [margin](https://developer.mozilla.org/en-US/docs/Web/CSS/margin)
- **letter spacing** (kearning): [letter-spacing](https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing)

Finally read [section 2.2.1](http://webtypography.net/2.2.1) and [section 2.2.2](http://webtypography.net/2.2.2) from _The Elements of Typographic Style Applied to the Web_ to learn the importance of vertical space in establishing a good flow.

---

## Text orientation and Writing modes

Sometimes it becomes necessary to display our text in something other than the default (for most western countries) of left to right, top to bottom. This might be for a creative reason as you see in [these examples](https://labs.jensimmons.com/#writing-modes) from Jen Simmons, or it might be because your site needs to be read in a language that functions differently than the one the site was created in.

Read more about [CSS Writing Modes](https://24ways.org/2016/css-writing-modes/) to learn more.

You may also want to review the following CSS articles:

- [text-orientation](https://developer.mozilla.org/en-US/docs/Web/CSS/text-orientation) MDN
- [writing-mode](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode) MDN
- [Handling different Text Directions](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Handling_different_text_directions) MDN
