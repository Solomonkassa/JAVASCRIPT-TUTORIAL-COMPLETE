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

---

## Learning Path

```
DOM Basics → DOM Manipulation → DOM Navigation 
→ Events Basics → Event Listeners → Event Objects 
→ Event Propagation
```

**Use DOM to**:
- Create dynamic web pages
- Respond to user input
- Update content without reloading
- Build interactive applications

**Start with**: [DOM Basics](./01-dom-basics.md)

---

[← Back to Main](../README.md) | [Modern JS →](../09-MODERN-JS/README.md)
