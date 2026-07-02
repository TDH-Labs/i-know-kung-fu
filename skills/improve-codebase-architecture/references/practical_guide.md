# Practical Codebase Clean-up Guide

- **Keep it DRY**: Don't repeat yourself. If a helper function is used in three places, move it to a shared helper library.
- **Prune dead files**: Clean up temporary scripts, experimental notebooks, or test fixtures that are no longer part of the build pipeline.
- **Lint consistently**: Use tools like Black, Ruff, or ESLint to enforce styling consistency across the project.
