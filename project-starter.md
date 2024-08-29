# Project starter guide

A practical guide to initialize a new project and setup tooling using best-practices.

## Project initialization

- Use the appropriate Nx generator to create your project

## Framework-agnostic steps

### Code style

- Use Prettier. See attached `.prettierrc` file. Recommended .prettierrc configuration:

```json
{
  "printWidth": 120,
  "endingPosition": "absolute",
  "singleQuote": true,
  "plugins": ["prettier-plugin-tailwindcss", "prettier-plugin-classnames"]
}
```
- Use ESLint. Recommended overrides:

```json
{
  "rules": {
    "@typescript-eslint/no-use-before-define": "off"
  }
}
```

- See `style.md` for code style guidelines

### IDE (Webstorm)
- Enable `run eslint --fix on save`
- Enable `run prettier on save`

## Frontend (React)

### CSS

- Initialize TailwindCSS
- Add a theme file. See `colors.md` for more details.

### State management

- Use Zustand or Valtio for reactive state management
- Use Tanstack Query for data fetching and server synchronization

### REST APIs
- Use `openapi-typescript` and `openapi-fetch` to get a type-safe API client

### Testing

- Use Playwright for end-to-end and component testing
- Use vitest for unit testing

## Backend

### Web framework

- Use NestJS as a framework
- Setup Swagger for API documentation: add  the following line to webpack.config.js in NxWebpackPlugin options: `transformers: ['@nestjs/swagger/plugin']`
- Respect Zalando's [API First principles](https://opensource.zalando.com/restful-api-guidelines/)

### Persistence

- Default to Postgres
- Consider event sourcing and CQRS

### Testing

- Use jest over vitest for compatibility with Nest.

## Deployment

### CI

- Use GitHub Actions for CI

### IaC

- Use Pulumi for IaC

## Project structure

See `project-structure.md` for more details about organizing your codebase.
