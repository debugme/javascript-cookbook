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

// (2) Define props to pass into component
const mapStateToProps = (state) => ({ text: state.text })

// (3) Define store dispatches to pass into component
const mapDispatchToProps = (dispatch, props) => {
  // Approach 1
  // const props = {
  //   onClick: () => dispatch({ type: 'LOGIN'})
  // }
  // return props
  
  // Approach 2
  
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



