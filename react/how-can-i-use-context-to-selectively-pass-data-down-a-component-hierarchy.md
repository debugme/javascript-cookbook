```jsx
// ------------------------------------------
//      ADD VALUES ONTO CONTEXT HERE
// ------------------------------------------
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { connect } from 'react-redux'
import Form from './form.component'

class FormContainer extends Component {
  // (1) Define keys to be added onto global context
  static childContextTypes = {
    ape: PropTypes.string.isRequired,
    bat: PropTypes.string.isRequired
  }
  // (2) Define data to be added onto global context
  getChildContext = () => ({
    ape: 'ape',
    bat: 'bat'
  })
  render () => <Form {...this.props} />
}

export default connect()(FormContainer)
```

```jsx
// ------------------------------------------
//      GET VALUES FROM CONTEXT HERE
// ------------------------------------------
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Form extends Component {
  // (3) We only want `store` and `bat` off of context
  // So the context object will NOT have `ape` on it
  static contextTypes = {
    store: PropTypes.object.isRequired,
    bat: PropTypes.string.isRequired
  }
  constructor(props, context) {
    super(props)
    // (4) This is how you access `context` from a constructor
    console.log('[x] context', context)
  }
  render = () => {
    // (5) This is how you access `context` from a method
    console.log('[x] this.context', this.context)
    return <div></div>
  }
}

export default Form
```



