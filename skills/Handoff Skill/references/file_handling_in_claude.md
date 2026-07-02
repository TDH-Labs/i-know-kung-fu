# File Handling in Claude

## Overview
File handling in Claude requires careful attention to avoid common errors. This guide covers best practices for reading and writing files in Claude.

## Best Practices
- **Read Before Write**: Always read the file before writing to avoid errors.
- **Temporary Files**: Use temporary files for handoff documents to ensure they are not kept around unnecessarily.

## Examples
```python
import tempfile
with tempfile.NamedTemporaryFile(delete=False, prefix='handoff_', suffix='.txt') as temp_file:
    temp_file.write(summary.encode('utf-8'))
    handoff_path = temp_file.name
```

## Troubleshooting
- **File Errors**: Ensure the file is correctly read before writing.
- **File Integrity**: Confirm that the file is correctly written and readable.