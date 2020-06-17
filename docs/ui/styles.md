# Styles Writing Convention

## General

### Class Names


## BEM
- We use BEM
- Naming format blockName_elementName__firstMofifierName__secondModifiername
- According to [General Convention](/docs/conventions.md) we use camelCase notation for class names
- According to [General Convention](/docs/conventions.md) we always use _ (underscore) as a separator and do not use - (minus sign)
- We use _ (single underscore) to split block and element
- We use __ (double underescore) to split modifiers
- We only use boolean modifiers and never user modifier_value

## Properties Order

## [Nesting](#nesting)
- When writing LESS styles only one level of nesting is allowd.
- Nesting styles is allowed only for the modificators

Bad
```
.box {
  &_header {
    &_subheader {
    
    }
  }
  &__red {
  
  }
}
```

Good
```
.box {
  // box styles
  &__red {}
  &__green {}
}

.box_header {}

.box_header_subheader {}
```

## Mixins And Functions
