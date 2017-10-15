```jsx
// Approach 1 - Prop names are different from prop values
const { first, last, prefix } = props
const fullname = <FullName firstName={first} lastName={last} title={prefix} />
```

```jsx
// Approach 2 - Prop names and values pair up but create repeated code
const { first: firstName, last: lastName, prefix: title } = props
const fullName = <FullName firstName={firstName} lastName={lastName} title={title} />
```

```jsx
// Approach 3 - Prop names and values are no longer repeated
const { first: firstName, last: lastName, prefix: title } = props
const fullName = <FullName {...{ firstName, lastName, title }} />
```



