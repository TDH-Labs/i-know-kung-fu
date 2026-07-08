# AI Governance Checklist

## Pre-Production Requirements

1. **Regulatory Compliance**:
   - Document audit trails for all AI decisions
   - Implement PII detection and redaction
   - Establish data access controls

2. **Prompt Versioning**:
   - Treat prompts as code with proper change management
   - Maintain detailed commit messages explaining changes
   - Implement promotion workflows (dev → test → prod)

3. **Model Management**:
   - Test new model versions against evaluation data set
   - Maintain ability to rollback to previous versions
   - Document model performance characteristics

## Production Incident Management

1. **Detection**:
   - Monitor evaluation dashboards for metric deviations
   - Track customer feedback channels

2. **Diagnosis**:
   - Use tracing data to identify root cause
   - Check for data staleness or schema changes

3. **Containment**:
   - Implement circuit breakers for failing components
   - Route queries to human agents when needed
   - Rollback problematic prompt versions

4. **Remediation**:
   - Add new test cases to prevent recurrence
   - Update documentation and runbooks
   - Conduct post-mortem analysis

## Ongoing Maintenance

- **Monthly Review**:
  - Audit prompt changes and their effectiveness
  - Review model performance trends
  - Verify data freshness in knowledge bases

- **Quarterly Review**:
  - Assess evaluation data set coverage
  - Validate governance controls
  - Review access permissions and audit logs