```js
// rootReducer.js
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
```

```js
// LogIn.jsx
import React from 'react'
import { connect } from 'react-redux'
import { bindActionCreators } = 'redux'

// (1) Define the component
const LogIn = (props) => {
  const { text, onClick } = props
  return <button onClick={onClick}>{text}</button>
}

// (2) Define values to be made available on props
const mapStateToProps = (state) => ({ text: state.text })

// (3) Define functions to be made available on props
const mapDispatchToProps = (dispatch, props) => {
  // Approach 1
  // const onClick = () => dispatch({ type: 'LOGIN'})
  // const props = { onClick }
  // return props

  // Approach 2
  const onClick = () => ({ type: 'LOGIN'})
  const actionCreators = { onClick }
  const props = bindActionCreators(actionCreators, dispatch)
  return props
}

// (4) Wire-up the component with the state of the whole application
export default connect(mapStateToProps, mapDispatchToProps)(LogIn)
```

```js
// Index.js
import React from 'react'
import ReactDOM from 'react-dom'
import { Provider } from 'react-redux'
import { createStore } from 'redux'

import UserName from './Username'
import rootReducer from './rootReducer'

// Connect your application to Redux
const initialState = {}
const store = createStore(rootReducer, initialState)
const application = () => (
  <Provider store={store}>
    <Username />
  </Provider>  
)

// Define where to mount your application
const mountNode = document.querySelector('#root')

// Mount your application in the DOM tree
ReactDom.render(application, mountNode)
```



