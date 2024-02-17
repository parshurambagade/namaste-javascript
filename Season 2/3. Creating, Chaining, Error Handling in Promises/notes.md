
Notes on Promise Chaining
=========================

Here, we learned about promise chaining and how to handle errors gracefully in JavaScript.

1\. Creating Promises
---------------------

We can create new promises using the `Promise` constructor. It takes a function with `resolve` and `reject` parameters. We can control whether the promise resolves or rejects within this function.

    
            const myPromise = new Promise((resolve, reject) => {
                // Logic here
                if (/* condition */) {
                    resolve(/* value */);
                } else {
                    reject(/* error */);
                }
            });
        

2\. Handling Errors with Catch
------------------------------

We can handle errors in promises using the `catch` method. This method is attached to the promise object and will catch any errors thrown in the chain.

    
            myPromise.catch(error => {
                // Handle error here
            });
        

3\. Promise Chaining
--------------------

We can chain promises by returning values or promises from `then` callbacks. This allows us to pass data between different asynchronous operations.

    
            myPromise
                .then(data => {
                    // Do something with data
                    return newData;
                })
                .then(newData => {
                    // Do something else
                })
                .catch(error => {
                    // Handle errors in the chain
                });
        

4\. Example: E-commerce Promise Chain
-------------------------------------

Suppose we have four APIs: `createOrder`, `proceedToPayment`, `showOrderSummary`, and `updateWalletBalance`. We can chain these promises to handle the e-commerce process.

    
            createOrder()
                .then(orderID => proceedToPayment(orderID))
                .then(paymentInfo => showOrderSummary(paymentInfo))
                .then(() => updateWalletBalance())
                .catch(error => {
                    // Handle errors in the chain
                });
        

By chaining promises, we can ensure a sequential flow of asynchronous operations and gracefully handle errors throughout the process.