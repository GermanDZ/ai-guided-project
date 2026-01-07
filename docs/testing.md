# Testing

> Testing strategy, conventions, and how to run tests.
>
> **Note**: This template is stack-agnostic. Examples below show common patterns—replace with your actual commands.

---

## Quick Reference

```bash
# JavaScript/TypeScript (Jest)
npm test                    # Run all tests
npm test -- --watch         # Watch mode
npm test -- --coverage      # With coverage

# JavaScript/TypeScript (Vitest)
npx vitest                  # Run all tests
npx vitest --watch          # Watch mode
npx vitest --coverage       # With coverage

# Python (pytest)
pytest                      # Run all tests
pytest --watch              # Watch mode (with pytest-watch)
pytest --cov                # With coverage

# Ruby (RSpec)
rspec                       # Run all tests
rspec --format documentation # Verbose output
rspec --coverage            # With coverage (SimpleCov)

# Go
go test ./...               # Run all tests
go test -v ./...            # Verbose
go test -cover ./...        # With coverage

# Rust
cargo test                  # Run all tests
cargo test -- --nocapture   # Show output
cargo tarpaulin             # With coverage

# Java (Maven)
mvn test                    # Run all tests
mvn test -Dtest=TestClass   # Specific test
mvn jacoco:report           # Coverage report

# Java (Gradle)
gradle test                 # Run all tests
gradle test --tests TestClass # Specific test
gradle jacocoTestReport     # Coverage report
```

---

## Testing Strategy

### Test Types

| Type | Purpose | Location |
|------|---------|----------|
| Unit | Test individual functions/components in isolation | `tests/unit/` |
| Integration | Test how parts work together | `tests/integration/` |
| E2E | Test full user flows | `tests/e2e/` |

### What to Test

- **Always test**: Business logic, data transformations, edge cases
- **Consider testing**: Component behavior, API contracts
- **Usually skip**: Third-party libraries, trivial getters/setters

---

## Writing Tests

### File Naming

```
[name].test.[ext]    # Unit tests
[name].spec.[ext]    # Integration/E2E tests
```

### Test Structure

Examples by language:

**JavaScript/TypeScript (Jest/Vitest)**
```javascript
describe('ComponentName', () => {
  describe('methodName', () => {
    it('should [expected behavior] when [condition]', () => {
      // Arrange
      // Act
      // Assert
    });
  });
});
```

**Python (pytest)**
```python
class TestComponentName:
    def test_should_do_something_when_condition(self):
        # Arrange
        # Act
        # Assert
        pass
```

**Ruby (RSpec)**
```ruby
RSpec.describe ComponentName do
  describe '#method_name' do
    it 'does something when condition' do
      # Arrange
      # Act
      # Assert
    end
  end
end
```

**Go**
```go
func TestMethodName_Condition(t *testing.T) {
    // Arrange
    // Act
    // Assert
}
```

**Rust**
```rust
#[cfg(test)]
mod tests {
    #[test]
    fn test_method_name_when_condition() {
        // Arrange
        // Act
        // Assert
    }
}
```

**Java (JUnit)**
```java
class ComponentNameTest {
    @Test
    void shouldDoSomethingWhenCondition() {
        // Arrange
        // Act
        // Assert
    }
}
```

### Naming Conventions

- Describe **what** the code does, not **how**
- Use "should [verb]" format
- Be specific about conditions

Good: `it('should return empty array when no items match filter')`
Bad: `it('works correctly')`

---

## Test Data

### Fixtures

*Describe where and how to manage test fixtures.*

```bash
# Location: tests/fixtures/
```

### Factories / Builders

*Describe how to generate test data.*

```
# [Add examples for your stack]
```

### Mocking

*Describe mocking conventions.*

```
# [Add examples for your stack]
```

---

## Coverage

### Requirements

- Minimum coverage: *[Define your threshold, e.g., 80%]*
- New code should include tests

### Viewing Coverage

```bash
# Generate coverage report
# [Add your command here]

# Open HTML report
# [Add your command here]
```

---

## CI Integration

Tests run automatically on:
- Pull request creation
- Push to `main` / `develop`

See `.github/workflows/` for CI configuration.

---

## Troubleshooting

### Tests are slow

- Check for unnecessary database calls
- Use mocks for external services
- Run specific files instead of full suite

### Tests are flaky

- Avoid time-dependent assertions
- Clean up state between tests
- Check for race conditions
