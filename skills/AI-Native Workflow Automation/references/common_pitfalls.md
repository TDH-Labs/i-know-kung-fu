# Common Pitfalls and How to Avoid Them

## 1. Treating AI as Autocomplete
**Mistake**: Using AI just for code completion or simple suggestions
**Solution**: Structure your organization around skill files and treat AI as a workforce
**Example**: The fastest-growing YC companies had 95% AI-generated codebases by treating AI as workforce, not autocomplete

## 2. Uncurated Company Brains
**Mistake**: Letting your knowledge base become a garbage dump with great search
**Solution**: Implement strict hygiene practices with provenance tracking and contradiction checks
**Example**: Without curation, retrieval will surface stale facts with high confidence

## 3. Computation in the Wrong Space
**Mistake**: Putting deterministic tasks in latent space or vice versa
**Solution**: Clearly separate tasks requiring human judgment (latent) from repeatable processes (deterministic)
**Example**: Seat assignments must be stored in deterministic space while matching logic uses latent space

## 4. One-Off Work
**Mistake**: Solving problems individually without creating reusable skills
**Solution**: Always "skillify" successful tasks into reusable components
**Example**: Garry Tan's rule: "If you have to ask for something twice, you failed"

## 5. Overlooking Non-Technical Users
**Mistake**: Thinking only engineers can build these systems
**Solution**: Create interfaces that allow all team members to contribute skill files
**Example**: YC's finance team member who collapsed 100 Excel workbooks into a single app

## 6. Underestimating Scale Differences
**Mistake**: Designing for human working memory limits (7 items) rather than AI scale (million tokens)
**Solution**: Build processes that leverage AI's massive context window
**Example**: An agent can keep "three Harry Potter books" worth of information active simultaneously