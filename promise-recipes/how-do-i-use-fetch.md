```js
const url = 'https://swapi.co/api/people/5'

const onValidate = (response) => {
    if (response.ok) 
        return response
    throw new Error(response.status)
}

const onSuccess = (response) => response.json()

const onFailure = (error) => console.log(`error: ${error}`)
```

```js
fetch(url)
    .then(onValidate)
    .then(onSuccess)
    .catch(onFailure)
```





