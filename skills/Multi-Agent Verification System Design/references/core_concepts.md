# Core Concepts of Multi-Agent Systems

Multi-agent systems (MAS) are AI architectures where multiple specialized agents work together to solve complex problems. Unlike single-agent systems, MAS incorporates:

1. **Specialization**: Each agent has a distinct role (e.g., generator, verifier, adversary)
2. **Redundancy**: Critical functions are checked by multiple agents
3. **Verification Protocols**: Clear rules for resolving disagreements (e.g., NASA's go-no-go)
4. **Uncertainty Awareness**: Built-in mechanisms to identify and flag uncertain outputs

Key principles from historical implementations:
- **Medical Tumor Boards**: Multiple experts debate until consensus
- **Financial 4-Eyes Principle**: Dual approval for critical transactions
- **Aviation Checklists**: Systematic verification under pressure
- **NASA Mission Control**: Specialized roles (GUIDO, FIDO, etc.) with veto power

MAS is particularly valuable when:
- Errors could cause harm (healthcare, finance)
- Regulatory compliance is required
- Confidence estimation is critical
- Hallucinations would be catastrophic

Single-agent systems remain appropriate for low-stakes applications like content summarization or entertainment recommendations where errors have minimal consequences.