# Process

What is time-consuming when developing software is hesitation. The bottleneck of software development is the discovery of requirements,
and hesitation when writing implementation. A good process should enable the developer to avoid having to hesitate, and separate the
different concerns of the software development process.

Here is the gist of it:

```mermaid
graph LR

Green[Test Passes] --1. Write a failing test \n to drive the implementation--> Red[Test Fails]
Red --2. Write minimal \n implementation code-->Green
Green --3. Refactor implementation \n and tests--> Green

style Red fill:#DC143C,stroke:#DC143C
style Green fill:#50C878,stroke:#50C878
```

## Some heuristics

- Defer naming when writing tests. We may throw them away.
- Be in good faith when writing the tests, and in bad faith when writing the solution
- Limit your bad faith to three occurrences
- Start by writing the tests and the solution in the same file
- Use tests as field notes of your understanding of the problem

## Concerns to separate

- Documenting your understanding of the problem
- Having a first naive solution
- Having a first good design
- Having a first good solution
- Performance

## What is a test?

- A test is a question about the domain
- A test helps archeologists to understand the code, it is documentation
- A test is a safety net that prevents breakage when we change things

## Why TDD?

- Liberating your mind from holding your understanding of the problem
- Reasoning about the problem
- Trusting the system you are building

## References:
- https://www.youtube.com/watch?v=kDfuP88hVgU
- https://www.youtube.com/watch?v=QVpu19o6TsU
