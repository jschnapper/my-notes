# React Styling 

[A Talk on React Styling](https://www.styled-components.com/docs/basics)

**Containers:** How things work

**Components:** How things look

## Best Practices
**Single-Use Classes**
* A class name for a specific component would not be used anywhere else except for a specific component
* Example: A style for button would only be used for 

**Using Components as a Styling Construct**
* Styling built-in to the component 
* Not using specific class names but using the component itself
* Example: Rather than a grid class, have a grid component

## Styled-Components 
* Write actual CSS in js
* Adapt based on props through interpolating functions 
* Allows for custom theming
  * Based on the context in which a component is rendered, it will have a certain styling
