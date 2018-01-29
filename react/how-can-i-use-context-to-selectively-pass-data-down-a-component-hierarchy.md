```jsx
// ------------------------------------------
//      ADD VALUES ONTO CONTEXT HERE
// ------------------------------------------
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import Header from './form.component'

class Page extends Component {
  // (1) Define keys to be added onto context
  static childContextTypes = {
    ape: PropTypes.string.isRequired,
    bat: PropTypes.string.isRequired
  }
  // (2) Define data to be added onto context
  getChildContext = () => ({
    ape: 'Ape',
    bat: 'Bat'
  })
  render () => <Header {...this.props} />
}

export default Page
```

```jsx
// ------------------------------------------
//      GET VALUES FROM CONTEXT HERE
// ------------------------------------------
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Header extends Component {
  // (3) We only want `bat` off of context, so context object will NOT have `ape` on it
  static contextTypes = {
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
    return <h1>hello world</h1>
  }
}

export default Header
```

```js
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Chapter extends Component {
  static childContextTypes = {
    pageTitle: PropTypes.string.isRequired,
    paragraphTitle: PropTypes.string.isRequired
  }
  getChildContext = () => ({
      pageTitle: 'page title',
      paragraphTitle: 'paragraph title'      
  })
  render = () => <Page /> 
}
```

```jsx
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Page extends Component {
  static contextTypes = {
    pageTitle: PropTypes.string.isRequired
  }
  constructor(props, context) {
    super(props)
    console.log('[x] context', context)
  }
  render = () => {
    console.log('[x] this.context', this.context)
    return <Paragraph />
  }  
}
```



