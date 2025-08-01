# Contributing to AI Context Standard

Thank you for your interest in contributing to the AI Context Standard! This document outlines how to propose changes to the specification itself.

## Contribution Phases

### Phase 1: Discussion (Open Community Input)
**Duration:** Ongoing  
**Status:** Current Phase

During this phase, we're gathering community input on the initial specification draft. All feedback is welcome, and major changes are still possible.

**How to contribute:**
- Open [Discussions](https://github.com/vibe-stack/ai-context-standard/discussions) for general ideas
- Create [Issues](https://github.com/vibe-stack/ai-context-standard/issues) for specific problems or suggestions
- Comment on existing proposals
- Share real-world use cases and examples

**What we're looking for:**
- Feedback on the overall approach and design
- Missing use cases or requirements
- Technical implementation concerns
- Developer experience feedback
- Tool maintainer input

### Phase 2: Refinement (Structured Proposals)
**Status:** Planned for Month 2-3

Once we have sufficient community input, we'll move to a more structured proposal process for significant changes.

**Process:**
- RFC (Request for Comments) process for major changes
- Working groups for complex topics
- Formal review periods
- Prototype implementations required for breaking changes

### Phase 3: Stabilization (Limited Changes)
**Status:** Planned for Month 4-6

As we approach v1.0 stable, only critical fixes and clarifications will be accepted.

**Criteria for changes:**
- Security fixes
- Critical interoperability issues
- Clarification of ambiguous language
- Minor backward-compatible improvements

### Phase 4: Maintenance (Conservative Evolution)
**Status:** Post v1.0

After v1.0 release, the specification will follow semantic versioning with a conservative approach to changes.

## Current Contribution Guidelines

### Reporting Issues

**Specification Issues**
- Ambiguous language
- Missing requirements
- Technical inconsistencies
- Implementation difficulties

**Use Case Issues**
- Unsupported scenarios
- Real-world problems not addressed
- Integration challenges

**Template:**
```markdown
## Issue Type
[ ] Specification Ambiguity
[ ] Missing Feature
[ ] Technical Problem
[ ] Use Case Gap

## Description
Clear description of the issue

## Impact
Who is affected and how

## Proposed Solution (optional)
Your suggested approach
```

### Suggesting Changes

**Small Changes** (typos, clarifications, minor improvements):
- Create an issue or pull request directly
- No formal process required

**Medium Changes** (new optional features, format extensions):
- Open a discussion first to gauge interest
- Create detailed issue with rationale
- Implement prototype if possible

**Large Changes** (breaking changes, major new features):
- Required discussion period (minimum 2 weeks)
- Community consensus needed
- Must include migration path
- Reference implementation required

### Discussion Guidelines

**General Discussions**
- Use descriptive titles
- Provide context and examples
- Search existing discussions first
- Stay on topic and be respectful

**Technical Discussions**
- Include code examples where relevant
- Reference specific sections of the spec
- Consider backward compatibility
- Think about implementation complexity

### Pull Request Process

**For Specification Changes:**

1. **Discussion First** - Ensure there's community support for the change
2. **Issue Reference** - Link to the issue that motivated the change
3. **Clear Description** - Explain what changed and why
4. **Examples Updated** - Include relevant examples
5. **Backward Compatibility** - Address any breaking changes

**PR Template:**
```markdown
## Summary
Brief description of changes

## Motivation
Why is this change needed?

## Changes
- List specific changes made
- Reference spec sections affected

## Backward Compatibility
- [ ] No breaking changes
- [ ] Breaking changes with migration path
- [ ] New optional feature

## Examples
Include updated or new examples

## Related Issues
Fixes #123
Related to #456
```

## Specification Versioning

### Version Numbers
- **Major.Minor.Patch** (e.g., 1.0.0)
- **Major**: Breaking changes requiring migration
- **Minor**: New backward-compatible features
- **Patch**: Bug fixes and clarifications

### Change Categories

**Breaking Changes (Major Version)**
- File format changes
- Required field modifications
- Behavior changes that break existing implementations

**New Features (Minor Version)**
- New optional fields
- Additional standard sections
- Extended functionality

**Fixes (Patch Version)**
- Typo corrections
- Clarification of ambiguous language
- Example improvements

## Review Process

### Current Review Team
During Phase 1, the initial maintainers will review all contributions:
- Focus on community consensus
- Technical feasibility
- Real-world applicability

### Future Governance
As the project grows, we'll establish:
- Technical steering committee
- Domain expert reviewers
- Tool maintainer advisory board

## Decision Making

### Consensus Building
- All major changes require community discussion
- Maintainers facilitate but don't dictate
- Focus on technical merit and user benefit

### Conflict Resolution
1. Extended discussion period
2. Alternative proposals
3. Community vote if needed
4. Maintainer decision as last resort

### Appeal Process
If you disagree with a decision:
1. Open a new discussion with additional rationale
2. Provide new evidence or use cases
3. Suggest compromise solutions

## Quality Standards

### Specification Text
- Clear, unambiguous language
- Consistent terminology
- Complete coverage of use cases
- Implementable by tools

### Examples
- Real-world scenarios
- Multiple complexity levels
- Different project types
- Common edge cases

### Documentation
- Keep README and spec in sync
- Update migration guides
- Maintain backward compatibility notes

## Getting Help

**Questions about Contributing:**
- Open a [Discussion](https://github.com/vibe-stack/ai-context-standard/discussions) with "Contributing" tag
- Ask in existing relevant discussions
- Contact maintainers directly for sensitive issues

**Technical Questions:**
- Check existing issues and discussions
- Provide minimal reproducible examples
- Reference specific spec sections

**Process Questions:**
- Review this document first
- Ask in "Meta" discussions
- Suggest improvements to this process

## Recognition

Contributors will be recognized in:
- CONTRIBUTORS.md file
- Release notes for significant contributions
- Specification acknowledgments section

## Code of Conduct

We follow the [Contributor Covenant](https://www.contributor-covenant.org/):
- Be respectful and inclusive
- Focus on technical merit
- Assume good intentions
- Help newcomers participate

---

## Quick Reference

**Phase 1 (Current): Discussion**
- ✅ Open discussions and issues freely
- ✅ Propose major changes
- ✅ Share use cases and examples
- ✅ Comment on any topic

**Getting Started:**
1. Read the [Specification](./SPECIFICATION.md)
2. Browse [existing discussions](https://github.com/vibe-stack/ai-context-standard/discussions)
3. Try the format in your own project
4. Share your experience and suggestions

**Need Help?** Open a discussion with the "Help" tag.

Thank you for helping make AI Context Standard better for everyone! 🚀
