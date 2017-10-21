```jsx
// Approach 1 - Complex logic for conditional rendering in-situ with JSX fragment
const FullName = (props) => {
    const { firstName, lastName, title } = props    
    // Elided code...
}

const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    // High Complexity
    return ({ firstName && lastName && title && <FullName {...{firstName, lastName, title }}/> })
}
```

```jsx
// Approach 2 - Simple logic for conditional rendering in-situ with JSX fragment
const FullName = (props) => {
    const { firstName, lastName, title } = props    
    // Elided code...
}

const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    const isVisible = (firstName && lastName && title)
    // Medium Complexity
    return ({ isVisible && <FullName {...{firstName, lastName, title }}/> })
}
```

```jsx
// Approach 3 - Logic for conditional rendering passed into JSX fragment
const FullName = (props) => {
    const { firstName, lastName, title, isVisible } = props    
    if (!isVisible) return null
    // Elided code...
}

const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    const isVisible = (firstName && lastName && title)
    // Low Complexity
    return (<FullName {...{firstName, lastName, title, isVisible }}/>)
}
```



