```js
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Chapter extends Component {
  static childContextTypes = {
    pageTitle: PropTypes.string.isRequired,      // (1) Add `pageTitle` to context
    paragraphTitle: PropTypes.string.isRequired  // (2) Add `paragraphTitle` to context
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

```jsx
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Paragraph extends Component {
  static contextTypes = {
    paragraphTitle: PropTypes.string.isRequired
  }
  constructor(props, context) {
    super(props)
    console.log('[x] context', context)
  }
  render = () => {
    console.log('[x] this.context', this.context)
    return <p>'All Done'</p>
  }  
}
```



