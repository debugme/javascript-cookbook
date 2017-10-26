```js
const url = 'http://random.cat/meow'

const onSuccess = (response) => {
  return console.log(response.data)
}

const onFailure = (error) => {
  if (error.response)
    return console.log(`Error in response ${error.response.status}`)
  if (error.request)
    return consolee.log('Error in request ${url}')
  return console.log(`Error in another place ${error.message}`)
}
```

```js
axios.get(url)
  .then((response) => console.log(response.data))
  .catch((error) => console.log(error))
```



