# gruber.website.html 
# Milestone 2: Accessibility and Visual Design Improvements

## Accessibility Testing and Fixes

### WAVE Accessibility Corrections

1. Added descriptive alternative text to all images so screen reader users can understand image content.
2. Corrected heading hierarchy to maintain a logical page structure.
3. Added explicit labels for all form controls.
4. Added semantic HTML elements (`header`, `nav`, `main`, `section`, and `footer`) to improve navigation and document structure.
5. Improved keyboard accessibility for navigation links, buttons, and form controls.
6. Adjusted all text and background color combinations to meet WCAG AA contrast requirements using the WebAIM Contrast Checker.
7. Added accessible validation error messages using ARIA attributes and screen reader announcements.
8. Ensured all links contain meaningful text that clearly describes their destination or purpose.
9. Resolved all WAVE accessibility errors identified during testing.

### WCAG AA Color Contrast Compliance

All text and background color combinations were tested using the WebAIM Contrast Checker and meet WCAG AA accessibility standards.

---

## Visual Design Decisions

### Gestalt Principle: Proximity

I used proximity by grouping related information within clearly defined sections and project cards. This helps users quickly understand which content belongs together and improves visual organization.

### Gestalt Principle: Similarity

I used similarity by maintaining consistent typography, navigation styling, colors, spacing, buttons, and project card layouts across all pages. This creates a unified experience and helps users recognize recurring content patterns throughout the website.

### Consistent Color Palette

The website uses a consistent color palette across all three pages:

- Primary Color: `#1F3A5F`
- Secondary Color: `#2C5F8A`
- Accent Color: `#D97706`
- Background Color: `#F8F9FA`
- Text Color: `#111827`

All colors were tested using the WebAIM Contrast Checker to ensure compliance with WCAG AA standards.

---

## Accessible Contact Form

### Accessibility Features

- Every form field has an associated `<label>` element.
- Related fields are grouped using `<fieldset>` and `<legend>`.
- Required fields are clearly identified.
- Error messages are announced to assistive technologies using `aria-live="polite"`.
- Error styling includes both color and visual border indicators.
- The form is fully keyboard accessible.

### Contact Form HTML

```html
<form id="contact-form" novalidate>

  <fieldset>
    <legend>Contact Information</legend>

    <label for="name">Name *</label>
    <input
      type="te*t"
      id="name"
      name="nam*"
      required
      aria-descri*edby="name-error">

    <span
    * id="name-error"
      class="erro*-message"
      aria-live="polite"*</span>

    <label for="email">Em*il Address *</label>
    <input
  *   type="email"
      id="email"
 *    name="email"
      required
  *   aria-describedby="email-error">*
    <span
      id="email-error"
*     class="error-message"
      a*ia-live="polite"></span>

  </fiel*set>

  <fieldset>
    <legend>Mes*age</legend>

    <label for="mess*ge">Message *</label>
    <textare*
      id="message"
      name="me*sage"
      rows="5"
      require*
      aria-describedby="message-e*ror"></textarea>

    <span
      *d="message-error"
      class="err*r-message"
      aria-live="polite*></span>

  </fieldset>

  <button*type="submit">Send Message</button*

</form>
```

### Contact Form CS*

```css
.error-message {
  displa*: block;
  color: #b91c1c;
  font-*ize: 0.9rem;
  margin-top: 0.25rem;
}

.input-error {
  border: 2px solid #b91c1c;
  background-color: #fef2f2;
}

button {
  background-color: #1f3a5f;
  color: white;
  padding: 0.75rem 1.25rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover,
button:focus {
  background-color: #2c5f8a;
}
```

### Contact Form Validation JavaScript

```javascript
const form = document.getElementById("contact-form");

form.addEventListener("submit", function (event) {
  let isValid = true;

  const name = document.getElementById("name");
  const email = document.getElementById("email");
  const message = document.getElementById("message");

  document.querySelectorAll(".error-message").forEach((error) => {
    error.textContent = "";
  });

  document.querySelectorAll(".input-error").forEach((field) => {
    field.classList.remove("input-error");
  });

  if (name.value.trim() === "") {
    document.getElementById("name-error").textContent =
      "Please enter your name.";
    name.classList.add("input-error");
    isValid = false;
  }

  if (email.value.trim() === "") {
    document.getElementById("email-error").textContent =
      "Please enter your email address.";
    email.classList.add("input-error");
    isValid = false;
  }

  if (message.value.trim() === "") {
    document.getElementById("message-error").textContent =
      "Please enter a message.";
    message.classList.add("input-error");
    isValid = false;
  }

  if (!isValid) {
    event.preventDefault();
  }
});
```

---

## Summary

This portfolio was refined to improve accessibility, usability, and visual consistency. All WAVE accessibility errors were corrected, WCAG AA color contrast requirements were met, Gestalt design principles were intentionally implemented, and an accessible contact form with semantic structure, labels, fieldsets, legends, and validation feedback was added to support all users.
