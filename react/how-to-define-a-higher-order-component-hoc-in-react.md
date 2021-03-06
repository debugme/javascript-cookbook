```jsx
const getRGBColor = () => parseInt(Math.random() * 255, 10)
const randomColor = () => [,,,].fill().map(getRGBColor).join(',')

export default randomColor
```

```jsx
import React, { Component } from 'react'

import randomColor from './randomColor'

const withColor = (Tag) => {
  class WithColor extends Component {
    changeColor () {
      const color = randomColor()
      const backgroundColor = randomColor()
      this.style = { color, backgroundColor }
    }
    render = () => {
      const { changeColor } = this
      const props = {...this.props, changeColor }
      return <Tag {...props} />
    }
  }
  const { displayName, name } = Tag  
  const tagName = (displayName || name || 'Component')
  WithColor.displayName = `WithColor(${tagName})`
  return WithColor
}

export default withColor
```

```jsx
import React from 'react'

const HeaderOne = (props) => {
  const { changeColor } = props
  const onClick = changeColor.bind(this)
  return <h1 onClick={onClick}}>H1</h1>
}

export default HeaderOne
```

```jsx
import React from 'react'

const HeaderTwo = (props) => {
  const { changeColor } = props
  const onClick = changeColor.bind(this)
  return <h1 onClick={onClick}}>H2</h1>
}

export default HeaderTwo
```

```jsx
import React from 'react'

// NOTE: https://reactjs.org/docs/higher-order-components.html#dont-use-hocs-inside-the-render-method
const ColorHeaderOne = withColor(HeaderOne)
const ColorHeaderTwo = withColor(HeaderTwo)

const Application = (props) => (
  <Fragment>
    <ColorHeaderOne {...props} />
    <ColorHeaderTwo {...props} />
  </Fragment>
)
```



