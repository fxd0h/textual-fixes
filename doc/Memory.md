# Memory - Textual Contribution Project

This file contains important information and context that should be remembered and used across all AI agent sessions working on contributing to the Textual project.

---

## Project Overview

### Repository Information
- **Repository**: Textual - Modern Text User Interface framework
- **Location**: `/Users/fx/Documents/gitstuff/textual`
- **GitHub**: https://github.com/Textualize/textual
- **Current Version**: 6.5.0 (as of repository clone)
- **Python Version Required**: ^3.9 (Python 3.9+)
- **Current System Python**: 3.11.13

### What is Textual?
Textual is a Python framework for building cross-platform user interfaces that run in the terminal or web browser. It combines modern Python with web development concepts for creating rich terminal applications.

---

## Development Environment Setup

### Prerequisites
1. **Poetry** - Python dependency management tool
   - Installation: https://python-poetry.org
   - Status: Currently NOT installed (needs installation)
   
2. **Python** - Version 3.9 or higher
   - Status: Python 3.11.13 is available ✓

3. **Make** - Build automation tool
   - Status: Should be available on macOS ✓

### Setup Steps (from CONTRIBUTING.md)
1. Install Poetry (if not already installed)
2. Clone the Textual repository ✓ (Done)
3. Run `poetry shell` to create a virtual environment
4. Run `make setup` to install all dependencies
5. Verify installation: `textual --version`
6. Install pre-commit hooks: `pre-commit install`

### Makefile Commands Available
- `make setup` - Install all dependencies
- `make test` - Run all tests
- `make testv` - Run tests with verbose output
- `make format` - Format code with black
- `make format-check` - Check code formatting
- `make typecheck` - Run mypy type checking
- `make demo` - Run the Textual demo
- `make docs-serve-offline` - Serve documentation locally
- `make docs-build` - Build documentation
- `make test-snapshot-update` - Update snapshot tests

---

## Contribution Guidelines

### Code Standards
- **Docstrings**: All code (functions, methods, classes) must have docstrings
- **Formatting**: Code must be formatted with `black` (`make format`)
- **Type Checking**: Code must pass mypy type checking (`make typecheck`)
- **Tests**: Write tests for all code changes
  - Bug fixes: Add regression tests linking to the original issue
  - Visual elements: Add snapshot tests

### Before Opening a PR Checklist
- [ ] Update `CHANGELOG.md`
- [ ] Format code with black (`make format`)
- [ ] All code has docstrings in the style of the codebase
- [ ] Code passes all tests (`make test`)

### Testing Guidelines
- **Snapshot Tests**: For visual elements/widgets
  - Run with: `pytest -vv tests/snapshot_tests/test_snapshots.py`
  - Update snapshots: `make test-snapshot-update`
  - Never modify snapshot files manually

### Documentation
- Documentation is built with MkDocs
- Preview locally: `make docs-serve-offline`
- For documentation changes, consider opening an issue first (subjective changes)
- Direct PRs are fine for objective/technical issues (bugs, broken links)

---

## Project Structure

### Key Directories
- `src/textual/` - Main source code
- `tests/` - Test suite
- `docs/` - Documentation source files
- `examples/` - Example applications
- `tools/` - Development tools
- `doc/` - Our contribution documentation (created)
- `sandbox/` - Temporary scripts (created)

### Important Files
- `pyproject.toml` - Poetry configuration and dependencies
- `Makefile` - Build and development commands
- `CONTRIBUTING.md` - Contribution guidelines
- `CHANGELOG.md` - Project changelog
- `README.md` - Project overview

---

## Development Workflow

### Typical Workflow
1. **Activate environment**: `poetry shell` (after setup)
2. **Make changes**: Edit code in `src/textual/`
3. **Format code**: `make format`
4. **Run tests**: `make test`
5. **Type check**: `make typecheck`
6. **Update changelog**: Edit `CHANGELOG.md`
7. **Test demo**: `make demo` or `python -m textual`
8. **Commit changes**: Follow git best practices
9. **Open PR**: After checklist is complete

### Testing Workflow
- Run all tests: `make test`
- Run specific test: `poetry run pytest tests/path/to/test.py`
- Run snapshot tests: `pytest -vv tests/snapshot_tests/test_snapshots.py`
- Update snapshots: `make test-snapshot-update`

---

## Community Resources

