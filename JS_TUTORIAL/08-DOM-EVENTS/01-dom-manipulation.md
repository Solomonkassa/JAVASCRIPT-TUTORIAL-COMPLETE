# DOM Manipulation and Events

The DOM (Document Object Model) is how JavaScript interacts with HTML. Events let you respond to user actions.

## Table of Contents
- [What is the DOM](#what-is-the-dom)
- [Selecting Elements](#selecting-elements)
- [Modifying Elements](#modifying-elements)
- [Creating Elements](#creating-elements)
- [Events](#events)
- [Event Delegation](#event-delegation)
- [Practical Examples](#practical-examples)
- [Exercises](#exercises)

---

## What is the DOM

The DOM represents your HTML as a tree of objects that JavaScript can interact with.

```html
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    <h1>Welcome</h1>
    <p>Hello</p>
  </body>
</html>
```

In JavaScript:
```javascript
document.documentElement  // <html>
document.head             // <head>
document.body             // <body>
document.title            // 'My Page'
```

---

## Selecting Elements

### getElementById
```javascript
const header = document.getElementById('main-header');
console.log(header); // <h1 id="main-header">...</h1>
```

### querySelector
```javascript
// Select first matching element
const button = document.querySelector('button');
const userEmail = document.querySelector('.user-email');
const header = document.querySelector('#header');
```

### querySelectorAll
```javascript
// Select all matching elements
const allButtons = document.querySelectorAll('button');
const items = document.querySelectorAll('.list-item');

// Loop through results
allButtons.forEach(button => {
  console.log(button.textContent);
});
```

### Other Methods
```javascript
document.getElementsByClassName('active');  // Live HTMLCollection
document.getElementsByTagName('p');         // Live HTMLCollection
document.getElementsByName('username');     // Live HTMLCollection
```

---

## Modifying Elements

### Text Content
```javascript
const heading = document.querySelector('h1');

// Read
console.log(heading.textContent); // Gets text

// Write
heading.textContent = 'New Title';
```

### HTML Content
```javascript
const container = document.querySelector('.container');

// Read
console.log(container.innerHTML);

// Write
container.innerHTML = '<p>New paragraph</p>';

// Append
container.innerHTML += '<p>Another paragraph</p>';
```

### Attributes
```javascript
const link = document.querySelector('a');

// Get attribute
console.log(link.getAttribute('href')); // Gets href

// Set attribute
link.setAttribute('href', 'https://example.com');
link.setAttribute('target', '_blank');

// Remove attribute
link.removeAttribute('disabled');

// Check if has attribute
if (link.hasAttribute('target')) {
  console.log('Has target attribute');
}

// Using properties directly
link.href = 'https://example.com';
link.id = 'main-link';
```

### Classes
```javascript
const button = document.querySelector('button');

// Add class
button.classList.add('active');

// Remove class
button.classList.remove('active');

// Toggle class
button.classList.toggle('active'); // Adds if not present, removes if present

// Check if has class
if (button.classList.contains('disabled')) {
  console.log('Button is disabled');
}

// Replace class
button.classList.replace('old-class', 'new-class');
```

### Styles
```javascript
const box = document.querySelector('.box');

// Set individual styles
box.style.color = 'red';
box.style.backgroundColor = 'blue';
box.style.padding = '20px';
box.style.fontSize = '16px';

// Get computed style
const computed = window.getComputedStyle(box);
console.log(computed.color);
console.log(computed.backgroundColor);
```

---

## Creating Elements

### Creating and Inserting
```javascript
// Create element
const newParagraph = document.createElement('p');
newParagraph.textContent = 'This is a new paragraph';

// Append to body
document.body.appendChild(newParagraph);

// Insert at specific position
const container = document.querySelector('.container');
container.appendChild(newParagraph);
```

### InsertAdjacentHTML
```javascript
const element = document.querySelector('#target');

// Insert before the element
element.insertAdjacentHTML('beforebegin', '<p>Before</p>');

// Insert as first child
element.insertAdjacentHTML('afterbegin', '<p>Start</p>');

// Insert as last child
element.insertAdjacentHTML('beforeend', '<p>End</p>');

// Insert after the element
element.insertAdjacentHTML('afterend', '<p>After</p>');
```

### InsertBefore
```javascript
const parent = document.querySelector('.container');
const newItem = document.createElement('li');
const firstItem = parent.firstChild;

parent.insertBefore(newItem, firstItem);
```

### Removing Elements
```javascript
const element = document.querySelector('.old-element');
element.remove();  // Remove from DOM

// Or using parent
element.parentElement.removeChild(element);
```

---

## Events

Events are triggered by user actions like clicks, typing, etc.

### Adding Event Listeners
```javascript
const button = document.querySelector('button');

// Using addEventListener (preferred)
button.addEventListener('click', function() {
  console.log('Button clicked!');
});

// Or with arrow function
button.addEventListener('click', () => {
  console.log('Button clicked!');
});
```

### Common Events
```javascript
// Click events
element.addEventListener('click', handler);
element.addEventListener('dblclick', handler);

// Mouse events
element.addEventListener('mouseover', handler);
element.addEventListener('mouseout', handler);
element.addEventListener('mousemove', handler);

// Form events
input.addEventListener('focus', handler);
input.addEventListener('blur', handler);
input.addEventListener('change', handler);
input.addEventListener('input', handler);
form.addEventListener('submit', handler);

// Keyboard events
document.addEventListener('keydown', handler);
document.addEventListener('keyup', handler);
document.addEventListener('keypress', handler);

// Window events
window.addEventListener('load', handler);
window.addEventListener('resize', handler);
window.addEventListener('scroll', handler);
```

### Event Object
```javascript
button.addEventListener('click', (event) => {
  console.log(event.type);       // 'click'
  console.log(event.target);     // The clicked element
  console.log(event.target.id);  // Element's ID
  console.log(event.clientX);    // Mouse X position
  console.log(event.clientY);    // Mouse Y position
  
  event.preventDefault();        // Prevent default action
  event.stopPropagation();       // Stop bubbling
});
```

### Form Submission
```javascript
const form = document.querySelector('form');

form.addEventListener('submit', (event) => {
  event.preventDefault(); // Don't reload page
  
  const name = form.querySelector('input[name="name"]').value;
  const email = form.querySelector('input[name="email"]').value;
  
  console.log(`Name: ${name}, Email: ${email}`);
  
  // Send to server
  // fetch('/api/users', { method: 'POST', body: {...} })
});
```

### Input Validation
```javascript
const input = document.querySelector('input[type="email"]');

input.addEventListener('blur', (event) => {
  if (!event.target.value.includes('@')) {
    event.target.classList.add('error');
  } else {
    event.target.classList.remove('error');
  }
});
```

---

## Event Delegation

Handle events on parent element for multiple children.

### Without Delegation (Inefficient)
```javascript
// Add listener to each button
const buttons = document.querySelectorAll('button');
buttons.forEach(button => {
  button.addEventListener('click', () => {
    console.log('Button clicked');
  });
});
```

### With Delegation (Efficient)
```javascript
// Add listener to parent
const container = document.querySelector('.button-container');

container.addEventListener('click', (event) => {
  if (event.target.tagName === 'BUTTON') {
    console.log('Button clicked:', event.target.textContent);
  }
});
```

### Practical Example: Todo List
```javascript
const todoList = document.querySelector('#todo-list');

// Single listener handles all items
todoList.addEventListener('click', (event) => {
  if (event.target.classList.contains('delete-btn')) {
    event.target.parentElement.remove();
  }
  
  if (event.target.classList.contains('complete-btn')) {
    event.target.parentElement.classList.toggle('completed');
  }
});
```

---

## Practical Examples

### Toggle Menu
```javascript
const menuButton = document.querySelector('.menu-button');
const menu = document.querySelector('.menu');

menuButton.addEventListener('click', () => {
  menu.classList.toggle('open');
});
```

### Show/Hide Password
```javascript
const passwordInput = document.querySelector('input[type="password"]');
const toggleButton = document.querySelector('.toggle-password');

toggleButton.addEventListener('click', () => {
  const type = passwordInput.type === 'password' ? 'text' : 'password';
  passwordInput.type = type;
  toggleButton.textContent = type === 'password' ? 'Show' : 'Hide';
});
```

### Character Counter
```javascript
const textarea = document.querySelector('textarea');
const counter = document.querySelector('.character-count');
const maxChars = 100;

textarea.addEventListener('input', (event) => {
  const count = event.target.value.length;
  counter.textContent = `${count}/${maxChars}`;
  
  if (count >= maxChars) {
    counter.classList.add('warning');
  } else {
    counter.classList.remove('warning');
  }
});
```

### Search Filter
```javascript
const searchInput = document.querySelector('#search');
const items = document.querySelectorAll('.item');

searchInput.addEventListener('input', (event) => {
  const query = event.target.value.toLowerCase();
  
  items.forEach(item => {
    const text = item.textContent.toLowerCase();
    item.style.display = text.includes(query) ? 'block' : 'none';
  });
});
```

---

## Exercises

### Exercise 1: Change Background Color
Create a button that changes the background color when clicked.

**Solution:**
```javascript
const button = document.querySelector('button');

button.addEventListener('click', () => {
  const randomColor = '#' + Math.floor(Math.random()*16777215).toString(16);
  document.body.style.backgroundColor = randomColor;
});
```

### Exercise 2: Toggle Element Visibility
Create a button that shows/hides a paragraph.

**Solution:**
```javascript
const button = document.querySelector('.toggle-btn');
const paragraph = document.querySelector('p');

button.addEventListener('click', () => {
  paragraph.style.display = paragraph.style.display === 'none' ? 'block' : 'none';
});
```

### Exercise 3: Todo Item Counter
Count and display number of items in a list.

**Solution:**
```javascript
const todoList = document.querySelector('#todo-list');
const counter = document.querySelector('.item-count');

function updateCount() {
  counter.textContent = todoList.children.length;
}

// Update on page load
updateCount();

// Update when items are added
todoList.addEventListener('click', (event) => {
  if (event.target.classList.contains('delete-btn')) {
    event.target.parentElement.remove();
    updateCount();
  }
});
```

---

## Next Steps

→ [Back to DOM & Events](./README.md)  
→ [Modern JavaScript](../09-MODERN-JS/README.md)
