```js
// How to colour text in the Browser Console
const colour  = 'color:red'
const message = 'hello world' 
console.log(`%c ${message}`, colour)

// How to colour text in the Server Console
const colour  = '\x1b[31m'
const message = 'hello world' 
console.log(`${colour} ${message}`)
```



