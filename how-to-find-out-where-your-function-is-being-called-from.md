```js
// Define your functions
const c = () => console.log('called by', new Error().stack)
const b = () => c()
const a = () => b()

// Call the function
a()
```



