```jsx
const asyncMiddleware = (store) => (next) => (action) => {

  // (1) Pull off all the data your code needs
  const { type, payload }
  const { meta, data } = payload
  const { isAsynch } = meta
  const { endoint } = data
  const { dispatch } = store

  // (2) Define a helper to pull JSON out of an AJAX response
  const onResponse = (payload) => {
    return payload.json()
  }

  // (3) Define a helper to dispatch a success action if AJAX request was a success
  const onSuccess = (payload) => {
    const type = type.replace('_REQUEST', '_SUCCESS') // e.g. 'FETCH_ITEMS_REQUEST' -> 'FETCH_ITEMS_SUCCESS'
    const action = { type, payload }
    dispatch(action)
  }

  // (4) Define a helper to dispatch a success action if AJAX request was a failure  
  const onFailure = (payload) => {
    const type = type.replace('_REQUEST', '_FAILURE') // e.g. 'FETCH_ITEMS_REQUEST' -> 'FETCH_ITEMS_FAILURE'    
    const action = { type, payload }
    dispatch(action)
  }  

  // (5) If action cannot be handled then pass action into the next middleware in chain
  if (!isAsync) {
    return next(action)
  }

  // (6) Process request and inject new action back into top of middleware chain
  return fetch(endpoint)
    .then(onResponse)
    .then(onSuccess)
    .catch(onFailure)    
}
```

**Open Questions**: 

1. As a rule should `payload` have both `metadata` and `data` ? It seems like a nice separation of concerns.



