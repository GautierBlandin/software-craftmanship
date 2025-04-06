# Use-cases

Use-cases represent workflows that the application is capable of performing.

Here is how a use-case file is structured:

```ts
interface UseCaseNameInput {
  // Input parameters for the use-case
}

interface UseCaseNameOutput {
  // Output parameters for the use-case
}

export class UseCaseName {
  async execute(input: UseCaseNameInput): Promise<UseCaseNameOutput> {
    // Implementation of the use-case
  }
}
```
