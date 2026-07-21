# Core Concepts

## Modular Application Structure
Keeping your application modular is crucial for scalability and maintainability. Each file should focus on a single responsibility, making it easier for the AI to understand and work with the code. This approach also helps in debugging and updating the application.

## Understanding Building Blocks
Before prompting the AI, it's essential to understand the fundamental concepts of your application. For example, if you're building a multi-user application, understanding race conditions can help you craft better prompts and avoid data loss.

## One Task Per Session
Breaking down features into small, manageable tasks ensures that each part of the application is thoroughly tested and functional. This practice also provides a safety net, as you can revert to previous versions if something goes wrong.

## Context Window Management
AI models have a limited context window, meaning they can only process a certain amount of information at a time. Keeping files small and focused helps the AI maintain context and reduces the risk of errors.

## Pro Tips
- Add modularity rules to your prompts or a Claude MD file to avoid repetition.
- Always test each task manually before pushing to GitHub.
- Use GitHub as a backup to safeguard your progress.