```html
<!-- index.html -->
<html>
  <head>
    <script>
      const worker = new Worker('worker.js')
      console.log('master dispatches message to worker')
      worker.postMessage('a')
      console.log('master receives message from worker')
      worker.addEventListener('message', (event) => {
        console.log(`${event.data}`)
      })
    </script>
  </head>
</html>
```

```js
// worker.js
importScripts('helpers.js')

// worker listens for messages from master
this.addEventListener('message', (event) => {
    echo(`${event.data}`)
})

// worker dispatches message for master
this.postMessage('c')
```

```js
// helpers.js
const echo = (data) => console.log(data)
```



