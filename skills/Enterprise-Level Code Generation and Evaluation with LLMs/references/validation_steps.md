# Validation Steps

## Unit Tests

Run unit tests to validate the functionality of the generated code.

```bash
mvn test
```

## Integration Tests

Run integration tests to ensure the code works well with other components.

```bash
mvn integration-test
```

## Security Tests

Perform security tests to identify and fix vulnerabilities.

```bash
sonar-scanner -Dsonar.projectKey=my_project -Dsonar.sources=.
```

## Code Review

Conduct code reviews to ensure the generated code meets enterprise standards.

For more on core concepts and practical guidelines, refer to [Core Concepts](references/core_concepts.md) and [Practical Guide](references/practical_guide.md).