<slot>
    Slots  
    Add a slot to a component’s HTML file so a parent component can pass markup into the component. A component can have zero or more slots.

    A slot (<slot></slot>) is a placeholder for markup that a parent component passes into a component’s body.
</slot>

<slot>
    A slot allows a child component to accept and render HTML content provided by its parent component.
</slot>

## 🧩 Basic Example with Syntax  
### 1. Default Slot (Unnamed)

---

### 📦 Child Component (`childComponent.html`)
```html
<template>
  <div class="box">
    <p>Inside Child:</p>
    <slot></slot> <!-- This will be replaced by content from parent -->
  </div>
</template>

### 📦 Parent Component (`parentComponent.html`)
```html
<template>
  <c-child-component>
    <p>This is from Parent Component</p>
  </c-child-component>
</template>

Output:
Inside Child:
This is from Parent Component


### 2. Named Slots

---

### 📦 Child Component (`childComponent.html`)
```html
<template>
  <div class="header">
    <slot name="header">Default Header</slot>
  </div>
  <div class="body">
    <slot name="body">Default Body</slot>
  </div>
  <div class="footer">
    <slot name="footer">Default Footer</slot>
  </div>
</template>


### 📦 Parent Component (`parentComponent.html`)
```html
<template>
  <c-child-component>
    <h1 slot="header">Custom Header from Parent</h1>
    <p slot="body">Custom Body Content</p>
    <p slot="footer">Custom Footer Text</p>
  </c-child-component>
</template>

Output:
Custom Header from Parent  
Custom Body Content  
Custom Footer Text


### 3. Slot with Fallback Content  
If the parent doesn’t provide content, the child can show a default.

---

### 📦 Child Component (`childComponent.html`)
```html
<template>
  <slot name="info">No info provided</slot>
</template>

### 📦 Parent Component (`parentComponent.html`)
```html
<template>
  <c-child-component></c-child-component>
</template>

Output:
No info provided

4. Accessing Elements Passed Via Slots
What is a slot?
A slot is a special place inside a child component where the parent can put some HTML.

1. Child component: cChild
cChild.html

<template>
  <div class="container">
    <slot></slot>
  </div>
  <button onclick={handleClick}>Check Slotted Content</button>
</template>
cChild.js

import { LightningElement } from 'lwc';

export default class CChild extends LightningElement {
    handleClick() {
        // Access elements passed from parent via slot
        // Note: use this.querySelector, NOT this.template.querySelector
        const slottedSpan = this.querySelector('span');
        if (slottedSpan) {
            alert('First slotted <span> content: ' + slottedSpan.textContent);
        } else {
            alert('No <span> element found in slot.');
        }
    }
}
2. Parent component: cParent
cParent.html

<template>
  <c-child>
    <span>Hello!</span>
    <span>How are you?</span>
  </c-child>
</template>
Explanation:
The parent passes two <span> elements inside the <c-child> component.

Inside cChild.js, this.querySelector('span') accesses the first slotted <span>.

The button triggers handleClick(), which alerts the content of the first slotted <span>.

5. Showing Slots Only Sometimes (Conditional Slots)
Sometimes you want to show slot content only if a condition is true.

How to do it?

Use a <template> with lwc:if:

<template>
  <template lwc:if={showSlot}>
    <slot></slot>  <!-- Show slot only if showSlot is true -->
  </template>
</template>
Example:

If showSlot = true, the slot content appears.

If showSlot = false, the slot content is hidden.


| Concept                         | How to do it                                                                   |
| ------------------------------- | ------------------------------------------------------------------------------ |
| Access elements passed via slot | Use `this.querySelector()` or `this.querySelectorAll()` inside child component |
| Show slot content conditionally | Wrap `<slot></slot>` inside `<template lwc:if={condition}>`                    |


| Feature                    | `@api` (Props)                    | `slot` (Content Injection)                    |
| -------------------------- | --------------------------------- | --------------------------------------------- |
| Pass text/data             | ✅ Yes                             | ❌ Not directly (must wrap it in markup)       |
| Pass HTML/markup           | ❌ No                              | ✅ Yes                                         |
| Layout defined by          | Child component                   | Parent component                              |
| Reusability for complex UI | ❌ Limited                         | ✅ Very high                                   |
| Example use cases          | Set title, show/hide, button text | Modal content, card layouts, dynamic sections |

