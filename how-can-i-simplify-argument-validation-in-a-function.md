```js
// A function with typical error checking
toLowerCase: (array) => {
  if (typeof array !== 'undefined') {
    return array.map(item => item.toLowerCase())
  }
  return []
}

// A function that uses default value to eliminate error checking
toLowerCase: (array = []) => array.map(item => item.toLowerCase())
```



