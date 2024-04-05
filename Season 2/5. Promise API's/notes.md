## Promise.all, Promise.allSettled, Promise.race in JavaScript

These notes covers the concepts of Promise.all, Promise.allSettled, Promise.race, and Promise.any, along with code examples for better understanding.

### **Understanding Promises:**

- Promises are objects representing the eventual completion (or failure) of an asynchronous operation.
- Promises can be in three states: pending, fulfilled, or rejected.
- Once a promise settles (fulfilled or rejected), it stays in that state.

### **1. Promise.all**

- Takes an iterable (array) of promises as input.
- Waits for all promises in the input array to settle (resolve or reject).
- Returns a single promise that:
    - Resolves with an array containing the fulfilled values of all promises if all promises are successful.
    - Rejects with the reason of the first rejected promise if any promise in the input array gets rejected.

**Code Example:**

```javascript
// Promises with different resolution times
const p1 = new Promise(resolve => setTimeout(() => resolve('P1 success'), 3000));
const p2 = new Promise(resolve => setTimeout(() => resolve('P2 success'), 1000));
const p3 = new Promise(resolve => setTimeout(() => resolve('P3 success'), 2000));

// Using Promise.all
Promise.all([p1, p2, p3])
  .then(values => console.log(values)) 
  // Output: ["P1 success", "P2 success", "P3 success"] after 3 seconds
  .catch(err => console.error(err)); 
  // Rejects immediately if any promise is rejected
```

**Key Points about Promise.all:**

- Use `Promise.all` when you need to wait for all promises to complete and require the results from all of them.
- If any promise fails, `Promise.all` rejects immediately with the reason of the first failure.

### **2. Promise.allSettled**

- Similar to `Promise.all` but waits for all promises to settle (regardless of success or failure).
- Returns a promise that resolves with an array of objects.
- Each object represents the outcome of a promise in the input array and has two properties:
    - `status`: "fulfilled" or "rejected"
    - `value`: The resolved value (if fulfilled)
    - `reason`: Rejection reason (if rejected)

**Code Example (modified from previous example):**

```javascript
Promise.allSettled([p1, p2, p3])
  .then(results => {
    results.forEach(result => console.log(result));
  });

// Output:
//(after 3 seconds)
// { status: 'fulfilled', value: 'P1 success' } 
// { status: 'fulfilled', value: 'P2 success' } 
// { status: 'fulfilled', value: 'P3 success' } 
```

**Key Points about Promise.allSettled:**

- Use `Promise.allSettled` when you need the outcome (success or failure) of all promises, even if some fail.
- It provides more information about each promise's settlement compared to `Promise.all`.

### **3. Promise.race**

- Takes an iterable (array) of promises as input.
- Returns a promise that resolves or rejects as soon as one of the promises in the input array settles.
- Resolves with the value of the first settled promise (fulfilled or rejected).

**Code Example (using same promises):**

```javascript
Promise.race([p1, p2, p3])
  .then(value => console.log(value)) 
  // Output: "P2 success" (after 1 second)
  .catch(err => console.error(err));
```

**Key Points about Promise.race:**

- Use `Promise.race` when you only care about the result of the first promise to settle (win or lose).
- Useful in scenarios like loading content where you only need to display the first available data.

### **4. Promise.any**

- Takes an iterable (array) of promises as input.
- Waits for the first promise to resolve (success).
- Returns a promise that:
    - Resolves with the value of the first fulfilled promise.
    - Rejects with an `AggregateError` containing reasons for all rejections if all promises are rejected.

**Code Example:**

```javascript
const p1 = new Promise(resolve => setTimeout(() => resolve('P1 success'), 3000));
const p2 = new Promise(reject => setTimeout(() => reject('P2 failure'), 2000));
const p3 = new Promise(resolve => setTimeout(() => resolve('P3 success'),4000));

Promise.race([p1, p2, p3])
  .then(value => console.log(value)) // Output: "P1 success" (after 3 second)
  .catch(error => {
    if (error instanceof AggregateError) {
      console.error("All promises were rejected:", error);
      error.errors.forEach(err => console.error(err.message)); // Loop through individual errors
    } else {
      console.error("An error occurred:", error);
    }
  });
```

**Key Points about Promise.race:**

- Use Promise.any when you only need the result of the first resolved promise.
- If all promises in the input array are rejected, Promise.any rejects with an `AggregateError` object containing reasons for all rejections. This allows you to handle individual rejection reasons using a loop within the .catch callback.
