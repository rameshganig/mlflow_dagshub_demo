# Contributing Guidelines

Thank you for considering contributing to this project! We welcome contributions of all kinds, from bug reports to code enhancements. Please take a moment to review the guidelines below to make the contribution process smooth for everyone.

---

## Table of Contents

- [Code Style](#code-style)
- [Commit Message Conventions](#commit-message-conventions)
- [Branch Naming](#branch-naming)
- [Submitting Pull Requests](#submitting-pull-requests)
- [Issue Reporting](#issue-reporting)
- [License](#license)

---

## Code Style

- **Python**: Follow the [PEP 8](https://peps.python.org/pep-0008/) style guide.
- **Formatting**: Run `black .` before committing. The project uses Black with a line length of 88 characters.
- **Linting**: Ensure the code passes `flake8` and `mypy` checks. You can run the test suite with:
  ```bash
  make lint   # runs black, flake8, and mypy
  make test   # runs the unit tests
  ```
- **Docstrings**: Use Google style docstrings for all public functions, classes, and modules.
- **Imports**: Keep imports grouped and sorted using `isort`.
- **Type Hints**: Add type hints to all functions and public methods.

---

## Commit Message Conventions

We follow the **Conventional Commits** specification. A well‑structured commit message helps generate a clear changelog and makes the history easier to read.

```
<type>(<scope>): <subject>

<body>

<footer>
```

- **type** – one of `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`, `ci`.
- **scope** – optional, a short identifier of the area affected (e.g., `parser`, `cli`).
- **subject** – concise description (max 50 characters, no period at the end).
- **body** – optional, more detailed explanation if needed.
- **footer** – optional, used for breaking changes (`BREAKING CHANGE:`) or referencing issues (`Closes #123`).

**Example**:
```
feat(parser): add support for JSON lines

The parser can now handle newline‑delimited JSON records, which is useful for streaming data.

Closes #42
```

---

## Branch Naming

- Use a short, descriptive name prefixed by the type of work:
  - `feature/<short-description>`
  - `bugfix/<short-description>`
  - `docs/<short-description>`
- Keep the branch name lowercase and use hyphens (`-`) to separate words.

---

## Submitting Pull Requests

1. **Fork** the repository and **clone** your fork.
2. **Create a new branch** from `main` following the naming convention above.
3. Implement your changes, ensuring the code style and tests pass.
4. **Run the test suite** locally:
   ```bash
   make test
   ```
5. **Commit** using the Conventional Commits format.
6. **Push** the branch to your fork.
7. Open a **Pull Request** against the `main` branch of the upstream repository.
   - Provide a clear title and description.
   - Reference any related issues (e.g., `Closes #123`).
   - If the PR introduces a breaking change, describe it in the description.
8. The CI pipeline will run automatically. Address any failures before merging.
9. Once approvals are received and CI passes, a maintainer will merge the PR.

---

## Issue Reporting

If you encounter a bug or have a feature request, please open an issue before submitting a PR. Include:
- A clear title.
- Steps to reproduce (for bugs).
- Expected vs. actual behavior.
- Any relevant logs or screenshots.

---

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (see the `LICENSE` file).

---

Thank you for helping make this project better! 🎉
