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


## 2. Named Slots  
Used when you want to have multiple content areas inside the child component.

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
