---
description: How to refactor, format, and structure a codebase that has been cluttered
  or corrupted by AI-generated boilerplate code (slop).
name: improve-codebase-architecture
tags:
- de-slop
- refactor
- code-cleanup
- codebase-cleanup
- clean-code
---

# improve-codebase-architecture

> How to refactor, format, and structure a codebase that has been cluttered or corrupted by AI-generated boilerplate code (slop).

Use this skill to refactor, streamline, and restructure files that have become cluttered, bloated, or fragmented by excessive AI-generated boilerplate.

## 🛠️ Step-by-Step Refactoring Workflow

1. **Establish a Baseline**: Run existing unit tests and linters before making any modifications to ensure you don't introduce regressions.
2. **Identify Slop**: Look for:
   - Duplicate utility functions or redundant helper modules.
   - Files containing large blocks of unused imports.
   - Functions with excessive complexity or unneeded abstraction layers.
3. **Consolidate and De-duplicate**: Extract duplicate logic into a shared helper module and remove duplicate code paths.
4. **Simplify Imports**: Group imports logically and prune unused references.
5. **Verify Changes**: Rerun unit tests and confirm the refactoring did not alter the runtime behavior of the codebase.

## 📺 Source Videos

- [How To De-Slop A Codebase Ruined By AI (with one skill)](https://www.youtube.com/watch?v=3MP8D-mdheA) — AI Coding

**Difficulty**: Intermediate

## Prerequisites

- Python 3.12+
- basic understanding of design patterns
