```js
// Define the data object you want to clone
const data = { a: 'ape', b: 'bat', c: { d: 'dog' } }
console.log('The data is ', data)

// Define a clone function based on the JSON object
const clone = (data) => JSON.parse(JSON.stringify(data))

// Use the clone function to make a deep copy of the data
const copy = clone(data))
console.log('The copy is ', copy)
```



