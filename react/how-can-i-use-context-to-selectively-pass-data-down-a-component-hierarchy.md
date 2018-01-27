```jsx
// ------------------------------------------
//      ADD VALUES ONTO CONTEXT HERE
// ------------------------------------------
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { connect } from 'react-redux'
import Form from './form.component'

class FormContainer extends Component {
  // (1) Define keys to be added onto context
  static childContextTypes = {
    ape: PropTypes.string.isRequired,
    bat: PropTypes.string.isRequired
  }
  // (2) Define data to be added onto context
  getChildContext = () => ({
    ape: 'ape',
    bat: 'bat'
  })
  render () => <Form {...this.props} />
}

export default connect()(FormContainer)
```

```jsx

```



