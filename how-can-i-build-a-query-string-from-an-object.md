```js
const buildQueryString = (options) => {
  const names = Object.keys(options)
  const buildPair = (name) => `${name}=${options[name]}`
  const pairs = names.map(buildPair)
  const query = pairs.join('&')
  return query
}

export default buildQueryString

```



