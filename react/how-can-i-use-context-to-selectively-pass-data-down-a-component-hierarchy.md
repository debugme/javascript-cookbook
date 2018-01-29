```js
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Chapter extends Component {
  static childContextTypes = {
    pageTitle: PropTypes.string.isRequired,        // (1) Define a `pageTitle` to add to context
    paragraphTitle: PropTypes.string.isRequired    // (2) Define a `paragraphTitle` to add to context
  }
  getChildContext = () => ({
      pageTitle: 'page title',                     // (3) Add `pageTitle` to context
      paragraphTitle: 'paragraph title'            // (4) Add `paragraphTitle` to context

  })
  render = () => <Page /> 
}
```

```jsx
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Page extends Component {
  static contextTypes = {
    pageTitle: PropTypes.string.isRequired         // (5) Expose `pageTitle` only to this component
  }
  constructor(props, context) {
    super(props)
    console.log('[x] context', context)            // (6) Context will only have `pageTitle` on it
  }
  render = () => {
    console.log('[x] this.context', this.context)  // (7) Context will only have `pageTitle` on it
    return <Paragraph />
  }  
}
```

```jsx
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Paragraph extends Component {
  static contextTypes = {
    paragraphTitle: PropTypes.string.isRequired   // (5) Expose `paragraphTitle` only to this component
  }
  constructor(props, context) {
    super(props)
    console.log('[x] context', context)           // (6) Access context from constructor
  }
  render = () => {
    console.log('[x] this.context', this.context) // (7) Access context from method
    return <p>'All Done'</p>
  }  
}
```

The _context_ object passed into _Page_, will only have _pageTitle_ on it.

The _context_ object passed into _Paragraph_, will only have _paragraphTitle_ on it.

