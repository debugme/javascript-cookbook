```js
// Handles missing values and irregular whitespace
const tokenise = (s, d= ',') => s.split(d).map(v => v.trim()).filter(v => v)

const stringData = ", mladen, asad, robin,  ben,roger, ardit  ,   alexis,  ,"
const actualList = tokenise(stringData)
const expectList = ["mladen", "asad", "robin", "ben", "roger", "ardit", "alexis"]

expect(actualList).toEqual(expectList)
```



