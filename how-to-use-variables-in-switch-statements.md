```js
// Approach1: Use Nested Ternaries
const normaliseEndpoint = (endpoint) => {
  const trim = endpoint.trim()
  const trimLowerCase = trim.toLowerCase()
  return trimLowerCase.startsWith('http://')
    ? trim.slice(5)
    : trimLowerCase.startsWith('https://')
    ? trim.slice(6)
    : !trimLowerCase.startsWith('//')
    ? `//${trim}`
    : trim
}

// Approach2: Use Variables In Switch Statements
const normaliseEndpoint = (endpoint) => {
  const trim = endpoint.trim()
  const trimLowerCase = trim.toLowerCase()
  switch(true) {
    case trimLowerCase.startsWith('http://'):
      return trim.slice(5)
    case trimLowerCase.startsWith('https://'):
      return trim.slice(6)
    case !trimLowerCase.startsWith('//'):
      return `//${trim}`
    default:
      return trim
  }
}
```



