# CHANGELOG

Todos los cambios notables de este proyecto están documentados en este archivo.

El formato sigue [Keep a Changelog](https://keepachangelog.com/es/1.0.0/) y este proyecto adhiere a [Versionado Semántico](https://semver.org/lang/es/).

---

## [Unreleased]

### Pendiente
- Páginas Docusaurus `v2/` completas en Español
- OWASP Tool Project application
- Versión tags en sub-repositorios: `osdo-sast/v2.0.0`, `@osdo/cli@2.0.0`

---

## [2.0.0] — 2026-04-08

> **Gran salto Q2 2026** — OSDO pasa de colección de actions a framework SecDevOps certificado.

### Cambios incompatibles (Breaking Changes)

- CLI migrado de Go/Cobra (`osdo-infra-cli`) a **oclif v4 + TypeScript** (`@osdo/cli`). Instalar con `npm install -g @osdo/cli`
- `.osdo/config.yaml` ahora requiere `version: "2"` — ver [COMPATIBILITY.md](./COMPATIBILITY.md) para la guía de migración
- Todas las actions deben referenciarse como `@v2` (era `@v1` o `@main`)
- Exit codes cambiados: `2` = security gate failure, `3` = policy violation, `4` = auth error — ver [COMPATIBILITY.md](./COMPATIBILITY.md)

### Nuevas Funcionalidades

#### CLI — @osdo/cli v2.0.0
- `osdo init` — Golden Path initializer con listr2: crea `.osdo/config.yaml`, `.github/workflows/osdo-security.yml`, `.pre-commit-config.yaml`, `SECURITY.md`
- `osdo scan` — scanner real: Semgrep (SAST), OSV-Scanner (SCA), Gitleaks (secrets), Hadolint (container linting). Graceful fallback si la herramienta no está instalada
- `osdo certify` — genera reporte Markdown real desde `.osdo/results/**/*.json`, mapea a controles OWASP/SLSA/OpenSSF. Exit code 2 si controles críticos sin cubrir
- `osdo deploy` — deployment multi-plataforma: `kubectl apply` (Kubernetes), `helm upgrade --install` (Helm), `docker stack deploy` (Swarm). Actualiza estado en la App automáticamente
- `osdo pipeline generate|validate|sync` — 6 templates × 3 plataformas (GitHub/GitLab/Azure). `sync` actualiza `@v0/@v1` → `@v2` in-place
- `osdo catalog list|describe|add` — catálogo de 22 actions + 10 workflows. `add` inyecta steps en YAML existente vía js-yaml
- `osdo preset list|show|create` — presets persistidos en `~/.config/osdo/config.json` vía `conf`
- `osdo app login|logout|pull|push|status` — integración bidireccional completa con OSDO App v2
- `osdo monitor setup|metrics|alerts` — Prometheus `/api/v1/query`, Alertmanager `/api/v1/alerts`, Grafana `/api/health` vía HTTP real
- `osdo security scan` — Trivy (filesystem/container) + Grype (SCA) con umbral `--fail-on CRITICAL|HIGH|MEDIUM`
- `osdo security policies` — Kyverno (kubectl get polr) + OPA Conftest con salida de violations estructurada
- `osdo security secrets` — Gitleaks con salida SARIF para Code Scanning de GitHub
- `osdo security compliance` — mapeo a OWASP Top 10, SLSA niveles, OpenSSF controles
- `osdo security report` — reporte consolidado HTML/Markdown/JSON desde todos los `.osdo/results/security/*.json`
- `BaseCommand` con `globalFlags` (verbose, dry-run, output, kubeconfig, config), `checkAppAuth()`, `dryRun()`, `dryRunLog()`
- `ConfigManager` dos capas: `conf` (user-level `~/.config/osdo/config.json`) + `js-yaml` (project `.osdo/config.yaml`)

#### OSDO App v2 — API CLI
- Autenticación Sanctum Bearer Token con abilities `cli:read`, `cli:write`
- `POST /api/cli/auth` — emite token (revoca tokens anteriores de la misma app automáticamente)
- `DELETE /api/cli/auth` — revoca token actual
- `GET /api/cli/packages` — paquetes del usuario con última versión
- `GET /api/cli/packages/:id` — `config.json` + array de templates Handlebars para renderizado
- `GET /api/cli/packages/:id/download` — ZIP stream
- `GET|POST /api/cli/deployments` — listado paginado y creación de deployments
- `PATCH /api/cli/deployments/:id/status` — actualiza estado + `deployed_at` automático
- Tabla `deployments`: user_id, package_version_id, platform, namespace, environment, status (enum), metadata (JSON)
- `CliAuthController`, `CliPackageController`, `CliDeploymentController`

#### Generator — Módulo Handlebars (replica Generator.vue)
- `lib/generator/handlebars.ts` — `renderPackage()`, `buildContext()`, `resolveActiveBlocks()`. Inyección dual `fieldName` + `fieldName_value` para campos select
- `lib/generator/prompter.ts` — `promptForPackage()` con `@inquirer/prompts` (text/switch/select), activación de bloques por dependencias
- `lib/generator/writer.ts` — `writeGeneratedFiles()` con soporte `--overwrite` y dry-run

#### osdo-actions v2.0.0 — 22 actions
Ver [osdo-actions/CHANGELOG.md](./osdo-actions/CHANGELOG.md) para detalle completo.

6 nuevas actions en v2:
- `osdo-mobile-scan` — SAST móvil (MobSF, Semgrep iOS/Android rules)
- `osdo-smart-contract-audit` — Slither + Mythril para contratos Solidity
- `osdo-llm-scan` — análisis de prompts, modelos y pipelines LLM
- `osdo-cloud-scan` — Checkov + Prowler para AWS/GCP/Azure
- `osdo-license-scan` — FOSSA / license-checker con política de licencias configurable
- `osdo-api-scan` — OWASP API Security + 42Crunch para OpenAPI/Swagger

#### Gobernanza e Institucional
- `GOVERNANCE.md` — tabla de maintainers, proceso de consenso perezoso, RFC para breaking changes, cadencia de releases (patch mensual, minor trimestral)
- `SECURITY-INSIGHTS.yml` — OpenSSF Security Insights v1: inventario SAST/SCA/secrets/SBOM/container, contacto `security@opensecdevops.org`
- `LANDSCAPE.md` — datos para CNCF Landscape Sandbox, categoría "Security & Compliance", 7 proyectos CNCF referenciados
- `COMPATIBILITY.md` — matriz CLI↔actions, tabla de env vars (7 variables), exit codes (0–5), guía migración v1→v2
- `.osdo/config.schema.json` — JSON Schema Draft-07 con 8 propiedades top-level: version, instance, runtime, test, security, reporting, app, build
- `.github/workflows/scorecard.yml` — OpenSSF Scorecard CI (`ossf/scorecard-action@v2.4.0`), objetivo ≥8.0/10
- `LICENSE` (raíz) — Apache 2.0, OpenSecDevOps Contributors 2024–2026

#### Documentación (Español como idioma principal)
- `osdo-actions/docs/QUICKSTART.md` → traducido al español (278 líneas)
- `osdo-actions/docs/ACTIONS_REFERENCE.md` → traducido al español con ejemplos `@v2`
- `osdo-actions/docs/CERTIFICATION_CHECKLISTS.md` → traducido al español
- `osdo-actions/docs/OPENSSF_BADGE_GUIDE.md` → traducido al español
- `osdo-workflows/README.md` → traducido al español
- `osdo-workflow-template/docs/SECURITY_CAPABILITIES.md` → reescrito en español (tabla OWASP Top 10 detallada, SLSA L3, inventario de herramientas)
- `pre-commit/README.md` → expandido de 9 a 187 líneas con configs por lenguaje (PHP, Node.js, Python, Go, Docker, IaC)
- `osdo-infra-cli/docs/CLI_REFERENCE.md` → añadidas secciones de exit codes y variables de entorno
- `documentation/sidebars.js` → sección OSDO v2 (introducción, CLI, 22 actions por dominio, 10 workflows, 4 dominios de seguridad)

### Correcciones

- `osdo-infra-cli/cmd/status.go`: Eliminado placeholder `// ... (existing vars)` — todas las variables declaradas correctamente
- `osdo-actions/publish.yml`: Lista actualizada a 22 actions (antes hardcodeada a 14)
- `osdo-workflow-template/ARCHITECTURE.md`: Roadmap actualizado a fechas 2026
- Docusaurus: Typo "OSDO is esay" corregido, tagline en Español
- `ux.table` reemplazado por `cli-table3` (eliminado en oclif v4)
- Import `import Handlebars from 'handlebars'` corregido a `import * as Handlebars` (ESM compatibility)

### Seguridad

- Exit code 2 en `osdo scan` cuando el security gate falla
- Exit code 3 en `osdo security scan`, `osdo security policies` con violations sobre el umbral
- Tokens Sanctum con abilities limitadas, auto-revocación al hacer re-login
- Gitleaks con salida SARIF integrable en GitHub Code Scanning
- `SECURITY.md` con SLA: 7 días crítico, 30 días alto, 60 días medio

---

## [1.0.0] — 2025-12-14

### Lanzamiento Público Inicial

- Framework de 3 capas: osdo-actions, osdo-workflows, osdo-workflow-template
- 16 GitHub Actions: sast, sca, secrets-scan, container-scan, iac-scan, sbom, sign, test-quality, compliance-report, dast-scan, api-scan, mobile-scan, cloud-scan, license-scan, policy-gate, fuzz
- 10 workflows reutilizables especializados
- CLI inicial en Go/Cobra con comandos: init, scan, certify, pipeline, deploy, status, security, catalog, monitor, preset
- App Laravel para registro y generación de paquetes de infraestructura
- Documentación inicial en Docusaurus (inglés)
- Pre-commit hooks básicos para PHP y Node.js

---

[Unreleased]: https://github.com/opensecdevops/osdo/compare/v2.0.0...HEAD
[2.0.0]: https://github.com/opensecdevops/osdo/compare/v1.0.0...v2.0.0
[1.0.0]: https://github.com/opensecdevops/osdo/releases/tag/v1.0.0
