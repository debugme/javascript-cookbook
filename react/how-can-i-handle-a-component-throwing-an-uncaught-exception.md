```js
import { Component } from 'react'

import Logger from '../../helpers/Logger'

class ErrorBoundary extends Component {
  constructor(props) {
    super(props)
    this.state = { hasError: false }
    this.logger = Logger.getInstance()
  }

  componentDidCatch(error, information) {
    try {
      this.setState({ hasError: true })
      this.logger.error('ErrorBoundary', { error, information }, 'Error')
    } catch (problem) {
      // Just incase the try block throws an exception!
    }
  }

  render() {
    const { children } = this.props
    const { hasError } = this.state
    if (hasError) {
      return null
    }
    return children
  }
}

export default ErrorBoundary
```

```js
const App = () => {
    return (
        <Errorr>
    )
}
```



