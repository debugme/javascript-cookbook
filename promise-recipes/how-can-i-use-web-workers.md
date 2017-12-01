```html
<!-- index.html -->
<html>
  <head>
    <script>
      const worker = new Worker('worker.js')
    </script>
  </head>
</html>
```

```js
// worker.js
this.addEventListener('message', (event) => {
    console.log(`${event.data}`)
})
this.postMessage()
```



