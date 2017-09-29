```js
const build = (nameKey, nameVal, titleKey, titleVal) => 
  ({
    [nameKey]: nameVal,
    [titleKey]: titleVal   
  })

const format = (data) => JSON.stringify(data, null, 2)
  
const ukObject = build('forename', 'henry', 'salutation', 'mr')
const usObject = build('firstname', 'david', 'title', 'mr')

const ukFormat = format(ukObject)
const usFormat = format(usObject)

console.log(ukFormat)
console.log(usFormat)
```



