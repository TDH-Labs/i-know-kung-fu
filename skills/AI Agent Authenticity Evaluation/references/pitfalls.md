# Common Pitfalls in Agent Evaluation

## Misclassification Errors
1. **Overestimating Automation**: Assuming scheduled tasks represent agentic behavior
   - Example: A system that sends weekly reports automatically isn't agentic

2. **Confusing Generation with Agency**: Mistaking content creation for autonomous operation
   - Example: Chatbots that generate responses but don't pursue goals

## Testing Mistakes
1. **Insufficient Task Complexity**: Using tests that don't differentiate levels
   - Solution: Include multi-step challenges requiring adaptation

2. **Ignoring Process Transparency**: Not examining how results are produced
   - Solution: Always request execution logs or reasoning chains

3. **Timeframe Errors**: Evaluating based on single interactions
   - Solution: Test across multiple sessions to check memory/context

## Vendor Deception Patterns
1. **Buzzword Overload**: Using 'agent' terminology without substance
   - Red Flag: Vague descriptions of 'AI-powered' without specifics

2. **Demo Specialization**: Showing pre-programmed scenarios
   - Detection: Request completely novel tasks during evaluation

3. **Human-in-the-Loop Masking**: Hiding manual intervention
   - Test: Measure response times and consistency for unusual requests