```js
// Approach1: How to conditionally add key-value pairs into an object
const a = {}
const x = 'happy'
const y = undefined
if (x) {
  a[x] = x
}
if (y) {
  a[y] = y
}
console.log('The value of a is ', a)

// Approach2: How to conditionally add key-value pairs into an object
const p = 'happy'
const q = undefined
const b = { ...( p ? { p } : { } ), ...( q ? { q } : { } )}
console.log('The value of b is ', b)
```



