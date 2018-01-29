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
    console.log('[x] context', context)           // (6) Context will only have `paragraphTitle` on it
  }
  render = () => {
    console.log('[x] this.context', this.context) // (7) Context will only have `paragraphTitle` on it
    return <p>'All Done'</p>
  }  
}
```

The `context` object passed into `Chapter` will have `pageTitle` and `paragraphTitle` added to it

The `context` object passed into `Page` will only contain \`pageTitle\` on it.

The `context` object passed into `Paragraph` will only contain `paragraphTitle` on it.

