# Pull Request Patterns - Textual Project

This document tracks patterns and best practices observed from accepted PRs in the Textual project. The goal is to understand what makes PRs successful and apply the same standards to our contributions.

---

## 📊 Analysis Strategy

### Regular Review Process
1. **Weekly Review**: Check recently merged PRs in Textualize/textual
2. **Pattern Identification**: Note common patterns in:
   - Commit message structure
   - PR description format
   - Test coverage approach
   - Code style and documentation
   - Reviewer interaction style
3. **Document Findings**: Update this file with observed patterns
4. **Apply Learnings**: Use these patterns in our PRs

---

## 🔍 Observed Patterns

### PR Description Structure

**Pattern 1: Detailed Description (Preferred)**
- Problem statement with context
- Solution explanation
- Reference to issue number
- Example: PR #6196
  ```
  Currently the `TextArea` cursor display is broken when trying to navigate a wrapped line:
  - Clicking a wrapped line will cause the cursor to disappear
  - Keyboard navigation on a wrapped line won't blink the cursor
  
  The problem is that the line cache introduced in ec0c050 doesn't properly account for wrapped lines.
  
  Fix the cache key so the 'cursor location' element is not simply based on a location in document-space.
  
  Fixes #6195
  ```

**Pattern 2: Concise Description (Also Accepted)**
- Brief summary of changes
- Example: PR #6216
  ```
  Add focus on click
  Add mount_compose
  ```

**Key Observations**:
- Both styles are accepted
- Detailed descriptions are better for complex fixes
- Always reference issue numbers when applicable
- Use "Fixes #XXXX" format for issue references

### Commit Message Patterns

**Observed Format**:
- Short, descriptive titles
- Use conventional commit prefixes when appropriate: `fix()`, `feat()`, `docs()`
- Examples from CHANGELOG:
  - `fix(text area): fix cursor display on wrapped line`
  - `expose grid-size`
  - `Focus on click and mount_compose`

**CHANGELOG Entry Format**:
- Brief description
- Link to PR or issue
- Format: `- Description https://github.com/Textualize/textual/pull/XXXX`

### Test Coverage Patterns
*(To be filled as we review PRs in detail)*

### Code Style Patterns
- Follow project's black formatting
- All tests must pass
- Pre-commit hooks must pass

### Reviewer Interaction Patterns
*(To be filled as we review PRs with comments)*

---

## 📝 Notes from Recent PRs

### PR #6196 - "fix(text area): fix cursor display on wrapped line"
- **Type**: Bug fix
- **Description**: Detailed with problem, solution, and issue reference
- **Commits**: 3 commits
- **Files Changed**: 2 files
- **Changes**: +8 / -1 lines
- **Pattern**: Small, focused fix with clear explanation

### PR #6216 - "Focus on click and mount_compose"
- **Type**: Feature addition
- **Description**: Very concise
- **Commits**: 5 commits
- **Files Changed**: 7 files
- **Changes**: +414 / -8 lines
- **Pattern**: Larger feature, multiple commits, concise description

### Common Acceptance Criteria
- ✅ All tests pass
- ✅ Code formatted correctly (black)
- ✅ CHANGELOG updated
- ✅ Tests added for new features/bug fixes
- ✅ Documentation updated if needed
- ✅ Issue referenced when applicable

---

## 🎯 Our PR Standards (Based on Observations)

### PR Title
- Clear and descriptive
- References issue number if applicable
- Action-oriented (Fix, Add, Change, etc.)
- Can use conventional commit format: `fix(component): description`

### PR Description
**For Bug Fixes**:
- Problem statement with context
- Solution explanation
- Reference to issue: `Fixes #XXXX`
- Testing approach

**For Features**:
- Brief summary or detailed explanation (both accepted)
- Use case or motivation
- Testing approach

### Commits
- One logical change per commit
- Clear commit messages
- Reference issue numbers when applicable
- Can use conventional commit format

### CHANGELOG
- Add entry in appropriate section (Fixed, Added, Changed)
- Format: `- Brief description https://github.com/Textualize/textual/pull/XXXX`
- Or: `- Brief description https://github.com/Textualize/textual/issues/XXXX`

---

## 📚 Learning Notes

### What Makes PRs Successful
1. **Clear Problem/Solution**: Even if description is short, the code should be self-explanatory
2. **Proper Testing**: Tests demonstrate the fix/feature works
3. **CHANGELOG Updated**: Shows awareness of project standards
4. **Issue References**: Links PR to original problem/request
5. **Focused Changes**: One logical change per PR (though can have multiple commits)

### Best Practices to Follow
- Keep PRs focused on one thing
- Write clear commit messages
- Update CHANGELOG.md
- Add tests for bug fixes and new features
- Reference issues when applicable
- Respond to reviewer feedback promptly

---

*Last updated: After analyzing PRs #6196, #6216, #6210, #6214*

*This document will be updated as we review more PRs and learn from the Textual project's standards.*
