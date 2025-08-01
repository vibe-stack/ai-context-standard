# AI Context Standard Specification

**Version:** 1.0  
**Status:** Draft  
**Last Updated:** August 2025

## Abstract

The AI Context Standard defines a human-readable, hierarchical configuration format for providing context and instructions to AI coding assistants and agents. This standard enables consistent AI behavior across different tools, IDEs, and workflows while remaining easy to edit and maintain.

## 1. Overview

### 1.1 Problem Statement

Current AI coding tools require context to be re-established for each session or tool switch. Developers waste time providing the same architectural context, coding standards, and project-specific instructions repeatedly across different AI assistants.

### 1.2 Goals

- **Human-Readable**: Easy to write and edit without specialized tools
- **Hierarchical**: Support project-wide, directory-specific, and file-specific contexts
- **Tool-Agnostic**: Work across different AI coding assistants
- **Extensible**: Allow for future enhancements without breaking existing implementations
- **Composable**: Enable sharing and inheritance of context configurations

## 2. File Format

### 2.1 File Name

Context files MUST be named `.aicontext` and placed in directories where they should apply.

### 2.2 File Structure

AI Context files use Markdown format with optional YAML frontmatter:

```markdown
---
version: "1.0"
extends: ["../shared.aicontext", "./docs/api.aicontext"]
priority: 100
applies_to: ["*.ts", "*.tsx"]
---

# Project Context

## Overview
Brief description of the project...

## Architecture
Description of system architecture...

## Coding Standards
Specific coding guidelines...
```

### 2.3 Frontmatter Schema

The YAML frontmatter is optional but provides metadata for processing:

```yaml
version: string          # Required: Spec version (e.g., "1.0")
extends: string[]        # Optional: Paths to parent contexts
priority: number         # Optional: Merge priority (default: 0)
applies_to: string[]     # Optional: File patterns this context applies to
ignore: string[]         # Optional: File patterns to exclude
metadata:               # Optional: Tool-specific metadata
  tool_name:
    custom_field: value
```

## 3. Context Hierarchy

### 3.1 Resolution Order

AI tools MUST resolve context in the following order (highest to lowest priority):

1. File-specific contexts (same directory as target file)
2. Directory contexts (walking up the directory tree)
3. Extended contexts (via `extends` field)
4. Default/fallback contexts

### 3.2 Inheritance Rules

- Child contexts override parent contexts
- `extends` contexts are merged before local content
- Higher `priority` values take precedence during conflicts
- Content is merged additively unless explicitly overridden

### 3.3 File Pattern Matching

The `applies_to` field uses glob patterns to specify file applicability:

```yaml
applies_to: 
  - "*.ts"
  - "*.tsx"
  - "components/**/*.jsx"
```

## 4. Standard Sections

While the format is flexible, these standard sections are recommended:

### 4.1 Project Overview
High-level description of the project, its purpose, and key characteristics.

### 4.2 Architecture
System architecture, design patterns, and structural conventions.

### 4.3 Coding Standards
Language-specific guidelines, formatting preferences, and best practices.

### 4.4 Dependencies
Key libraries, frameworks, and their usage patterns within the project.

### 4.5 File-Specific Rules
Rules that apply to specific file types or patterns, formatted as:

```markdown
### `*.tsx` files
TypeScript React components should use functional syntax with proper prop interfaces.

### `*.api.ts` files
API routes must include proper error handling and input validation.
```

### 4.6 Context Hints
Additional context that helps AI understand project-specific patterns and decisions.

### 4.7 Ignore Patterns
Files and directories that AI should not consider when providing assistance.

## 5. Implementation Guidelines

### 5.1 Parser Requirements

AI tools implementing this standard MUST:

- Parse YAML frontmatter correctly
- Support Markdown content extraction
- Implement proper context hierarchy resolution
- Handle file pattern matching for `applies_to` fields

### 5.2 Context Merging

When merging multiple contexts:

1. Start with the most general context (project root)
2. Apply extended contexts in order
3. Apply directory-specific contexts walking down the path
4. Apply file-specific contexts last
5. Respect priority values for conflict resolution

### 5.3 Error Handling

- Invalid YAML frontmatter SHOULD be ignored with a warning
- Missing extended files SHOULD be skipped with a warning
- Malformed file patterns SHOULD be ignored with a warning
- Processing MUST continue despite individual file errors

## 6. Examples

### 6.1 Basic Project Context

```markdown
---
version: "1.0"
---

# React TypeScript Project

## Overview
A modern React application built with TypeScript, Next.js 14, and Tailwind CSS.

## Architecture
- `/app` - Next.js App Router pages and layouts
- `/components` - Reusable UI components
- `/lib` - Utilities and shared business logic
- `/types` - TypeScript type definitions

## Coding Standards
- Use functional components with hooks
- Prefer composition over inheritance
- Always include proper TypeScript interfaces
- Use semantic HTML elements
```

### 6.2 Component-Specific Context

```markdown
---
version: "1.0"
extends: ["../../.aicontext"]
applies_to: ["*.tsx"]
priority: 10
---

# UI Components

## Component Standards
All components in this directory should:
- Export a default component and its props interface
- Include JSDoc comments for complex props
- Use forwardRef for components that accept refs
- Follow the established naming convention: PascalCase

## Styling
Use Tailwind CSS classes exclusively. Avoid inline styles or CSS modules.
```

### 6.3 API Route Context

```markdown
---
version: "1.0"
extends: ["../../../.aicontext"]
applies_to: ["*.api.ts", "route.ts"]
---

# API Routes

## Standards
- Always validate input using Zod schemas
- Return consistent error response format
- Include proper HTTP status codes
- Add request logging for debugging

## Error Format
```json
{
  "error": "Error message",
  "code": "ERROR_CODE",
  "details": {}
}
```
```

## 7. Migration Guide

### 7.1 From Cursor Rules

Convert `.cursorrules` files to `.aicontext`:

```bash
# .cursorrules content becomes the main content
# Add frontmatter with version
# Organize into standard sections
```

### 7.2 From README-based Context

Extract AI-relevant sections from README files into dedicated `.aicontext` files while maintaining the human documentation separately.

## 8. Tooling

### 8.1 Validation

Tools SHOULD provide validation for:
- YAML frontmatter syntax
- File pattern validity
- Circular dependency detection in `extends`
- Missing extended files

### 8.2 IDE Support

Recommended IDE features:
- Syntax highlighting for `.aicontext` files
- Autocomplete for standard sections
- Validation and error reporting
- Context preview and merging visualization

## 9. Versioning

This specification uses semantic versioning. Breaking changes will increment the major version number. Tools MUST check the `version` field and handle unknown versions gracefully.

## 10. Security Considerations

- Context files may contain sensitive architectural information
- Tools SHOULD respect `.gitignore` patterns for context files
- Consider implications of context inheritance across directory boundaries

## 11. Future Considerations

- Schema validation using JSON Schema
- Conditional contexts based on environment
- Integration with existing configuration formats
- Standardized context sharing and discovery mechanisms

---

**Contributing:** This specification is open for community input. Please submit issues and pull requests to improve and extend this standard.

**License:** This specification is released under CC0 1.0 Universal (Public Domain).
