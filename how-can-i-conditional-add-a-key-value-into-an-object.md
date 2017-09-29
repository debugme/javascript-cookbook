```js
// How to conditionally add a key-value pair into an object (Approach 1)
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

// How to conditionally add a key-value pair into an object (Approach 2)
let b = {}
const p = 'happy'
const q = undefined
b = { ...( p ? { p } : { } )}
b = { ...( q ? { q } : { } )}
console.log('The value of b is ', b)
```



