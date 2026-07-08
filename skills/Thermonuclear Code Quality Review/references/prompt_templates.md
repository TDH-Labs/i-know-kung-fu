# Review Prompt Templates

## Main Review Directive
```
Perform a thermonuclear code quality audit of the current changes. Rethink implementations to:
1. Improve abstractions and modularity
2. Eliminate spaghetti code
3. Strengthen type boundaries
4. Reduce concepts readers must hold

Be extremely ambitious - propose structural changes that delete whole categories of complexity.
```

## Type Safety Checklist
```markdown
For each type boundary:
- [ ] No `any` or `unknown` types
- [ ] No unnecessary optionality (?) 
- [ ] Clear input/output contracts
- [ ] Proper discriminated unions for variant types
```

## File Size Enforcement
```
BLOCKER: File {filename} is {currentLines} lines (max 1000)
Required action:
1. Split into {recommendedFiles} focused modules by:
   - {concern1} -> {newFile1}.ts
   - {concern2} -> {newFile2}.ts
```

## Code Judo Examples
```typescript
// Before: Scattered conditionals
if (tracker === 'custom') { /* special case */ }

// After: Type-driven design
type Tracker = Standard | Custom;
interface Custom { isCustom: true; handler: () => void; }
```