# Integrating Skills with Claude Design

Skills automate copy generation and template selection, reducing Claude Design iterations.

## Skill Types
1. **Visual Layout Skills**: Match content to templates
2. **Copy Generation Skills**: Maintain brand voice
3. **Asset Production Skills**: Batch create variations

## Implementation Workflow
1. **Setup**:
   - Install Firecrawl/Playwright connectors
   - Load template PDFs/examples
2. **Training**:
   - Provide 5-10 copy examples
   - Define tone guidelines
3. **Execution**:
   - Input: Content brief/outline
   - Output: Structured prompt for Claude Design

## Example Skill Prompt
```
I'm preparing a LinkedIn carousel about our Q3 results. 
Use the Acme Financial Skill with:
- Data: {attach CSV}
- Tone: Professional but approachable
- Template Preference: Stat-heavy layouts
```

## Validation Steps
1. Check copy against brand voice guidelines
2. Verify template appropriateness
3. Test with 3 sample inputs

## Common Issues
- Overly generic copy → Add more examples
- Template mismatch → Adjust skill parameters
- Style drift → Re-anchor to design system