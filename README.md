# AI Context Standard

> A human-readable, hierarchical standard for providing context to AI coding assistants

[![GitHub stars](https://img.shields.io/github/stars/vibe-stack/ai-context-standard?style=social)](https://github.com/vibe-stack/ai-context-standard)
[![License: CC0](https://img.shields.io/badge/License-CC0-blue.svg)](https://creativecommons.org/publicdomain/zero/1.0/)
[![Spec Version](https://img.shields.io/badge/spec-v1.0--draft-orange.svg)](./SPEC.md)

## The Problem

You spend time explaining the same project context to every AI coding assistant:

- "This is a React TypeScript project using Next.js..."
- "Follow these coding standards..."  
- "The architecture works like this..."
- "Don't touch the legacy auth code..."

Then you switch tools and start over. **There has to be a better way.**

## The Solution

AI Context Standard provides a simple `.aicontext` file format that any AI tool can understand:

```markdown
---
version: "1.0"
---

# My React App

## Overview
A React TypeScript project using Next.js 14 with App Router.

## Architecture  
- `/app` - Next.js pages and layouts
- `/components` - Reusable UI components
- `/lib` - Utilities and business logic

## Coding Standards
- Use functional components with hooks
- Always include TypeScript interfaces for props
- Prefer composition over inheritance

## Context Hints
When working on authentication, reference `/lib/auth.ts` patterns.
```

Place `.aicontext` files anywhere in your project. AI tools merge them hierarchically, giving you precise control over context at every level.

## Quick Start

1. **Create** a `.aicontext` file in your project root
2. **Write** your project context in simple Markdown
3. **Use** with any compatible AI tool

### Example Structure

```
my-project/
├── .aicontext                 # Project-wide context
├── src/
│   ├── components/
│   │   └── .aicontext        # Component-specific rules
│   └── api/
│       └── .aicontext        # API-specific guidelines
└── docs/
    └── .aicontext            # Documentation context
```

## Key Features

🧠 **Tool Agnostic** - Works with any AI coding assistant  
📝 **Human Readable** - Just Markdown with optional YAML frontmatter  
🏗️ **Hierarchical** - Context inherits and overrides naturally  
🎯 **File Specific** - Target rules to specific file types  
🔗 **Composable** - Share and extend contexts across projects  
⚡ **No Dependencies** - Simple files, no special tooling required  

## Real Examples

### Frontend Project
```markdown
---
version: "1.0"
applies_to: ["*.tsx", "*.ts"]
---

# E-commerce Frontend

## Tech Stack
React 18, TypeScript, Tailwind CSS, React Query

## Component Patterns
- Use compound components for complex UI
- Colocate types with components
- Export both component and props interface

### `*.tsx` files
Always use `forwardRef` for components that might need refs.
```

### API Project  
```markdown
---
version: "1.0"
extends: ["../shared-backend.aicontext"]
---

# User Service API

## Architecture
Clean architecture with domain-driven design principles.

## Standards
- Validate all inputs with Zod
- Return consistent error responses
- Log all requests with correlation IDs

### `*.route.ts` files
Include rate limiting and auth middleware on all public endpoints.
```

## Specification

📋 **[Read the Full Specification](./SPEC.md)**

The specification covers:
- Complete file format definition
- Context hierarchy and inheritance rules  
- Implementation guidelines for tools
- Migration paths from existing formats

## Tool Support

### Current Support
- 🏗️ **Reference Implementation** - Basic parser and validator
- 🔧 **VS Code Extension** - Syntax highlighting and validation

### Planned Support
For now, only for vCode-IDE 

- [vCode IDE on Github](https://github.com/vibe-stack/vcode)

*Want to add support to your tool? [Let's chat!](https://github.com/vibe-stack/ai-context-standard/discussions)*

## Migration

### From Cursor Rules
```bash
# Your existing .cursorrules content becomes the main content
# Add version frontmatter and organize into sections
mv .cursorrules .aicontext
# Edit to add frontmatter and structure
```

### From README-driven Context
Extract AI-relevant sections from your README into dedicated `.aicontext` files while keeping human documentation separate.

## Contributing

This is a community-driven standard. We need your input to make it work for everyone.

### Ways to Contribute

🗣️ **Join the Discussion** - Share your use cases in [Discussions](https://github.com/vibe-stack/ai-context-standard/discussions)  
🐛 **Report Issues** - Found a problem? [Open an issue](https://github.com/vibe-stack/ai-context-standard/issues)  
💡 **Suggest Features** - Have ideas? We'd love to hear them  
🔧 **Build Tools** - Create parsers, extensions, or integrations  
📝 **Improve Docs** - Help make the spec clearer and more complete  

### Quick Links

- [📋 Specification](./SPEC.md)
- [💬 Discussions](https://github.com/vibe-stack/ai-context-standard/discussions)
- [🐛 Issues](https://github.com/vibe-stack/ai-context-standard/issues)
- [🚀 Roadmap](https://github.com/vibe-stack/ai-context-standard/projects/1)

## FAQ

**Q: How is this different from `.cursorrules`?**  
A: AI Context is tool-agnostic, hierarchical, and designed as an open standard. While Cursor Rules work great in Cursor, AI Context files should work everywhere.

**Q: What about existing project documentation?**  
A: AI Context complements your existing docs. Keep your README for humans, use `.aicontext` for AI tools.

**Q: How do I validate my `.aicontext` files?**  
A: Actively being worked on

**Q: Can I include sensitive information?**  
A: Be mindful of what you include. Context files may contain architectural details you don't want to share publicly.

## License

This specification is released under [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) - dedicated to the public domain.

---

**Ready to give your AI tools better context?** Star this repo and create your first `.aicontext` file today!

[⭐ Star on GitHub](https://github.com/vibe-stack/ai-context-standard) • [📋 Read the Spec](./SPECIFICATION.md) • [💬 Join Discussion](https://github.com/vibe-stack/ai-context-standard/discussions)
