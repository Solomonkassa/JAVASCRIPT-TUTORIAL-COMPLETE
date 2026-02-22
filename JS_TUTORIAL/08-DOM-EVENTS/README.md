# DOM & Events: Interacting with Web Pages

Learn to manipulate HTML and respond to user interactions.

## Topics Covered

1. **[DOM Basics](./01-dom-basics.md)** - Accessing HTML elements
2. **[DOM Manipulation](./02-dom-manipulation.md)** - Modifying content and attributes
3. **[DOM Navigation](./03-dom-navigation.md)** - Traversing the DOM tree
4. **[Events Basics](./04-events-basics.md)** - Handling user interactions
5. **[Event Listeners](./05-event-listeners.md)** - addEventListener and event delegation
6. **[Event Objects](./06-event-objects.md)** - Working with event data
7. **[Event Propagation](./07-event-propagation.md)** - Bubbling and capturing

## Quick Reference

### Selecting Elements
```javascript
// Single element
document.getElementById("myId")
document.querySelector(".myClass")

// Multiple elements
document.querySelectorAll(".myClass")
document.getElementsByClassName("myClass")
```

### Manipulating Content
```javascript
element.textContent = "New text"
element.innerHTML = "<p>HTML content</p>"
element.className = "new-class"
```

### Event Listeners
```javascript
element.addEventListener("click", (event) => {
    console.log("Clicked!");
});
```

## What is the DOM?

The **Document Object Model (DOM)** is a programming interface for web documents. It represents the page so programs can change the structure, style, and content dynamically.

**The DOM is a tree:**
```
Document
  └─ html
      ├─ head
      │   ├─ title
      │   └─ meta
      └─ body
          ├─ header
          ├─ main
          │   ├─ article
          │   └─ article
          └─ footer
```

## Common Event Types

| Event | When | Example |
|-------|------|---------|
| click | User clicks element | Button, link click |
| change | Form input changes | Select dropdown, checkbox |
| submit | Form submitted | Form submission |
| focus | Element gets focus | Input field selected |
| blur | Element loses focus | Moving away from input |
| keydown | Key pressed down | Keyboard input |
| scroll | Page scrolls | User scrolling |
| load | Page fully loaded | Image, page load |
| resize | Window resized | Responsive behavior |

## Real-World Patterns

**Toggle visibility:**
```javascript
const button = document.getElementById("toggle");
const content = document.getElementById("content");
button.addEventListener("click", () => {
  content.classList.toggle("hidden");
});
```

**Form validation:**
```javascript
const form = document.getElementById("myForm");
form.addEventListener("submit", (e) => {
  e.preventDefault();
  if (validateForm()) {
    form.submit();
  }
});
```

**Event delegation (many items):**
```javascript
document.getElementById("list").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log("Item clicked:", e.target.textContent);
  }
});
```

## Learning Path

```
DOM Basics → DOM Manipulation → DOM Navigation 
→ Events Basics → Event Listeners → Event Objects 
→ Event Propagation
```

## Key Concepts

- **DOM Nodes**: Every element in HTML is a node
- **Selecting**: Finding elements with selectors
- **Manipulation**: Changing content, styles, attributes
- **Navigation**: Moving between parent/child/sibling nodes
- **Events**: Responding to user actions
- **Event Listeners**: Functions that run when events occur
- **Propagation**: How events bubble through the DOM tree
- **Delegation**: Efficient event handling for many elements

## DOM Manipulation Best Practices

- Use `textContent` instead of `innerHTML` when setting plain text
- Use `classList` instead of manually changing `className`
- Avoid repeatedly accessing same element (cache in variables)
- Use event delegation for dynamic content
- Remove event listeners when no longer needed
- Be careful with innerHTML (security risk with user input)

## Common Mistakes to Avoid

- Accessing DOM before page loads (script in head without defer)
- Using `innerHTML` with user input (XSS vulnerability)
- Not removing event listeners (memory leaks)
- Selecting elements incorrectly (wrong selector)
- Modifying className directly instead of using classList
- Not preventing default behavior when needed (e.preventDefault())

## Performance Optimization

- Use event delegation instead of many listeners
- Cache DOM queries in variables
- Use `requestAnimationFrame` for animations
- Batch DOM updates to avoid reflows
- Use `addEventListener` instead of on* attributes
- Consider DocumentFragment for multiple insertions

## Practice Exercises

1. Create an interactive to-do list with add/delete/complete
2. Build a form with real-time validation feedback
3. Create a color picker with DOM manipulation
4. Build an accordion that expands/collapses sections
5. Create a counter with increment/decrement buttons
6. Build a dynamic table that adds/removes rows
7. Create keyboard shortcuts for common actions
8. Build a modal dialog with open/close functionality

## Advanced Topics

- Virtual DOM (frameworks like React)
- Shadow DOM
- MutationObserver
- Intersection Observer
- Performance optimization
- Accessibility (ARIA attributes)

## Use DOM to

- Create dynamic web pages that respond to users
- Respond to user input (clicks, typing, scrolling)
- Update content without reloading page
- Build interactive applications
- Create animations and transitions
- Implement user-friendly interfaces

---

**Course Section**: DOM & Events - Interactive Web Pages  
**Author**: Solomon Kassa  
**Last Updated**: February 2026  
**Difficulty**: Intermediate  
**Prerequisites**: Fundamentals, Functions, Objects & Arrays  
**Next**: Modern JavaScript section

**Start with**: [DOM Manipulation & Events](./01-dom-manipulation.md)

---

[← Back to Main](../README.md) | [Modern JS →](../09-MODERN-JS/README.md)
