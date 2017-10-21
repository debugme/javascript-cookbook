```jsx
import React from 'react'
import { BrowserRouter, Route } from 'react-router-dom'

// page and paragraph are mandatory parameters
// sentence is an optional parameter
// You can provide whatever you like for delimiter value

const getPath = () => {
  const parameters = [':page', ':paragraph', ':sentence?']
  const delimiter = ';'
  const path = `/${parameters.join(delimiter)}`
  return path
}

const render = (props) => {
  const { match: { params: { page, paragraph, sentence = '!' }}} = props
  const heading = `Page:${page} Paragraph:${paragraph} Sentence:${sentence}`
  return <h1>{heading}</h1>
}

const App = () => (
  <BrowserRouter>
    <div>
      <Route path={path} render={render} />
    </div>
  </BrowserRouter>
)

export default App
```



