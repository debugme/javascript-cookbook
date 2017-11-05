```js
// ES5 Approach
const isNumber = (value) => typeof value === 'number' && !isNaN(value)
```

```js
// ES6 Approach
const isNumber = Number.isFinite(value)
```



