---
---
Here at Devexperts we're writing FE apps using *our own specific approach*  
This includes:
- reactive state management
- type-safe [[dependency injection]] 
- dump components development

Common architecture at Devex FE has the following terms:
- `Component` - React component
- `View-Model` (or VM) - a reactive state manager, holds reactive state ([[RxJS]] for example), controls the state, reacts on state changes from itself and other models provides API to read current state, change it or subscribe to observe the changes
- `Container` - clue between components and view-models, used to gather state information from different VM's and pass it as props to components

Let's cover each topic in more details
# Reactive state manager
describe VM's with reactive state
# Type-safe Dependency Injection
describe context framework as an addon to reactive state

# Dumb components
Components should be **stupid** and **replaceable**  
We want to [[Coupling|de-couple]] components from business-logic and develop them independently in a sandbox environment such as [[storybook]]
> This approach is also called [jamstack](https://jamstack.org/)

Ready components can then be connected to your application via [[React]] props

