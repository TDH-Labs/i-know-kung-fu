# Common Pitfalls in Agent Operations

## Configuration Errors
1. **Overriding Chaos**: Having too many nested agents.md files can create unpredictable behavior when rules conflict. Best practice is to limit overrides to 2-3 levels maximum.

2. **Skill Bloat**: Creating overly broad skills that load unnecessary context. Example: A "document processing" skill that loads both PDF and PowerPoint logic when only one is needed.

## Protocol Missteps
3. **MCP Authentication Gaps**: Forgetting to include credential rotation in MCP configurations can lead to service disruptions when tokens expire.

4. **A2A Discovery Failures**: Agents failing to find each other because:
   - Agent cards aren't properly published
   - Network permissions block discovery requests
   - Card descriptions are too vague for proper matching

## Subagent Problems
5. **Context Leakage**: Assuming subagents inherit all parent context automatically. In reality, you must explicitly pass required context to each subagent.

6. **Orphaned Subagents**: Subagents that don't properly terminate after completing tasks, consuming resources. Always implement:
   - Timeout mechanisms
   - Completion confirmation protocols
   - Resource cleanup routines

## Cross-Platform Issues
7. **File Name Variations**: Some platforms use different names for agents.md (e.g., Claude.md). Always check documentation for the specific agent platform you're using.

8. **Protocol Version Mismatch**: When different agents or tools use incompatible versions of MCP or A2A. Standardize on:
   - MCP v1.2+
   - A2A v2.0+
   Across all components.