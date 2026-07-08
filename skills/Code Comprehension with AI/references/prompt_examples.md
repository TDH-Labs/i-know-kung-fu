# Concrete Prompt Examples and Templates

## Basic Catch Me Up Prompt
```
I am a new contributor to the [repository name] project. Catch me up on how this repository works using these exploration modes:
1. Architecture - Show the high-level components and their relationships
2. Convention - Document the key coding patterns and style rules
3. Feature Trace - Explain how [specific feature] is implemented

Present the information in table format with these columns:
- Component/Concept
- Purpose
- Key Dependencies
- Notable Implementation Details

Specifically clarify: [your burning question about the codebase]
```

## PR Review Assistance Prompt
```
I'm reviewing PR #[number] in [repository]. Help me comprehend:
1. What existing components this change affects (Architecture)
2. Whether it follows our [language/framework] conventions (Convention)
3. How it compares to similar past changes (History)

Identify any:
- Potential breaking changes
- Untested edge cases
- Deviations from established patterns

Format as:
1. Summary of changes
2. Risk assessment
3. Suggested review focus areas
```

## Incident Investigation Prompt
```
We're seeing [error description] in [component]. Help me trace:
1. When this behavior was introduced (History)
2. All code paths that could lead to this state (Feature Trace)
3. Relevant test coverage (Testing)

Create a timeline of:
- Key commits affecting this area
- Past similar incidents
- Recent related changes

Output as markdown with:
- Timeline section
- Code path flowchart description
- Test gap analysis
```

## Convention Verification Prompt
```
I'm modifying [file path]. Verify:
1. Does this follow our [language] conventions?
2. Are there similar patterns elsewhere in the codebase?
3. What exceptions to conventions exist and why?

Compare against:
- Our style guide
- Recent similar changes
- Core framework patterns

Highlight any deviations with:
- Severity (critical/warning/suggestion)
- Justification if intentional
- Suggested alternatives if problematic
```