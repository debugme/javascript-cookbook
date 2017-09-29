```js
const parse = (constants, ...variables) => ({ constants, variables })

const john = 'Jonathan'
const resultOne = parse(`Hello, ${john}. Nice name, ${john}.`)
console.log(`The result for ${john} is `, resultOne)

const bill = 'William'
const resultTwo = parse`Goodbye, ${bill}. Cool name, ${bill}.`
console.log(`The result for ${bill} is `, resultTwo)
```



