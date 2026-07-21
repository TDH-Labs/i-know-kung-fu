# Code Examples

## Configuration File
```json
{
  "api_key": "your_api_key_here",
  "model": "MiniMax M2.5",
  "base_url": "https://api.openrouter.ai"
}
```

## Modular File Structure
```plaintext
project/
│
├── .claude/
│   └── settings.json.local
├── src/
│   ├── auth.js
│   ├── database.js
│   ├── routes.js
│   └── utils.js
└── README.md
```

## Prompt Example
```plaintext
Create a modular authentication system with the following features:
- User registration
- User login
- Password reset
Ensure each feature is in a separate file and follows best practices for security.
```

## Testing Script
```bash
# Run tests for each module
npm test auth.js
npm test database.js
npm test routes.js
npm test utils.js
```

## GitHub Push Command
```bash
# Add, commit, and push changes to GitHub
git add .
git commit -m "Added authentication system"
git push origin main
```