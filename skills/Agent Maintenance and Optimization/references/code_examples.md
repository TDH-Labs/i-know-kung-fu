# Code and Prompt Examples

## Harness Configuration Template

```python
class AgentHarness:
    def __init__(self):
        # Data Sources
        self.allowed_sources = [
            'crm/current_customers',
            'knowledge_base/v2',
            'support_tickets/last_90_days'
        ]
        
        # Permissions
        self.permissions = {
            'read': True,
            'write': False,
            'execute': ['search', 'draft_responses'],
            'create_records': False
        }
        
        # Proof Requirements
        self.proof_standards = {
            'claims': 'require_source',
            'recommendations': 'show_alternatives',
            'drafts': 'mark_placeholders'
        }
        
        # Human Review Triggers
        self.review_rules = [
            {'condition': 'dollar_value > 1000', 'action': 'require_approval'},
            {'condition': 'new_company', 'action': 'flag_for_review'}
        ]
```

## Pruning Decision Prompt

```
You are an AI agent optimizer. Evaluate whether to keep or remove the following tool:

Tool: {tool_name}
Current Usage: {usage_frequency}
Error Rate: {error_percentage}
Dependencies: {dependent_processes}

Consider:
1. Is this tool absolutely essential to core functionality?
2. Has usage declined significantly over the past quarter?
3. Does it create more errors/overhead than value?
4. Are there newer tools that make this obsolete?

Format your response as:
Decision: keep/remove
Reason: [1-2 sentences]
Impact: [expected effect on performance]
```

## Source Validation Check

```python
def validate_sources(sources):
    """Check if configured sources are still valid"""
    invalid = []
    for source in sources:
        if not source.exists():
            invalid.append(f"Missing: {source}")
        elif source.last_updated < (datetime.now() - timedelta(days=90)):
            invalid.append(f"Stale: {source} (last updated {source.last_updated})")
        elif source.deprecation_notice:
            invalid.append(f"Deprecated: {source}")
    
    if invalid:
        raise ConfigurationError(
            f"{len(invalid)} invalid sources detected:\n" +
            "\n".join(invalid)
        )
```

## Change Log Template

```markdown
## Harness Update {date}

### Changes Made
- Removed: {tools_removed}
- Added: {tools_added}
- Modified: {config_changes}

### Reason
{justification}

### Expected Impact
{performance_prediction}

### Verification Plan
1. {test_case_1}
2. {test_case_2}
3. {test_case_3}
```