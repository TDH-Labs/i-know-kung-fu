## Code Examples

### Simple AI Prompt for Code Generation
```python
# Example of a simple AI prompt for code generation
prompt = "Generate a Python function to calculate the factorial of a number."
response = ai_agent.generate(prompt)
print(response)
```

### Unit Testing AI-Generated Code
```python
# Example of unit testing AI-generated code
def test_factorial():
    assert factorial(5) == 120
    assert factorial(0) == 1
    assert factorial(1) == 1
```

### Integration Testing
```python
# Example of integration testing AI agents
def test_integration():
    result = ai_agent.generate("Generate a function to calculate the factorial of a number.")
    assert result == expected_output
```
