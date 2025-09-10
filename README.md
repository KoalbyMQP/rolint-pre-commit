# rolint-pre-commit

[![rolint](https://img.shields.io/pypi/v/rolint.svg)](https://pypi.python.org/pypi/rolint)
[![Actions status](https://github.com/KoalbyMQP/rolint-pre-commit/workflows/main/badge.svg)](https://github.com/KoalbyMQP/rolint-pre-commit/actions)

A [pre-commit](https://pre-commit.com/) hook for [RoLint](https://github.com/KoalbyMQP/Tools/tree/main/RoLint).

Distributed as a standalone repository to enable installing RoLint via prebuilt wheels from [PyPI](https://pypi.org/project/rolint/).

## Using RoLint with pre-commit

To run RoLint on your C/C++/Python files before each commit:

```yaml
repos:
-   repo: https://github.com/KoalbyMQP/rolint-pre-commit
    # RoLint version.
    rev: v0.1.9
    hooks:
    -   id: rolint  # Text output (default)
```

### JSON Output

For detailed reporting with JSON output:

```yaml
repos:
-   repo: https://github.com/KoalbyMQP/rolint-pre-commit
    # RoLint version.
    rev: v0.1.9
    hooks:
    -   id: rolint-json
        args: [--output-path, custom_results.json]  # Optional: custom output file
```

### Custom Arguments

You can override default arguments:

```yaml
repos:
-   repo: https://github.com/KoalbyMQP/rolint-pre-commit
    # RoLint version.
    rev: v0.1.9
    hooks:
    -   id: rolint
        args: [--lang, cpp, --output, json]  # Force C++ mode with JSON output
```

### Force Specific Language

To lint only specific file types:

```yaml
repos:
-   repo: https://github.com/KoalbyMQP/rolint-pre-commit
    # RoLint version.
    rev: v0.1.9
    hooks:
    -   id: rolint
        args: [--lang, python]  # Only check Python files
        types: [python]  # Only run on Python files
```

## What RoLint Checks

RoLint performs safety-focused linting for robotics code, checking for:

- Banned unsafe functions in C/C++
- Control flow safety issues
- Type safety violations
- Python code quality issues
- And more robotics-specific safety patterns

## License

This pre-commit hook repository is licensed under MIT License.
RoLint itself may have different licensing terms.