```js
// Case 1: If a promise is resolved the THEN block is run
Promise.resolve(1)
  .then(value => console.log(`[case1] pass: ${value}`))
  .catch(error => console.log(`[case1] fail: ${error}`))

// Case 2: If a promise is rejected the CATCH block is run
Promise.reject(1)
  .then(value => console.log(`[case2] pass: ${value}`))
  .catch(error => console.log(`[case2] fail: ${error}`))

// Case 3: If all promises are resolved the THEN block is run
Promise.all([Promise.resolve(1), Promise.resolve(2)])
  .then(items => console.log(`[case3] pass: ${JSON.stringify(items)}`))
  .catch(error => console.log(`[case3] fail: ${error.toString()}`))

// Case 4: If all promises are rejected the CATCH block is run
Promise.all([Promise.reject(1), Promise.reject(2)])
  .then(items => console.log(`[case4] pass: ${JSON.stringify(items)}`))
  .catch(error => console.log(`[case4] fail: ${error.toString()}`))

// Case 5: If some promises are resolved and some are rejected the CATCH block is run
Promise.all([Promise.resolve(1), Promise.reject(2)])
  .then(items => console.log(`[case5] pass: ${JSON.stringify(items)}`))
  .catch(error => console.log(`[case5] fail: ${error.toString()}`))

// Case 6: If a chain of promises are all resolved the final THEN block is run
Promise.resolve(1)
  .then(data => Promise.resolve(data + 1))
  .then(data => Promise.resolve(data + 1))
  .then(data => Promise.resolve(data + 1))
  .then(data => console.log(`[case6] pass: ${JSON.stringify(data)}`))
  .catch(error => console.log(`[case6] fail: ${error.toString()}`))

// Case 7: If a chain of promises do not all resolve the CATCH block is run
Promise.resolve(1)
  .then(data => Promise.resolve(data + 1))
  .then(data => Promise.reject(data + 1))
  .then(data => Promise.resolve(data + 1))
  .then(data => console.log(`[case7] pass: ${JSON.stringify(data)}`))
  .catch(error => console.log(`[case7] fail: ${error.toString()}`))

// Case 8: How to avoid fail fast behaviour of Promise.all()
const request = async (data) => {
  try {
    if (data % 2 !== 0) throw new Error(`${data} not even`)
    return Promise.resolve({ value: data, valid: true })
  } catch (error) {
    return Promise.resolve({ value: error.toString(), valid: false })
  }
}

Promise
  .all([request(2), request(5), request(8)])
  .then(results => Promise.resolve(results.filter(({ valid }) => valid)))
  .then(answers => console.log(answers))
```



