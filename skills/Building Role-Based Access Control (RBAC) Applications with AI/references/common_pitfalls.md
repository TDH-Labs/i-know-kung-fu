# Common Pitfalls in AI-Assisted RBAC Development

1. **Premature Generation**: Building the app before defining permissions leads to expensive rework. Example: Generating a UI where organizer vs. regular user is just a button label rather than a true permission.

2. **Flattened Data Structures**: Using comma-separated strings instead of proper relational tables. This breaks when users sign up for multiple events.

3. **Over-Reliance on AI**: Using AI for everything, including tasks better suited to visual tools. This runs up token costs for simple permission changes.

4. **Fragile Automations**: Creating workflows that break when the data model changes, requiring constant AI regeneration.

5. **Incomplete Testing**: Not verifying that permission rules work at all levels (UI, API, database).

6. **Scope Mismatch**: Using the wrong tool for the job (e.g., trying to build a consumer UI app with a business tool).

## Anti-Pattern Examples
- Storing sign-ups as "user1,user2" in an events table
- Reprompting AI to fix permission issues instead of using visual permission editors
- Building complex workflows through sequential AI prompts rather than integrated automation tools
- Not considering edge cases like concurrent sign-ups or permission changes

## Prevention Strategies
- Always define permissions before generation
- Inspect the generated database schema for proper relationships
- Use visual tools for permissions and workflows
- Reserve AI for specific custom UI components
- Test all permission scenarios thoroughly