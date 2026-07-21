# Code Examples for Generative UI
This document provides concrete code examples for implementing Generative UI layers.

### Rendering Contract Example
```python
contract = {
  "components": ["date_field", "time_field", "submit_button"],
  "layout_rules": {
    "flights": {
      "1-3": "swipable_carousel",
      "4+": "vertical_list"
    }
  }
}
```

### Streaming Example
```python
# Simulate streaming UI components
components = ["skeleton", "partial_fill", "complete"]
for component in components:
    render(component)
```

### BFF Example
```python
# Handle platform-specific rendering
if platform == "Android":
    render_android_ui()
elif platform == "iOS":
    render_ios_ui()
```

### Best Practices
- **Version Awareness**: Ensure the model is aware of client capabilities.
- **Progressive Rendering**: Use streaming to show partial results.
- **Platform-Specific Rules**: Let the BFF handle platform differences.

For more details, see [Practical Guide](references/practical_guide.md).