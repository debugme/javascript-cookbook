```jsx
// (1) Define functions to generate pseudo-random RGB colors
const getRGBColor = () => parseInt(Math.random() * 255, 10)
const randomColor = () => [,,,].fill().map(getRGBColor).join(',')

export default randomColor
```

```jsx
// (2) Define a Higher Order Component that adds color changing
import React, { Component } from 'react'

import randomColor from './randomColor'

const withColor = (Tag) => {
  return class extends Component {
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
}

export default withColor
```

```jsx
import React from 'react'

const HeaderOne = ({ changeColor }) => <h1 onClick={changeColor.bind(this)}>H1</h1>

export default HeaderOne
```

```jsx
import React from 'react'

const HeaderTwo = ({ changeColor }) => <h2 onClick={changeColor.bind(this)}>H2</h2>

export default HeaderTwo
```

```jsx
import React from 'react'

// Do NOT define your HOC'd components in render() method!
// https://reactjs.org/docs/higher-order-components.html#dont-use-hocs-inside-the-render-method
const ColorHeaderOne = withColor(HeaderOne)
const ColorHeaderTwo = withColor(HeaderTwo)

const Application = (props) => (
  <Fragment>
    <ColorHeaderOne {...props} />
    <ColorHeaderTwo {...props} />        
  </Fragment>
)
```



