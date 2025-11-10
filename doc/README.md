# Textual Contribution Project Documentation

📚 **Documentation for contributing to the Textual project**

This directory contains documentation and context for working on contributions to the [Textual](https://github.com/Textualize/textual) project.

---

## 📋 Quick Start

### Prerequisites Check
```bash
# Check Python version (needs 3.9+)
python3 --version

# Check if Poetry is installed
poetry --version

# Check if Make is available
make --version
```

### Initial Setup
```bash
# Navigate to repository
cd /Users/fx/Documents/gitstuff/textual

# Install Poetry if not installed (see below)
# Then activate environment
poetry shell

# Install dependencies
make setup

# Verify installation
textual --version

# Install pre-commit hooks
pre-commit install

# Run demo to verify everything works
make demo
```

---

## 📖 Documentation Files

- **[Memory.md](./Memory.md)** - Comprehensive memory and context for AI agents
- **[README.md](./README.md)** - This file - quick reference guide
- **[BugAnalysis.md](./BugAnalysis.md)** - Analysis of bugs to fix (easy ones first)
- **[SessionLog.md](./SessionLog.md)** - Log of all sessions and tasks

---

## 🛠️ Development Commands

### Setup & Environment
```bash
make setup              # Install all dependencies
poetry shell            # Activate virtual environment
poetry install          # Install dependencies (alternative)
```

### Code Quality
```bash
make format             # Format code with black
make format-check       # Check code formatting
make typecheck         # Run mypy type checking
```

### Testing
```bash
make test              # Run all tests
make testv             # Run tests with verbose output
make test-coverage     # Run tests with coverage report
make test-snapshot-update  # Update snapshot tests
```

### Documentation
```bash
make docs-serve-offline    # Serve docs locally (reloads on changes)
make docs-build            # Build documentation
make docs-build-offline    # Build offline documentation
```

### Demo & Development
```bash
make demo              # Run Textual demo
make repl              # Start Python REPL with textual imported
```

---

## 📝 Contribution Checklist

Before opening a PR, ensure:

- [ ] Code is formatted: `make format`
- [ ] All tests pass: `make test`
- [ ] Type checking passes: `make typecheck`
- [ ] CHANGELOG.md is updated
- [ ] All code has docstrings
- [ ] Tests are written for changes
- [ ] Snapshot tests updated (if visual changes)

---

## 🐛 Finding Issues to Fix

1. **GitHub Issues**: https://github.com/Textualize/textual/issues
   - Look for "good first issue" labels
   - Check for bugs that match your skills

2. **Test Failures**: Run `make test` and look for failing tests

3. **Type Errors**: Run `make typecheck` and fix type issues

4. **Documentation**: Check docs for outdated or incorrect information

---

## 🧪 Testing Guidelines

### Running Tests
```bash
# All tests
make test

# Specific test file
poetry run pytest tests/path/to/test_file.py

# Specific test
poetry run pytest tests/path/to/test_file.py::test_function_name

# Snapshot tests
pytest -vv tests/snapshot_tests/test_snapshots.py
```

### Writing Tests
- **Bug fixes**: Add regression tests that link to the original issue
- **Visual elements**: Add snapshot tests
- **New features**: Add comprehensive test coverage

### Snapshot Testing
Snapshot tests ensure visual widgets look correct:
1. Create test in `tests/snapshot_tests/test_snapshots.py`
2. Run: `pytest -vv tests/snapshot_tests/test_snapshots.py`
3. Review browser interface showing diffs
4. Update snapshots: `make test-snapshot-update`

---

## 📚 Learning Resources

- **Official Docs**: https://textual.textualize.io/
- **Examples**: `examples/` directory in repository
- **API Reference**: https://textual.textualize.io/api/
- **Discord Community**: https://discord.gg/Enf6Z3qhVr

---

## 🔧 Installing Poetry

If Poetry is not installed:

### macOS/Linux
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

### Alternative (pip)
```bash
pip install poetry
```

### Verify Installation
```bash
poetry --version
```

---

## 📁 Project Structure

```
textual/
├── src/textual/          # Main source code
├── tests/                # Test suite
├── docs/                 # Documentation source
├── examples/             # Example applications
├── tools/                # Development tools
├── doc/                  # Our contribution docs (this folder)
├── sandbox/              # Temporary scripts
├── pyproject.toml        # Poetry config
├── Makefile              # Build commands
└── CONTRIBUTING.md       # Contribution guide
```

---

## 🎯 Common Tasks

### Adding a New Feature
1. Create feature branch
2. Implement feature with tests
3. Add docstrings
4. Format code: `make format`
5. Run tests: `make test`
6. Update CHANGELOG.md
7. Open PR

### Fixing a Bug
1. Reproduce the bug
2. Write regression test (should fail)
3. Fix the bug
4. Verify test passes
5. Format code: `make format`
6. Update CHANGELOG.md
7. Open PR with link to issue

### Improving Documentation
1. For subjective changes: Open issue first
2. For technical issues: Direct PR is fine
3. Build docs locally: `make docs-serve-offline`
4. Preview changes
5. Open PR

---

## 💡 Tips

- Always run `poetry shell` before working
- Use `make demo` to see Textual in action
- Check existing code for docstring style examples
- Join Discord for help and discussion
- Review existing PRs to understand contribution style

---

## 🔗 Useful Links

- **Repository**: https://github.com/Textualize/textual
- **Documentation**: https://textual.textualize.io/
- **Discord**: https://discord.gg/Enf6Z3qhVr
- **Issues**: https://github.com/Textualize/textual/issues
- **Poetry Docs**: https://python-poetry.org/docs/

---

*Last Updated: Initial setup*
