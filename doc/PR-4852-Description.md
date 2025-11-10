# PR Description: Fix TextArea scrollbar position not updated after paste

## Description

Fixes #4852

When pasting text into a `TextArea`, the vertical scrollbar position was not updated to show the cursor position after the pasted text. Users had to manually scroll to see where their cursor ended up—a classic UX frustration that's been plaguing text editors since the days of vi vs emacs debates.

## The Problem

The `TextArea` widget has two methods for handling paste operations:
1. `_on_paste()` - handles paste events (programmatic or external)
2. `action_paste()` - handles keyboard shortcuts (Ctrl+V, Cmd+V)

Both methods correctly insert the text and move the cursor to the end of the pasted content, but neither was calling `scroll_cursor_visible()` to ensure the scrollbar updated to show the new cursor position.

## The Solution

Added `scroll_cursor_visible()` calls in both methods after `move_cursor()`. This ensures that:
- The scrollbar automatically scrolls to show the cursor after pasting
- Works correctly for both vertical and horizontal scrolling
- Handles edge cases (gutters, viewport boundaries) automatically
- Uses existing, well-tested code—no need to reinvent the wheel

## Changes

- Added `scroll_cursor_visible()` call in `_on_paste()` method (line ~1853)
- Added `scroll_cursor_visible()` call in `action_paste()` method (line ~2534)
- Added 3 regression tests to prevent this bug from returning
- Updated CHANGELOG.md

## Testing

Added comprehensive regression tests:
- `test_paste_scrollbar_position_updated()` - Tests paste via action (Ctrl+V)
- `test_paste_event_scrollbar_position_updated()` - Tests paste via event
- `test_paste_scrollbar_with_wide_text()` - Tests with wide text requiring both scrollbars (addresses comment from TomJGooding)

All tests pass ✅, and existing tests continue to pass ✅.

## Checklist

- [x] Update the `CHANGELOG.md`
- [x] Format your code with black (`make format`)
- [x] All your code has docstrings in the style of the rest of the codebase
- [x] Your code passes all tests (`make test`)
- [x] Added regression tests that link to the original issue (#4852)

**Please review the following checklist.**

- [x] Docstrings on all new or modified functions / classes 
  - ✅ `_on_paste()` method already had docstring (no changes needed)
  - ✅ `action_paste()` method already had docstring (no changes needed)
  - ✅ All 3 new test functions have comprehensive docstrings

- [x] Updated documentation
  - ✅ No public API changes - this is an internal fix
  - ✅ No documentation updates required (behavior change is self-explanatory)

- [x] Updated CHANGELOG.md (where appropriate)
  - ✅ Entry added: "Fixed `TextArea` scrollbar position not updated after paste https://github.com/Textualize/textual/issues/4852"

---

*Sometimes the best fixes are the ones that make you go "oh, of course!"—just two lines of code, but immediate impact on user experience.*
