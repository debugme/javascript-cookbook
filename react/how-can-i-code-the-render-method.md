```jsx
// Approach1
const FullName = (props) => {
    const { firstName, lastName, title } = props    
    // Elided code...
}

const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    // High Complexity (Imperative Code)
    return ({ firstName && lastName && title && <FullName {...{firstName, lastName, title }}/> })
}
```

```jsx
// Approach2
const FullName = (props) => {
    const { firstName, lastName, title } = props    
    // Elided code...
}

const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    const isVisible = (firstName && lastName && title)
    // Medium Complexity (Hybrid Imperative + Declarative)
    return ({ isVisible && <FullName {...{firstName, lastName, title }}/> })
}
```

```jsx
// Approach3
const FullName = (props) => {
    const { firstName, lastName, title, isVisible } = props    
    if (!isVisible) return null
    // Elided code...
}

const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    const isVisible = (firstName && lastName && title)
    // Low Complexity (Declarative Code)
    return (<FullName {...{firstName, lastName, title, isVisible }}/>)
}
```



