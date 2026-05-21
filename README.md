# OSDO — Open SecDevOps Framework

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![OpenSSF Best Practices](https://www.bestpractices.dev/projects/0/badge)](https://www.bestpractices.dev/projects/0)
[![OWASP](https://img.shields.io/badge/OWASP-Tool%20Project-orange)](https://owasp.org)
[![Version](https://img.shields.io/badge/version-2.0.0-green.svg)](./CHANGELOG.md)

**OSDO (Open SecDevOps)** is an open-source security-first DevOps framework that integrates security scanning, compliance automation, and secure software delivery into CI/CD pipelines. It provides a complete toolkit from code commit to production deployment with built-in security gates.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        OSDO Framework v2.0                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌──────────┐  ┌──────────────┐  ┌──────────────┐  ┌───────────┐  │
│  │ OSDO CLI │  │  OSDO App    │  │  OSDO Actions │  │ OSDO      │  │
│  │ @osdo/cli│  │  (Dashboard) │  │  (22 actions) │  │ Workflows │  │
│  └────┬─────┘  └──────┬───────┘  └──────┬───────┘  └─────┬─────┘  │
│       │                │                  │                │        │
│       └────────────────┴──────────────────┴────────────────┘        │
│                              │                                      │
│  ┌──────────────────────────────────────────────────────────────┐   │
│  │              Security Scanning Layer                          │   │
│  │  SAST │ SCA │ Secrets │ Container │ IaC │ DAST │ SBOM │ Sign │   │
│  └──────────────────────────────────────────────────────────────┘   │
│                              │                                      │
│  ┌──────────────────────────────────────────────────────────────┐   │
│  │              Compliance & Reporting                           │   │
│  │  OWASP Top 10 │ SLSA │ OpenSSF Scorecard │ CIS │ NIST       │   │
│  └──────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 📦 Components

| Component | Description | Repository |
|-----------|-------------|------------|
| **OSDO CLI** | Command-line interface (oclif/TypeScript) for scanning, certification, deployment, and pipeline management | [`osdo-cli`](https://github.com/opensecdevops/osdo-cli) |
| **OSDO App** | Web dashboard (Laravel) for pipeline visualization, team management, and compliance reporting | [`osdo-app`](https://github.com/opensecdevops/osdo-app) |
| **OSDO Actions** | 22 granular GitHub Actions for security scanning (SAST, SCA, secrets, containers, IaC, DAST, SBOM, signing) | [`osdo-actions`](https://github.com/opensecdevops/osdo-actions) |
| **OSDO Workflows** | 10 reusable GitHub Actions workflows for complete security pipelines | [`osdo-workflows`](https://github.com/opensecdevops/osdo-workflows) |
| **OSDO Workflow Template** | Starter workflow templates for quick adoption | [`osdo-workflow-template`](https://github.com/opensecdevops/osdo-workflow-template) |
| **OSDO Operator** | Kubernetes operator for automated security policy enforcement | [`osdo-operator`](https://github.com/opensecdevops/osdo-operator) |
| **OSDO Scanner** | Containerized multi-tool security scanner | [`osdo-scanner`](https://github.com/opensecdevops/osdo-scanner) |
| **OSDO Starter** | Project starter templates with pre-configured security | [`osdo-starter`](https://github.com/opensecdevops/osdo-starter) |
| **OSDO VS Code** | VS Code extension for in-editor security scanning | [`osdo-vscode`](https://github.com/opensecdevops/osdo-vscode) |
| **OSDO Pre-commit** | Pre-commit hooks for early security detection | [`osdo-pre-commit`](https://github.com/opensecdevops/osdo-pre-commit) |
| **Documentation** | Framework documentation (Docusaurus) | [`documentation`](https://github.com/opensecdevops/documentation) |

### Legacy Components

| Component | Description | Repository |
|-----------|-------------|------------|
| OSDO Infra CLI | Legacy Go/Cobra CLI (deprecated in favor of `@osdo/cli`) | [`osdo-infra-cli`](https://github.com/opensecdevops/osdo-infra-cli) |
| OSDO SAST | Standalone SAST action (now part of `osdo-actions`) | [`osdo-sast`](https://github.com/opensecdevops/osdo-sast) |
| OSDO SCA | Standalone SCA action (now part of `osdo-actions`) | [`osdo-sca`](https://github.com/opensecdevops/osdo-sca) |
| OSDO Secrets Scan | Standalone secrets scanning (now part of `osdo-actions`) | [`osdo-secrets-scan`](https://github.com/opensecdevops/osdo-secrets-scan) |
| OSDO Container Scan | Standalone container scan (now part of `osdo-actions`) | [`osdo-container-scan`](https://github.com/opensecdevops/osdo-container-scan) |
| OSDO IaC Scan | Standalone IaC scan (now part of `osdo-actions`) | [`osdo-iac-scan`](https://github.com/opensecdevops/osdo-iac-scan) |
| OSDO Sign | Artifact signing (now part of `osdo-actions`) | [`osdo-sign`](https://github.com/opensecdevops/osdo-sign) |
| OSDO SBOM | SBOM generation (now part of `osdo-actions`) | [`osdo-sbom`](https://github.com/opensecdevops/osdo-sbom) |
| OSDO Pentest Pipeline | Penetration testing pipeline | [`osdo-pentest-pipeline`](https://github.com/opensecdevops/osdo-pentest-pipeline) |

---

## 🚀 Quick Start

### Install the CLI

```bash
npm install -g @osdo/cli
```

### Initialize a project

```bash
osdo init
```

This creates:
- `.osdo/config.yaml` — Project configuration
- `.github/workflows/osdo-security.yml` — Security pipeline
- `.pre-commit-config.yaml` — Pre-commit hooks
- `SECURITY.md` — Security policy

### Run a security scan

```bash
osdo scan
```

Runs SAST (Semgrep), SCA (OSV-Scanner), secrets detection (Gitleaks), and container linting (Hadolint).

### Generate compliance report

```bash
osdo certify
```

Maps scan results to OWASP Top 10, SLSA levels, and OpenSSF controls.

### Use in GitHub Actions

```yaml
name: OSDO Security Pipeline
on: [push, pull_request]

jobs:
  security:
    uses: opensecdevops/osdo-workflows/.github/workflows/osdo-framework.yml@v2
    with:
      scan-sast: true
      scan-sca: true
      scan-secrets: true
      scan-containers: true
      fail-on-critical: true
```

---

## 📋 Standards & Certifications

OSDO is designed to help organizations achieve and maintain compliance with:

| Standard | Coverage |
|----------|----------|
| **OWASP Top 10** | Full SAST/DAST coverage mapping |
| **SLSA** | Build provenance and supply chain integrity |
| **OpenSSF Scorecard** | Automated best practices scoring |
| **CIS Benchmarks** | Container and infrastructure hardening |
| **NIST SSDF** | Secure Software Development Framework |
| **SOC 2** | Security control evidence generation |

### Framework Certifications (In Progress)

- [ ] CNCF Sandbox Project
- [ ] OWASP Tool Project
- [ ] Linux Foundation Project
- [ ] OpenSSF Best Practices Badge

---

## 📖 Documentation

Full documentation is available at the [OSDO Documentation](https://github.com/opensecdevops/documentation) repository.

- [Quick Start Guide](https://github.com/opensecdevops/documentation)
- [CLI Reference](https://github.com/opensecdevops/osdo-cli#readme)
- [Actions Catalog](https://github.com/opensecdevops/osdo-actions#readme)
- [Workflow Templates](https://github.com/opensecdevops/osdo-workflows#readme)
- [Migration Guide (v1 → v2)](./COMPATIBILITY.md)

---

## 🔒 Security

Please see [SECURITY.md](./SECURITY.md) for our security policy and responsible disclosure process.

---

## 🏛️ Governance

This project follows an open governance model. See [GOVERNANCE.md](./GOVERNANCE.md) for details on:
- Maintainers and decision-making process
- Release cadence
- How to become a maintainer

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## 📄 License

This project is licensed under the Apache License 2.0 — see the [LICENSE](./LICENSE) file for details.

---

## 🗺️ Roadmap

See [LANDSCAPE.md](./LANDSCAPE.md) for the project landscape and strategic direction.

---

## 📊 Changelog

All notable changes are documented in [CHANGELOG.md](./CHANGELOG.md).

This project adheres to [Semantic Versioning](https://semver.org/) and [Keep a Changelog](https://keepachangelog.com/).
