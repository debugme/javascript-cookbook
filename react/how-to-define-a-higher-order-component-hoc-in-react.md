```jsx
// (1) Define functions to generate pseudo-random RGB colors
const makeColor = () => parseInt(Math.random() * 255, 10)

const randomRGBColor = () => {
    const colorList = [,,,].fill().map(makeColor)
    const colorData = colorList.join(',')
    return colorData
}

export default randomRGBColor
```

```jsx
// (2) Define a Higher Order Component that adds color changing
import React, { Component } from 'react'
import randomRGBColor from './randomRGBColor'

const withColor = (Tag) => {
    return class extends Component {
        changeColor(){
            this.style = { 
                color: randomRGBColor(),
                backgroundColor: randomRGBColor()
            }
        }
        render = () => {
            const { changeColor } = this
            const props = {...this.props, changeColor }
            return <Tag {..props} />
        }
    }
}

export default withColor
```

```jsx
import React from 'react'

const HeaderOne = (props) => {
    return <h1 onClick={props.changeColor.bind(this)}>HeaderOne Goes In Here</h1>
}

export default HeaderOne
```

```jsx
import React from 'react'

const HeaderTwo = (props) => {
    return <h2 onClick={props.changeColor.bind(this)}>HeaderTwo Goes In Here</h2>
}

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



