---
title: Modals - Introduction
description: What are modals, what are they used for and how are they made?
date: 2024-09-25

layout: layouts/post.njk
---

## What is a modal?

A modal is a dialog box/pop-up that appears on top of the main content, usually to capture user input or display important information.

Modals appear on top of the main content, often with a semi-transparent background to distinguish it from the underlying content. They can be closed by the user, usually by clicking on a close button or pressing the Esc key. They can be used to display a variety of content, such as text, images, forms, or other interactive elements.

### Common Use Cases

- Displaying additional information about a product or service.
- Prompting the user to log in or register.
- Providing a contact form or other interactive element.
- Displaying a warning or error message.
- Offering a special promotion or discount.

## Best Practices for Modals

- Accessibility: Ensure modals are keyboard navigable.
- Use ARIA roles and attributes, like role="dialog" and aria-labelledby.
- Ensure focus is trapped within the modal while it’s open.
- Clearly indicate how to close the modal.
- Avoid overusing modals; they can disrupt the user experience.
- Make sure the content is relevant and concise.

## Example

Below is markup for a simple modal dialog.

```html
<div
  id="modal"
  class="modal"
  role="dialog"
  aria-labelledby="modal-title"
  aria-modal="true"
  aria-hidden="true"
>
  <section class="modal-content">
    <span class="close-button" aria-label="Close modal">&times;</span>
    <h2 id="modal-title">Modal Title</h2>
    <p id="modal-description">This is a simple modal example.</p>
    <input type="text" placeholder="Your feedback" />
    <button>Submit</button>
  </section>
</div>
```

1. The whole modal is wrapped in a `div` this div will normally be hidden by CSS when the page loads. Normally the `.modal` container will be styled to cover the entire window, and will have a background that obscures the other content so that the user will focus on the modal.
    - The `role="dialog"` attribute is used to indicate that the modal is a dialog box
    - The `aria-labelledby` attribute is used to link the modal to the title of the modal
    - The `aria-modal="true"` attribute is used to indicate that the modal is modal (
    - The `aria-hidden="true"` attribute is used to prevent the modal from being focusable
2. The modal content is wrapped in a `section` element. The modal should have a clear way to close it. This can be a button or the escape key (or both)
    - The `aria-label` attribute is used to provide a label for the close button that screen readers can announce to the user.
3. The modal should have a clear title and description. This can be a heading and a paragraph
4. If the modal expects input there should be a clearly marked 'submit' button
5. The modal should be positioned absolutely and have a z-index greater than the rest of the content. It needs to be on top!
6. Javascript is generally needed to show the modal and later dismiss it. There should be a clearly labeled button to bring the modal up.

Continue to the [Practice with Modals](../ponder1) activity to actually build a functional modal.
