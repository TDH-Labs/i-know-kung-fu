# Practical Guide to Agent Maintenance

## Step 1: Establish Baseline Metrics

Before making changes, document:
- Current toolset and permissions
- Key performance indicators (response time, accuracy, etc.)
- Human review workload
- Error rates by task type

## Step 2: Implement the Five Checks

1. **Source Audit**:
   - List all data sources the agent uses
   - Verify each is still authoritative
   - Identify new sources that should be added
   - Flag deprecated sources for removal

2. **Permission Review**:
   - Catalog all access rights (read, write, execute)
   - Assess if each is still appropriate for current model capabilities
   - Implement least-privilege principles

3. **Job Description Validation**:
   - Compare current agent outputs to original design
   - Identify capability creep or underutilization
   - Explicitly document allowed and prohibited actions

4. **Proof Requirements**:
   - Ensure every factual claim requires sourcing
   - Implement traceability for all recommendations
   - Standardize evidence presentation formats

5. **Value Assessment**:
   - Track actual usage of agent outputs
   - Measure time saved versus time spent reviewing
   - Identify redundant or low-value outputs

## Maintenance Schedule

- **Weekly**: Quick source validity checks
- **Monthly**: Full permission and job scope review
- **Quarterly**: Comprehensive harness redesign session
- **After Model Updates**: Immediate impact assessment

## Pruning Methodology

1. List all tools/integrations
2. For each, ask:
   - Is this absolutely essential to core functionality?
   - Has usage declined over time?
   - Does it create more errors than value?
3. Remove anything not passing all three questions
4. Monitor performance for 1-2 weeks
5. Reintroduce tools only if clear regression appears