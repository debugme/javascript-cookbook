```js
const stringData = ", mladen, asad, robin,  ben,roger, ardit  ,   alexis,  ,"
const actualList = stringData.split(',').map(v => v.trim()).filter(v => v)
const expectList = ["mladen", "asad", "robin", "ben", "roger", "ardit", "alexis"]

expect(actualList).toEqual(expectList)
```



