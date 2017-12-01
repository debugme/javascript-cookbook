```js
// A function with typical error checking for undefined argument being passed in
toLowerCase: (array) => {
  if (typeof array !== 'undefined') {
    return array.map(item => item.toLowerCase())
  }
  return []
}

// A function that uses default value to check for undefined arguments being passed in
toLowerCase: (array = []) => array.map(item => item.toLowerCase())
```



