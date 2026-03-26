---
name: apply-standards
description: Write or update the standards section in ~/.claude/CLAUDE.md from emmaly:standards — use to persist standards across all projects
---

# Apply Standards to ~/.claude/CLAUDE.md

This skill writes the content of `emmaly:standards` into `~/.claude/CLAUDE.md` so it is loaded automatically in every conversation, across all projects.

## Steps

1. **Read the standards source**: Read the file `../standards/SKILL.md` relative to this skill (i.e. the sibling `standards` skill directory). Strip the YAML frontmatter (everything between the opening and closing `---` lines). Keep only the body content.

2. **Read `~/.claude/CLAUDE.md`**: If it doesn't exist, create it. Read its current contents.

3. **Check for existing markers**: Look for the marker pair `<!-- emmaly:standards -->` and `<!-- /emmaly:standards -->`.

4. **Update or insert**:
   - **If markers exist**: Replace everything from `<!-- emmaly:standards -->` through `<!-- /emmaly:standards -->` (inclusive) with the new block below.
   - **If no markers**: Append the new block to the end of the file.

5. **Block format** (use exactly this structure):
   ```
   <!-- emmaly:standards -->
   ## Standards

   {body content from standards/SKILL.md}

   <!-- /emmaly:standards -->
   ```

6. **Report**: Tell the user whether the section was added or updated, and confirm the target file path.
