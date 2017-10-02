```js
// Define an array of values
const array = [ true, false, -1, 0, 1, 2.0, [], {}, '', ' ', 'a']
console.log('array contains ', array)

// Define an identity function
const identity = item => item

// Filter out falsey values
const items = array.filter(identity)
console.log('items contain ', items)
```



