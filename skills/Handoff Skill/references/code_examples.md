# Code Examples and Templates

## Basic Handoff Command
```
/handoff
```
This creates a standard handoff document summarizing the current conversation.

## Focused Handoff with Arguments
```
/handoff "Continue with the prototype implementation focusing on the user authentication flow"
```
The argument becomes the focus description for the next agent.

## Handoff Document Structure Example
```markdown
# Handoff Document

## Conversation Summary
[Brief summary of key points from the conversation]

## Current State
[Description of where the work currently stands]

## Suggested Next Steps
1. [First recommended action]
2. [Second recommended action]
3. [Etc.]

## Recommended Skills
- /prototype
- /grill
- /implement

## Artifact References
- [path/to/relevant/file1]
- [path/to/relevant/file2]
```

## File Handling Pseudocode
```python
def create_handoff(content):
    temp_dir = get_temp_directory()
    file_path = os.path.join(temp_dir, 'mic_temp_t_handoff.md')
    
    # Claude requires reading before writing
    if os.path.exists(file_path):
        with open(file_path, 'r') as f:
            existing_content = f.read()
    
    with open(file_path, 'w') as f:
        f.write(content)
    
    return file_path
```