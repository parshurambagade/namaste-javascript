
Call, Apply, and Bind Methods
============================================

JavaScript provides three methods - **call**, **apply**, and **bind** - for manipulating the context of functions and borrowing functions from other objects.

1\. Call Method:
----------------

*   Invokes a function directly with the specified context.
*   Syntax: `function.call(context, arg1, arg2, ...)`
*   Passes arguments individually.
*   Useful for function borrowing.

### Example:
```javascript
    // Define a function
    function printFullName() {
      console.log(this.firstName + ' ' + this.lastName);
    }
    
    // Create an object
    let name = {
      firstName: 'Sachin',
      lastName: 'Tendulkar'
    };
    
    // Call the function with object's context
    printFullName.call(name); // Output: Sachin Tendulkar
```   

2\. Apply Method:
-----------------

*   Similar to `call` method but accepts arguments as an array.
*   Syntax: `function.apply(context, [arg1, arg2, ...])`
*   Useful when the number of arguments is variable or unknown.

### Example:
```javascript
    // Define a function with additional parameters
    function printLocation(hometown, state) {
      console.log(this.firstName + ' ' + hometown + ', ' + state);
    }
    
    // Call the function with object's context and arguments array
    printLocation.apply(name, ['Mumbai', 'Maharashtra']); // Output: Sachin Mumbai, Maharashtra
```    

3\. Bind Method:
----------------

*   Creates a new function with the specified context bound to it.
*   Does not invoke the function immediately; returns a copy of the function.
*   Syntax: `function.bind(context)`
*   Useful for creating function references with predefined contexts.

### Example:
```javascript
    // Bind the function to the object and get a new function reference
    let printMyName = printFullName.bind(name);
    
    // Invoke the new function later
    printMyName(); // Output: Sachin Tendulkar
    
```
Conclusion:
-----------

Understanding the **call**, **apply**, and **bind** methods in JavaScript is essential for manipulating function contexts and facilitating function reuse. These concepts are frequently tested in interviews and are foundational to many other JavaScript concepts.

Practice using these methods to become proficient in JavaScript development.