# Project starter guide

A practical and opinionated guide for setting up a full-stack monorepo.

## Project initialization

- Use the appropriate Nx generator to create your project

## Framework-agnostic steps

### Code style

- Use ESLint. Recommended overrides:

```json
{
  "rules": {
    "@typescript-eslint/no-use-before-define": "off"
  }
}
```

- Use Prettier. See attached `.prettierrc` file. Recommended .prettierrc configuration:

```json
{
  "printWidth": 120,
  "endingPosition": "absolute",
  "singleQuote": true
}
```

### IDE (Webstorm)
- Enable `run eslint --fix on save`
- Enable `run prettier on save`

## Frontend (React)

### CSS

- Use TailwindCSS
- Add a theme file. See `frontend/theming-colors.md` for more details.

### State management

- Use Zustand or Valtio for complex reactive state management
- Use Tanstack Query for data fetching and server synchronization

### REST APIs
- Use `openapi-typescript` and `openapi-fetch` to get a type-safe API client

### Testing

- Use Playwright for end-to-end testing
- Use vitest with react-testing-library for component testing
- Use vitest for unit testing

## Backend

### Framework

- Consider using NestJS

### Persistence

- Unless you have a very good justification for a different persistence system, [just use Postgres](https://mccue.dev/pages/8-16-24-just-use-postgres). If you need it serverless, you can use Neon Serverless Postgres.

## Deployment

### CI

- Use GitHub Actions for CI

### IaC

- Default to Pulumi, and consider SST if you are mostly using AWS Serverless.

## Project structure

See `backend/backend-project-structure.md` for more details about organizing your codebase.
