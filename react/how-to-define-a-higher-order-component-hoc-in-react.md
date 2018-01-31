```jsx
// randomRGBColor.js
const randomRGBColor = () => {
    const makeColor = () => parseInt(Math.random() * 255, 10)
    const colorList = [,,,].fill().map(makeColor)
    const colorData = colorList.join(',')
    return colorData
}

export default randomRGBColor
```

```jsx
import React, { Component } from 'react'

const withChameleon = (Tag) => {
    return class extends Component {
        onClick(event){
            this.style = randomRGBColor()
        }
        render = () => <Tag {..this.props, onClick: this.onClick} />
    }
}
```

```jsx
import React, { Component } from 'react'

class Headline extends Component {
    render() {
        const onClick = this.props.onClick.bind(this)
        return <h1 onClick={onClick}>Headline Goes In Here</h1>
    }
}
```



