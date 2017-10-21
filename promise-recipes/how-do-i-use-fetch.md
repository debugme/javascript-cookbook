```js
const url = 'https://swapi.co/api/people/5'

const onValidate = (response) => {
    if (response.ok) 
        return response.json()
    throw new Error(response.status)
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



