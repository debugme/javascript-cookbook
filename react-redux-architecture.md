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
const LogIn = (props) => {
  const { text, onClick } = props
  return <button onClick={onClick}>{text}</button>
}
const mapStateToProps = (state) => ({ text: state.text })
const mapDispatchToProps = (dispatch, props) => ({
  onClick: () => dispatch({ type: 'LOGIN'})
})
export default connect(mapStateToProps, mapDispatchToProps)(LogIn)
```

```js
// Index.js
import React from 'react'
import ReactDOM from 'react-dom'
import { Provider } from 'react-redux'
import { createStore } from 'redux'

import rootReducer from './rootReducer'
import UserName from './Username'

const store = createStore(rootReducer)

const application = () => (
  <Provider store={store}>  
    <Username />
  </Provider>  
)
const mountNode = document.querySelector('#root')
ReactDom.render(application, mountNode)
```





