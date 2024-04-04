
JavaScript Execution and Event Loop Notes
=========================================

JavaScript Execution Process
----------------------------

JavaScript is a synchronous, single-threaded language. It executes code line by line.

Global execution context is created when a JavaScript program starts. Code is executed within this context.

Execution context of functions is pushed onto the call stack when they are invoked and popped off when done.

**Example:**
```js
    function a() {
        console.log(4);
    }
    console.log('start');
    a();
    console.log('end');
        
``` 
This code will print:
```
    start
    4
    end
```    

Event Loop and Asynchronous JavaScript
--------------------------------------

JavaScript does not wait for asynchronous tasks like timers or network requests. Event Loop manages these tasks.

Web APIs provide functionalities like `setTimeout()`, `fetch()`, and DOM manipulation.

Callback functions from Web APIs are added to the callback queue when tasks are complete.

Event Loop continuously checks the call stack and callback queue. It moves callbacks from the queue to the stack when the stack is empty.

**Example:**
```js 
    console.log('start');
    setTimeout(() => {
        console.log('callback');
    }, 5000);
    console.log('end');
```      

This code will print:
```   
    start
    end
    callback
```      

Microtask Queue and Priority
----------------------------

Microtask queue has higher priority than the callback queue. Promises and Mutation Observer callbacks go to the microtask queue.

Event Loop executes microtasks before callbacks. This ensures priority for tasks like promise resolutions.

Conclusion
----------

JavaScript execution involves the call stack, event loop, and task queues. Understanding these concepts is crucial for writing efficient asynchronous code.

JavaScript's power lies in its ability to handle asynchronous tasks effectively, providing a smooth user experience.
