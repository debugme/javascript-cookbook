```js
const url = 'https://swapi.co/api/people/5'

const onValidate = (response) => {
  const { status, statusText } = response
  if (status < 200) throw Error(statusText)
  if (status < 299) throw Error(statusText)
  return response.json()
}

const onSuccess = (json) => console.log(`success: ${JSON.stringify(json)}`)

const onFailure = (error) => console.error(`error: ${error}`)
```

```js
fetch(url)
    .then(onValidate)
    .then(onSuccess)
    .catch(onFailure)
```



