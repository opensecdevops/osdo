# Contributing to OSDO

Thank you for your interest in contributing to the Open SecDevOps (OSDO) framework! This document provides guidelines and information about contributing.

---

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
- [Development Setup](#development-setup)
- [Commit Convention](#commit-convention)
- [Pull Request Process](#pull-request-process)
- [Security Issues](#security-issues)

---

## Code of Conduct

This project adheres to the [Code of Conduct](./CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.

---

## How to Contribute

### Reporting Bugs

1. Check existing [issues](https://github.com/opensecdevops/osdo/issues) to avoid duplicates
2. Use the bug report template
3. Include: steps to reproduce, expected behavior, actual behavior, environment details

### Suggesting Features

1. Open a [discussion](https://github.com/opensecdevops/osdo/discussions) first
2. Describe the use case and expected behavior
3. Wait for community feedback before starting implementation

### Code Contributions

1. Fork the relevant repository
2. Create a feature branch from `main`: `git checkout -b feat/my-feature`
3. Make your changes following our coding standards
4. Write tests for new functionality
5. Submit a pull request

---

## Development Setup

### Prerequisites

- Node.js >= 20.0.0 (for CLI)
- PHP >= 8.1 (for App)
- Go >= 1.21 (for Operator)
- Docker (for Scanner)

### Repository Structure

Each component has its own repository. Clone the one you want to work on:

```bash
# CLI development
git clone https://github.com/opensecdevops/osdo-cli.git
cd osdo-cli && npm install && npm run build

# App development
git clone https://github.com/opensecdevops/osdo-app.git
cd osdo-app && composer install && npm install

# Operator development
git clone https://github.com/opensecdevops/osdo-operator.git
cd osdo-operator && go mod download
```

---

## Commit Convention

We use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Code style (formatting, semicolons, etc.) |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `perf` | Performance improvement |
| `test` | Adding or correcting tests |
| `build` | Build system or external dependencies |
| `ci` | CI configuration |
| `chore` | Other changes that don't modify src or test |
| `security` | Security-related changes |

### Scopes

| Scope | Component |
|-------|-----------|
| `cli` | OSDO CLI |
| `app` | OSDO App |
| `actions` | OSDO Actions |
| `workflows` | OSDO Workflows |
| `operator` | OSDO Operator |
| `scanner` | OSDO Scanner |
| `docs` | Documentation |
| `infra` | Infrastructure |

### Examples

```
feat(cli): add osdo scan --format sarif output
fix(actions): correct exit code for policy violations
docs(workflows): update usage examples for v2
security(scanner): patch CVE-2024-XXXX in base image
```

---

## Pull Request Process

1. **Title**: Use conventional commit format
2. **Description**: Fill in the PR template completely
3. **Tests**: All existing tests must pass; add tests for new code
4. **Documentation**: Update relevant docs
5. **Review**: At least 1 maintainer approval required
6. **CI**: All checks must pass (lint, test, security scan)

### PR Labels

- `breaking-change` — Requires major version bump
- `security` — Security-related fix
- `needs-docs` — Documentation update required
- `good-first-issue` — Suitable for new contributors

---

## Security Issues

**Do NOT open public issues for security vulnerabilities.**

Please report security issues through [GitHub Security Advisories](https://github.com/opensecdevops/osdo/security/advisories/new) or see [SECURITY.md](./SECURITY.md) for full details.

---

## License

By contributing, you agree that your contributions will be licensed under the Apache License 2.0.
