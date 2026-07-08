# Practical Guide to Building RBAC Apps

## Initial Setup
1. Start with a clear prompt describing your application's core functionality and user roles. For example:
   "Build an event management app. Organizers can create and edit events with name, date, and description. Regular users can view events and sign up."

2. Before any generation occurs, define:
   - All user roles (e.g., organizers, regular users)
   - Permissions for each role (create/edit vs. view)
   - Key data entities and their relationships

## Database Design
- Ensure your tool creates proper relational tables, not flattened structures
- Verify relationships are modeled correctly (e.g., sign-ups should link users to events via a join table)
- Check that all necessary fields exist for each entity

## Permission Implementation
- Use visual tools to assign permissions rather than prompting AI
- Create clear permission groups with checkboxes for each capability
- Test each role's access thoroughly

## Workflow Automation
- Set up triggers based on data changes (e.g., new sign-up)
- Define actions (send email, update status)
- Add conditions (check capacity before allowing sign-up)
- Ensure workflows update automatically when data model changes

## Custom Logic
- Use AI only for specific UI components (like a capacity counter)
- Keep these components self-contained and permission-aware
- Avoid using AI for core permission or workflow logic