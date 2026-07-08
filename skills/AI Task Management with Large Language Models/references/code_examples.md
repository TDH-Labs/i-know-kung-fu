# Code Examples for AI Task Management

## Task Specification Template
```python
task_spec = {
    "task_name": "CRM Data Deduplication",
    "input_sources": [
        {"type": "csv_export", "location": "s3://crm-exports/2024-q2.csv"},
        {"type": "api", "endpoint": "https://api.company.com/customers"}
    ],
    "success_criteria": {
        "completeness": "100% records processed",
        "accuracy": "<0.1% false positive merges",
        "output_format": "Standardized JSON customer profiles"
    },
    "constraints": {
        "privacy": "Do not process payment info columns",
        "timeout": "24h max runtime"
    },
    "review_protocol": {
        "sample_size": "5% random sampling",
        "validation_checks": ["email_format", "postal_code_valid"]
    }
}
```

## Prompt Structure for Large Tasks
```markdown
# PROJECT: Annual Report Fact-Checking

## CONTEXT
- Company: Acme Corp (industrial manufacturing)
- Audience: Investors and regulators
- Style Guide: [LINK_TO_STYLEGUIDE]

## SOURCE MATERIALS
1. Draft report PDF: [LINK]
2. Supporting data: [LINK_TO_SPREADSHEET]
3. Previous year's report: [LINK]

## DELIVERABLES
- Annotated PDF with all factual claims verified
- Appendix of uncorroborated statements
- Consistency matrix against last year's report

## PROCESS INSTRUCTIONS
1. First pass: Flag statistically improbable claims
2. Second pass: Cross-reference with source data
3. Third pass: Check all numerical references

## QUALITY CONTROLS
- Zero tolerance for false verifications
- 100% coverage of numerical data
- Style consistency with previous reports
```

## Output Validation Script
```python
def validate_output(task_output, success_criteria):
    """Sample validation function for programmatic checks"""
    errors = []
    
    # Check completeness
    if len(task_output["processed_items"]) != task_output["total_items"]:
        errors.append(f"Completeness fail: {len(task_output['processed_items'])}/{task_output['total_items']} processed")
        
    # Check accuracy sample
    sample = random.sample(task_output["decisions"], 
                          max(100, int(0.05*len(task_output["decisions"]))))
    false_positives = [d for d in sample if d["action"] == "merge" and not validate_merge(d)]
    
    if len(false_positives)/len(sample) > 0.001:
        errors.append(f"Accuracy fail: {len(false_positives)} false merges in sample")
        
    return {"valid": len(errors) == 0, "errors": errors}
```