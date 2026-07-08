# Step-by-Step Review Workflow

## 1. Initial Scan
- Calculate current file sizes and flag any over 1K lines
- Identify all type boundaries (look for any/unknown/optional markers)
- Map control flow complexity (nesting depth, conditional branches)

## 2. Deep Audit
For each changed file:
1. Check for "code judo" opportunities (structural simplifications)
2. Verify type safety at all boundaries
3. Evaluate abstraction quality (helper functions vs inline logic)
4. Detect unnecessary sequential operations

## 3. Findings Prioritization
Organize issues by severity:
```
1. BLOCKER: File size violations (>1K lines)
2. CRITICAL: Type safety issues (any/unknown)
3. HIGH: Duplicated logic
4. MEDIUM: Legibility concerns
```

## 4. Recommendation Phase
For each finding:
- Propose specific refactors (example: "Split initService.ts into 3 modules")
- Provide code samples for ideal solutions
- Estimate complexity/benefit ratio

## 5. Approval Decision
Reject PRs that:
- Introduce new files >1K lines
- Add type safety violations
- Increase overall complexity

Approve only when:
- Behavior remains correct
- Codebase is cleaner than before
- All critical issues addressed