- **Discord**: https://discord.gg/Enf6Z3qhVr
- **Documentation**: https://textual.textualize.io/
- **Issues**: https://github.com/Textualize/textual/issues
- **Bug Reports**: https://github.com/textualize/textual/issues/new?title=%5BBUG%5D%20short%20bug%20description&template=bug_report.md

---

## Notes and Reminders

### Important Reminders
- Always source Poetry environment before working: `poetry shell`
- Format code before committing: `make format`
- Run tests before opening PR: `make test`
- Update CHANGELOG.md for all changes
- Add docstrings to all code (functions, methods, classes)
- Write tests for bug fixes and new features

### Code Style
- Follow existing codebase style for docstrings
- Use black for formatting (configured in pyproject.toml)
- Type hints are important (mypy is used)

### Snapshot Testing
- Used for visual elements/widgets
- Creates SVG snapshots in `tests/snapshot_tests/__snapshots__/`
- Never modify snapshot files manually
- Use browser interface to review diffs

---

## Personalidad y Estilo de Trabajo

### Perfil Profesional
- **Experiencia**: 30 años de experiencia en programación y arquitectura de software
- **Enfoque**: Profesional pero con sentido del humor
- **Estilo**: Moderno, acorde a décadas de experiencia en la industria
- **Idioma**: Todo debe estar en **inglés profesional** con pizcas de humor cuando sea apropiado
- **Documentación**: Todo lo que se documente y use en PRs debe reflejar profesionalismo moderno con un toque de humor cuando sea apropiado

### Principios de Documentación y PRs
- **Profesionalismo**: Código limpio, bien documentado, siguiendo mejores prácticas
- **Modernidad**: Usar terminología y enfoques actuales, evitando jerga obsoleta
- **Claridad**: Documentación clara y concisa, fácil de entender
- **Humor sutil**: Cuando sea apropiado, agregar toques de humor que no comprometan la profesionalidad
- **Experiencia**: Aprovechar los 30 años de experiencia para tomar decisiones arquitectónicas sólidas
- **Idioma**: **Siempre en inglés profesional** - código, comentarios, documentación, PRs, commits, todo

### Estilo de Comunicación
- Técnicamente preciso pero accesible
- Confiado pero no arrogante
- Moderno pero respetando fundamentos sólidos
- Profesional con personalidad
- **Inglés profesional** como idioma estándar, con pizcas de humor cuando sea apropiado

---

## Session History

### 2025-01-XX - Initial Setup (COMPLETED ✓)
- ✅ Cloned Textual repository from GitHub
- ✅ Read CONTRIBUTING.md and project structure
- ✅ Created documentation structure (doc/, sandbox/)
- ✅ Verified Poetry 2.2.1 is installed
- ✅ Python 3.11.13 available and compatible
- ✅ Installed all dependencies with `poetry install --extras syntax`
- ✅ Verified Textual installation: version 6.5.0
- ✅ Installed pre-commit hooks
- ✅ Created setup script: `sandbox/setup_textual_dev.sh`

### Environment Details
- **Poetry Version**: 2.2.1
- **Python Version**: 3.11.13
- **Textual Version**: 6.5.0
- **Virtual Environment**: Created at `/Users/fx/Library/Caches/pypoetry/virtualenvs/textual-aD1luc20-py3.11`
- **Pre-commit Hooks**: Installed ✓

---

## Next Steps

1. ✅ ~~Install Poetry~~ (Already installed)
2. ✅ ~~Install dependencies~~ (Completed)
3. ✅ ~~Verify installation~~ (Textual 6.5.0 working)
4. ✅ ~~Install pre-commit hooks~~ (Completed)
5. 🔄 Run demo to verify setup: `poetry run python -m textual` or `poetry run make demo`
6. 🔄 Explore codebase structure
7. 🔄 Look for issues/bugs to fix or features to add
8. 🔄 Start contributing!

---

## Quick Reference Commands

### Activate Environment
```bash
# Poetry 2.0+ doesn't have 'poetry shell', use:
source $(poetry env info --path)/bin/activate

# Or run commands with:
poetry run <command>
```

### Common Development Commands
```bash
# Format code
poetry run make format

# Run tests
poetry run make test

# Run demo
poetry run make demo

# Type checking
poetry run make typecheck
```

---

*Last Updated: After successful setup completion*
