```js
// Define a function that builds an object with computed property names
const build = (nameKey, nameVal, titleKey, titleVal) => ({[nameKey]: nameVal, [titleKey]: titleVal})

// Define a function that pretty-prints an object
const format = (data) => JSON.stringify(data, null, 2)

// Create objects with computed property names
const ukObject = build('forename', 'henry', 'salutation', 'mr')
const usObject = build('firstname', 'david', 'title', 'mr')

// Format the created objects
const ukFormat = format(ukObject)
const usFormat = format(usObject)

// Print out the formatted objects
console.log(ukFormat)
console.log(usFormat)
```



