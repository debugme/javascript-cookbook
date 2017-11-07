```js
function* rangeGenerator(from, upto, step = 1) {
  for (let index = from; index < upto; index += step) {
    yield index
  }
}

let range = rangeGenerator(0, 10)

for (let value of range) {
  console.log(`value is ${value}`)
}
```



