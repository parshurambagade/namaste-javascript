# Event Bubbling and Capturing

## Understanding Event Bubbling and Capturing

Event bubbling and capturing are two fundamental methods for handling event propagation in the Document Object Model (DOM). These methods determine the order in which events are received by elements.

### Event Propagation

When an event is fired on an element, it can be managed not only by that element but also by its parent, grandparent, and so on up to the document node, unless propagation is explicitly stopped. Here's how the two strategies work:

#### Event Bubbling (Bottom-Up)

- **Process**: In event bubbling, the event is first captured and handled by the innermost element and then propagated to outer elements.
- **Example**: If a user clicks on a button nested within several layers of `div` elements, the event will first be handled by the button, then by its parent `div`, and so on up to the root.

```javascript
// Example of Event Bubbling
document.getElementById("child").addEventListener("click", function() {
    console.log("Child clicked!");
});

document.getElementById("parent").addEventListener("click", function() {
    console.log("Parent clicked!");
});
```

### Event Capturing/Trickling (Top-Down)

- **Process**: Event capturing is the opposite of event bubbling. The event is first captured at the highest level, and it is then propagated down to the target element.
- **Example**: Using the same structure as above, the event would first trigger an event handler on the root element and then fire handlers as it propagates down to the target.

```javascript
// Example of Event Capturing
document.getElementById("parent").addEventListener("click", function() {
    console.log("Parent clicked!");
}, true); // the 'true' parameter makes it capture

document.getElementById("child").addEventListener("click", function() {
    console.log("Child clicked!");
}, true);
```
### Third parameter in `addEventListener`

The third parameter in `addEventListener` determines the event phase:

- `true`: Capturing phase 
- `false` or omitted: Bubbling phase 

This parameter controls when the event handler is executed during event propagation, allowing developers to specify the desired phase for handling events.

### Stopping Event Propagation

To prevent further propagation of an event (whether in bubbling or capturing phase), you can use the `stopPropagation` method. This method stops the event from traveling further through the event flow.

```javascript
document.getElementById("child").addEventListener("click", function(event) {
    event.stopPropagation();
    console.log("Child clicked and propagation stopped!");
});
```

## Practical Application: Setting Up DOM Elements and Event Handlers

Consider a scenario where you set up a simple webpage structure with a "grandparent", "parent", and "child" div.

### HTML Structure

```html
<div id="grandparent">
    <div id="parent">
        <div id="child">Click me!</div>
    </div>
</div>
```

### CSS Styling

To make the divs visually distinct:

```css
#grandparent, #parent, #child {
    min-width: 100px;
    min-height: 100px;
    padding: 30px;
    border: 1px solid black;
}
```

### Adding Event Listeners

```javascript
let elGrandparent = document.getElementById("grandparent");
let elParent = document.getElementById("parent");
let elChild = document.getElementById("child");

elChild.addEventListener("click", function() {
    console.log("Child clicked!");
});

elParent.addEventListener("click", function() {
    console.log("Parent clicked!");
});

elGrandparent.addEventListener("click", function() {
    console.log("Grandparent clicked!");
});
```

Remember, proper handling of event propagation is crucial in JavaScript applications to maintain control over application flow and to prevent unintended actions from occurring due to mismanagement of events.  