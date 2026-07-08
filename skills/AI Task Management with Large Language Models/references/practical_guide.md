# Practical Guide to AI Task Management

## Identifying Fable-Scale Tasks
Look for:
1. Tasks that make you sigh/face-palm when considering them
2. Work everyone knows needs doing but nobody owns
3. Projects requiring weeks of manual effort (e.g., 500-page document review)
4. Data-intensive operations (CRM cleanups, inventory reconciliations)

## Data Preparation Framework
1. **Source Identification**: Map all required data sources (APIs, spreadsheets, documents)
2. **Sanitization**: Remove sensitive data the model shouldn't process
3. **Structuring**: Organize data for model comprehension (e.g., CSV for tabular data)
4. **Metadata**: Include explanatory notes about data conventions

## Success Criteria Definition
For each task, document:
- **Quality Standards**: What "done right" looks like (e.g., "0 typos in final document")
- **Review Process**: How you'll validate outputs (sampling strategy, automated checks)
- **Revision Protocol**: Process for correcting identified issues

## Common Task Archetypes
1. **Mega-Document Processing**: Legal/compliance reviews, consistency checks
2. **Data Reconciliation**: CRM deduplication, financial record alignment
3. **Code Refactoring**: Large-scale architecture changes with style enforcement
4. **Research Synthesis**: Combining multiple sources into executive briefs

## Cost Management
- Estimate token usage using model pricing calculators
- Compare against human labor costs for same task
- Budget for 2-3 revision cycles in cost projections