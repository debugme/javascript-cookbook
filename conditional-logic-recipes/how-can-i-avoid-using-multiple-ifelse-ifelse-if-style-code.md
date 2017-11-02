```js
// Data is mixed up with conditional logic
function createStudent(info){
  const { likesJavaScript = false, likesES2015 = false } = info
  if (likesJavaScript && likesES2015) {
    return 'The student likes JavaScript and ES2015!'
  }
  if (likesJavaScript && !likesES2015) {
    return 'The student likes JavaScript!'
  }
  if (!likesJavaScript && likesES2015) {
    return 'The student likes ES2015!'
  }  
  return 'The student does not like much...'
}


```

```js
// Data is separated from conditional logic
const lookUpMap = {
  'true:true': 'The student likes JavaScript and ES2015!',
  'true:false': 'The student likes JavaScript!',
  'false:true': 'The student likes ES2015!',
  'false:false': 'The student does not like much...'
}

function createStudent(info){
  const { likesJavaScript = false, likesES2015 = false } = info
  const lookUpKey = `${likesJavaScript}:${likesES2015}`
  const result = lookUpMap[lookUpKey]
  return result
}
```



