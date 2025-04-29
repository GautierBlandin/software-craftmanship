# useEffect Guidelines

This doc is a copy-pasted reddit comment: <https://www.reddit.com/r/reactjs/comments/1k9713j/comment/mpc13v3/>

## Content

The core rules I follow with useEffect:

- eslint-plugin-react-hooks must be fully enabled, reporting issues as errors.
- The implementer is fully aware of this https://react.dev/learn/you-might-not-need-an-effect documentation and their use case does not have an obvious workaround based on those docs.
- The implementer is not using useEffect to make API calls (use a lib like tanstack-query or RTK query instead)
- The useEffect is not trying to respond to changes in the application core domain. It is truly something localized to some Component, or is a genuine React “escape hatch” integrating with some external system

After all of the above have been checked off and it is established that useEffect really is the best option,

- useEffect never goes directly in a component. Instead it is wrapped by a custom hook with a legible name
- The custom hook is kept compact and in its documentation clearly explains why it was deemed the effect was necessary
