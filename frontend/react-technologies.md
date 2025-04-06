# React technologies

## Component library

Using a component library as a baseline rather than building everything from the ground up is generally a good idea in order to ship faster. Here are some good ones:

- Shadcn components
- Material UI
- Tailwind UI

## Styling

As of 2025, the two ways of doing styling that are emerging as the standard are:

- Using Tailwind
- Using css modules directly

See: <https://alexkondov.com/full-stack-tao-styling/>

## State management

### Remote state

Remote state is accessed through a port/infrastructure architecture, with react-query being used to manage the
associated meta-state (isPending, isLoading, etc.)

### Local / shared state

Valtio proxies are used to manage local state
