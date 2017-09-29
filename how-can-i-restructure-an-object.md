```js
// Define an object with key-value pairs
const data = { a: 'ape', b: 'bat', d: { e: 'elephant' } }
console.log('The value of data is ', data)

// Pull out an individual key-value pair
const { a } = data
console.log(`The value of a is ${a}`)

// Rename the key when you pull out a key-value pair
const { b: animal } = data
console.log(`The value of animal is ${animal}`)

// Provide a default value if a key was not found
const { c = 'cat' } = data
console.log(`The value of c is ${c}`)

// Pull out a nested key-value pair
const { d: { e } } = data
console.log(`The value of e is ${e}`)
```



