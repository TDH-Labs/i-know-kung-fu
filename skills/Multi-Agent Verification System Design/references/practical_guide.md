# Practical Implementation Guide

## Agent Roles
1. **Generator Agent**: Creates initial responses (fast, creative)
   - Prompt template: "Generate a [medical diagnosis/financial recommendation] for [input details]. Provide your most confident answer."

2. **Verifier Agent**: Fact-checks outputs
   - Prompt template: "Verify this [diagnosis/recommendation]: [Generator's output]. Check against [knowledge sources]. Identify any factual inconsistencies or unsupported claims."

3. **Adversary Agent**: Stress-tests conclusions
   - Prompt template: "Challenge this output: [Generator's output]. List all possible failure modes, edge cases, or alternative interpretations. Be exhaustive."

## System Architecture
- **Orchestration Layer**: Manages agent communication (sequential or parallel)
- **Voting Mechanism**: Resolves disagreements (majority, unanimous, or expert-weighted)
- **Escalation Protocol**: Human review triggers for unresolved conflicts

## Implementation Considerations
1. **Latency vs Accuracy Tradeoff**: More agents increase reliability but slow response times
2. **Cost Optimization**: Only use full MAS for high-stakes decisions
3. **Domain Specialization**: Tailor agent roles to specific use cases (e.g., legal vs medical)

Example Deployment Pattern:
1. Generator produces draft output
2. Verifier and Adversary run in parallel
3. System compares results:
   - If consensus: Return verified output
   - If conflict: Escalate to human or run additional verification rounds