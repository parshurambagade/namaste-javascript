
Promise APIs
=========================

1\. Introduction to Promises
----------------------------

Promises are a fundamental part of JavaScript asynchronous programming. They represent a value that may be available now, or in the future, or never.

A promise can be in one of the following states:

*   **Pending:** Initial state, neither fulfilled nor rejected.
*   **Fulfilled:** The operation completed successfully.
*   **Rejected:** The operation failed.

2\. Promise.all
---------------

`Promise.all` takes an array of promises and returns a single promise that resolves when all of the promises in the array have resolved, or rejects with the reason of the first promise that rejects.

Example:

    
            const p1 = new Promise(resolve => setTimeout(resolve, 3000, 'P1 Success'));
            const p2 = new Promise(resolve => setTimeout(resolve, 1000, 'P2 Success'));
            const p3 = new Promise((resolve, reject) => setTimeout(reject, 2000, 'P3 Failure'));
    
            Promise.all([p1, p2, p3])
                .then(results => console.log(results))
                .catch(error => console.error(error));
        

**Explanation:** In this example, we create three promises (`p1`, `p2`, `p3`) using `setTimeout` to simulate asynchronous operations. We then use `Promise.all` to wait for all promises to resolve. The `then` block logs the results if all promises are resolved, and the `catch` block logs the first rejection reason if any promise is rejected.

3\. Promise.allSettled
----------------------

`Promise.allSettled` waits for all promises to be settled (either fulfilled or rejected) and returns a promise that resolves after all of the given promises have either resolved or rejected.

Example:

    
            Promise.allSettled([p1, p2, p3])
                .then(results => console.log(results))
                .catch(error => console.error(error));
        

**Explanation:** Similar to `Promise.all`, this example waits for all promises to settle. The `then` block logs the results, including the status (fulfilled or rejected) and value/reason of each promise. The `catch` block handles any errors that occur.

4\. Promise.race
----------------

`Promise.race` returns a promise that resolves or rejects as soon as one of the promises in the iterable resolves or rejects, with the value or reason from that promise.

Example:

    
            Promise.race([p1, p2, p3])
                .then(result => console.log(result))
                .catch(error => console.error(error));
        

**Explanation:** This example demonstrates how `Promise.race` resolves with the first settled promise (either fulfilled or rejected). The `then` block logs the result of the first settled promise, while the `catch` block handles any errors.

5\. Promise.any
---------------

`Promise.any` takes an iterable of Promise objects and, as soon as one of the promises in the iterable fulfills, returns a single promise that resolves with the value from that promise.

Example:

    
            Promise.any([p1, p2, p3])
                .then(result => console.log(result))
                .catch(errors => console.error('All promises were rejected', errors));
        

**Explanation:** Here, `Promise.any` resolves with the first fulfilled promise. If all promises are rejected, it returns an `AggregateError` containing the rejection reasons of all the promises. The `then` block logs the result of the first fulfilled promise, while the `catch` block handles the case where all promises are rejected.

Conclusion
----------

Understanding Promise APIs is crucial for handling asynchronous operations in JavaScript. By mastering these APIs, developers can effectively manage and coordinate multiple asynchronous tasks, leading to more efficient and reliable code.

Remember to practice writing and using promises in various scenarios to solidify your understanding and improve your programming skills.