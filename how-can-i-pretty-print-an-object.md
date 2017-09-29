```js
// Define an object with key-value pairs
const data = { a: 'ape', b: 'bat', d: { e: 'elephant' } }

// Define a pretty-printer function
const format = (data) => JSON.stringify(data, null, 2)

// Print the pretty version of your data
const pretty = format(data)
console.log(`data is ${pretty}`)
```



