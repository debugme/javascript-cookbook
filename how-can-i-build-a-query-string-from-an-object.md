```js
// utils.js
const buildQueryString = (options) => {
  const names = Object.keys(options)
  const buildPair = (name) => `${name}=${options[name]}`
  const pairs = names.map(buildPair)
  const query = pairs.join('&')
  return query
}

export default buildQueryString
```

```js
// code.js 
import buildQueryString from './utils'

const options = {
    a: 'ape',
    b: 'bat',
    c: 'cat'
}

const query = buildQueryString(options)
console.assert(query === 'a=ape&b=bat&c=cat')
```



