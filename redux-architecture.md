```js
// How to install Redux as an application dependency
npm install redux --save


```

```js
import Redux from 'redux'

// (1) How to create a root reducer
const rootReducer = (state = {}, action) => {
  switch (action.type) {
    case 'LOGIN':
      return { ...state, loggedIn: true }
    case 'LOGOUT':
      return { ...state, loggedIn: false }      
    default:
      return state
  }
}

// (2) How to create a store associated with the root reducer
const store = Redux.createStore(rootReducer)

// (3) How to dispatch an action to the store
const action = { type: 'LOGIN' }
store.dispatch(action)

// (4) How to get the current  state of the store
const state = store.getState()

// (5) How to listen to changes to the store
const onChange = (store) => console.log('[onChange] ', store.getState())
const unsubscribe = store.listen(onChange)

// (6) How to stop listening to changes to the store
unsubscribe()
```



