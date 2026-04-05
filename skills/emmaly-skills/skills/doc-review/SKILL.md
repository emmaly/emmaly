---
name: doc-review
description: Use when reviewing project documentation for quality, accuracy, completeness, or consistency — identifies actionable recommendations and presents each interactively
---

# Doc Review

Systematically review documentation, identify items needing attention, and interactively present recommendations for each.

## Scope

Unless the user specifies particular files or directories:

1. **Discover all documentation** in the project — `.md` files, `CLAUDE.md`, `README.md`, etc.
2. **Exclude**: `node_modules`, `.git`, `vendor`, `dist`, `build`, and other generated directories.
3. If the user names specific files or a subset, review only those.

## Review Phase

Read each doc and identify **concrete, actionable** items. Only flag things that actually need addressing — don't manufacture recommendations. Categories:

- **Outdated or inaccurate** information (references to old APIs, removed features, wrong paths)
- **Missing sections or gaps** (undocumented behavior, missing setup steps)
- **Inconsistencies** between docs or between docs and code
- **Clarity/readability** improvements (ambiguous wording, confusing structure)
- **Structural issues** (broken links, formatting problems, poor organization)
- **Convention conflicts** (content that contradicts project conventions or CLAUDE.md)

## Interactive Recommendation Phase

For each recommendation, use `AskUserQuestion` to present it. Structure each question as:

- **Option 1**: Your specific recommendation, marked `(Recommended)` — describe exactly what you'd change
- **Option 2**: An alternative approach — a different reasonable way to address the same issue
- **Option 3**: Skip — leave as-is
- (Other is provided automatically by the tool)

**Batching**: Group up to 4 related recommendations from the same file into a single `AskUserQuestion` call to reduce interruptions. Start a new call for each new file or when you've hit 4 questions.

**Question format**: The question text should clearly state what the issue is. The option descriptions should state what the change would be.

Example:
```
Question: "README.md references `npm start` but the project uses `pnpm dev` — update the command?"
Option 1: "Change to `pnpm dev` (Recommended)" — description of the fix
Option 2: "Document both commands" — alternative approach
Option 3: "Skip" — leave as-is
```

## Update Phase

After collecting all answers:

1. Apply accepted changes (option 1 or option 2 selections) to the docs.
2. For "Other" responses, follow the user's custom instruction.
3. Skip items the user chose to skip.

## Summary

After all updates are applied, report:

- Number of docs reviewed
- Changes made (briefly, per file)
- Items skipped
