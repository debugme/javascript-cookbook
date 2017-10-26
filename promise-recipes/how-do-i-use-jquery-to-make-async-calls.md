```js
const url = 'http://random.cat/meow'
$.getJSON(url)
  .done((data) => console.log(`done: ${data}`))
  .fail(() => console.log('fail'))
    
```



