# Core Concepts of AI Research OS

## Three-Layer Architecture

The system operates on three distinct layers:
1. **Raw Layer**: Immutable source files (articles, videos, code repos) stored in their original format
2. **Index Layer**: A YAML-based catalog containing metadata and summaries of all sources
3. **Wiki Layer**: AI-generated derivatives including:
   - Concept explanations
   - Entity definitions
   - Comparative analyses
   - Open research questions

## Key Principles

- **File-Based Organization**: Avoids complex databases in favor of simple file structures
- **Progressive Disclosure**: Agents first check summaries, then wiki pages, only accessing raw sources when necessary
- **Organic Growth**: Every interaction leaves traces in the wiki through new concepts or notes
- **Project-Centric**: Research is scoped to specific initiatives (articles, videos, codebases)

## Component Integration

The system connects with:
- Obsidian for note management
- Readwise for content highlights
- Notebook LM for research assistance
- GitHub for codebase analysis
- Web scrapers for external content

Each component remains independent while contributing to the unified index, allowing for flexible customization based on user needs.