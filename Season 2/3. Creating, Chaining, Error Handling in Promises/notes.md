
Promise Chaining
======================

Introduction to Promises
------------------------

A promise is an object representing the eventual completion or failure of an asynchronous operation. It allows handling asynchronous operations in a more readable and manageable way.

Creating a Promise
------------------

A promise is created using the Promise constructor. It takes a function with two parameters: resolve and reject. Resolve is called when the asynchronous operation is successful, and reject is called when it fails.

 ```javascript   
    const promise = new Promise((resolve, reject) => {
      // Asynchronous operation
      if (/* operation successful */) {
        resolve(/* result */);
      } else {
        reject(/* error */);
      }
    });
```   

Handling Promise Errors
-----------------------

Errors in promises are handled using the `catch` method. It allows gracefully handling errors that occur during asynchronous operations.

```javascript  
    promise.catch(error => {
      console.error(error);
    });
```   

Promise Chaining
----------------

Promise chaining is a technique used to perform multiple asynchronous operations sequentially. It involves chaining `then` methods to handle the results of each operation.

 ```javascript    
    promise
      .then(result => {
        // Handle result of the first operation
        return /* result */;
      })
      .then(result => {
        // Handle result of the second operation
        return /* result */;
      })
      .catch(error => {
        // Handle errors in any operation
        console.error(error);
      });
```  

Advanced Promise Chaining
-------------------------

In complex scenarios, multiple promises can be chained together. Each step in the chain returns a value or a promise, which is passed to the next step using the `return` keyword.

 ```javascript   
    promise
      .then(result => {
        // Perform some operation
        return /* result or new promise */;
      })
      .then(result => {
        // Perform another operation
        return /* result or new promise */;
      })
      .catch(error => {
        // Handle errors in any operation
        console.error(error);
      });
```

Example: E-commerce Operations
------------------------------

Consider an example of an e-commerce website with multiple asynchronous operations: create order, proceed to payment, show order summary, and update wallet balance. These operations can be chained together using promises.

```javascript
    createOrder()
      .then(orderId => proceedToPayment(orderId))
      .then(paymentInfo => showOrderSummary(paymentInfo))
      .then(() => updateWalletBalance())
      .catch(error => {
        console.error(error);
      });
```   

Conclusion
----------

Promise chaining is a powerful technique for managing asynchronous operations in JavaScript. It allows writing cleaner, more maintainable code and simplifies error handling in asynchronous workflows.