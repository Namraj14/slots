<slot>
    Slots  
    Add a slot to a component’s HTML file so a parent component can pass markup into the component. A component can have zero or more slots.

    A slot (<slot></slot>) is a placeholder for markup that a parent component passes into a component’s body.
</slot>

<slot>
    A slot allows a child component to accept and render HTML content provided by its parent component.
</slot>

🧩 Basic Example with Syntax
1. Default Slot (Unnamed)
📦 Child Component (childComponent.html)

<template>
  <div class="box">
    <p>Inside Child:</p>
    <slot></slot> <!-- This will be replaced by content from parent -->
  </div>
</template>
📦 Parent Component (parentComponent.html)

<template>
  <c-child-component>
    <p>This is from Parent Component</p>
  </c-child-component>
</template>
🔍 Output:

Inside Child:
This is from Parent Component
