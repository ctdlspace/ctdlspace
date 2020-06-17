# React Coding Convention

## Components Naming
- exportable components are real functions — becouse this way React show components name in the inspector

```
export function Component(props) {
  const {} = props
  return (
    <div className="component">...</div>
  )
}

export function Component_subComponent(props) {
  const {} = props
  return (
    <div className="component_subComponent">...</div>
  )
}
```

## Composition

## Data Driven Components
