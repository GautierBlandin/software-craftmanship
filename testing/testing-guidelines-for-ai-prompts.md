# Testing Guidelines for AI Code Generation

When writing tests, follow these key principles:

## Test Structure
- Always write the smallest test possible for the behavior being tested
- Structure tests with clear "Given", "When", "Then" sections
- Name tests after the specific behavior being tested, not the method
- Write clear failure messages that explain what went wrong
- Test behaviors, not methods - a single method may require multiple tests

## Test Scope and Size
- Prefer small tests (single process) over medium (single machine) or large tests (distributed)
- Small tests should have no I/O operations, no sleeping, and no blocking calls
- Follow the 80/15/5 ratio: 80% unit tests, 15% integration tests, 5% end-to-end tests

## Test Quality
- Make tests complete: include all information needed to understand how it arrives at its result
- Make tests concise: exclude distracting or irrelevant information
- Tests should be hermetic: assume as little as possible about the outside environment
- Tests should be obvious: contain only the information required to exercise the behavior
- Avoid flaky tests at all costs - they destroy confidence in the test suite

## Test API Boundaries
- Test via public APIs rather than implementation details
- Test state, not interactions - focus on what the result is, not how it was achieved
- Tests should rarely need to change unless requirements change

## Test Logic and Sharing
- Don't put logic in tests - tests should be trivially correct upon inspection
- Follow DAMP (Descriptive And Meaningful Phrases) over DRY for test code
- Use shared setup appropriately for constructing objects under test
- Avoid harmful sharing: tests depending on specific values in shared setup
- Use helper methods that clearly define what's relevant for the test

## Test Maintenance
- Tests should not break during pure refactorings
- Only add tests for new features, don't modify existing tests
- For bug fixes, add tests to cover the missing case without modifying existing tests
- Only modify tests when behavior intentionally changes
