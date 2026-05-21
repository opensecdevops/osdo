# Matriz de Compatibilidad OSDO

## Versiones soportadas

| Componente | Versión v2 (actual) | Versión v1 (legacy) |
|------------|---------------------|---------------------|
| **CLI** (`@osdo/cli`) | v2.x — oclif/Node.js ≥20 | v1.x — Go 1.21+ |
| **osdo-actions** | v2.x | v1.x |
| **osdo-workflows** | v2.x | v1.x |
| **osdo-workflow-template** | v2.x | v1.x |
| **OSDO App** | v2.x (API `/api/cli/*`) | v1.x (sin API CLI) |

## Compatibilidad entre componentes

| CLI Version | osdo-actions | osdo-workflows | GitHub Actions | Node.js |
|-------------|--------------|----------------|----------------|---------|
| v2.x (oclif) | v2.x ✅ | v2.x ✅ | ubuntu-22.04+ | ≥20 LTS |
| v2.x (oclif) | v1.x ⚠️ | v1.x ⚠️ | ubuntu-20.04+ | ≥20 LTS |
| v1.x (Go) | v1.x ✅ | v1.x ✅ | ubuntu-20.04+ | N/A |
| v1.x (Go) | v2.x ❌ | v2.x ❌ | — | N/A |

**Leyenda**: ✅ Compatible | ⚠️ Funcional con warnings | ❌ No compatible

## Variables de entorno soportadas

| Variable | Descripción | Equivalente en flag | Desde |
|----------|-------------|---------------------|-------|
| `OSDO_VERBOSE` | Modo verbose | `--verbose` / `-v` | v2.0 |
| `OSDO_DRY_RUN` | Modo simulación | `--dry-run` | v2.0 |
| `OSDO_OUTPUT` | Formato de salida (`table`/`json`/`yaml`) | `--output` / `-o` | v2.0 |
| `OSDO_CONFIG` | Ruta al archivo de configuración | `--config` | v2.0 |
| `OSDO_APP_URL` | URL de la OSDO App | `--app-url` | v2.0 |
| `OSDO_APP_TOKEN` | Token de autenticación con la App | (login automático) | v2.0 |
| `KUBECONFIG` | Ruta al kubeconfig de Kubernetes | `--kubeconfig` | v1.0 |

## Códigos de salida del CLI

| Código | Significado | Comandos |
|--------|-------------|---------|
| `0` | Éxito — sin errores ni findings por encima del umbral | Todos |
| `1` | Error general — problema de configuración, red, o ejecución | Todos |
| `2` | Security gate fallido — findings por encima del umbral configurado | `scan`, `certify`, `security scan` |
| `3` | No autenticado — `osdo app login` requerido | `app pull`, `app push`, `app status` |
| `4` | Herramienta externa no encontrada — instalar la herramienta requerida | `scan`, `security scan`, `monitor` |
| `5` | Configuración inválida — `.osdo/config.yaml` no pasa validación del schema | `validate`, comandos con config |

## Requisitos mínimos del sistema

### CLI v2 (oclif/Node.js)
- **Node.js**: v20.0.0 LTS o superior (recomendado: v22 LTS)
- **npm**: v10 o superior
- **OS**: Linux (Ubuntu 20.04+), macOS (12+), Windows (WSL2 recomendado)

### CLI v1 (Go — legacy)
- **Go**: 1.21 o superior
- **OS**: Linux, macOS, Windows

### Para osdo-actions (GitHub Actions)
- **GitHub Actions Runner**: ubuntu-22.04 o ubuntu-latest
- **GitHub Actions**: API v3+

## Política de soporte

| Versión | Estado | Soporte hasta |
|---------|--------|---------------|
| v2.x | ✅ Activo — nuevas features + bugfixes | Indefinido |
| v1.x | ⚠️ Mantenimiento — sólo fixes críticos de seguridad | 2026-12-31 |
| v0.x | ❌ Sin soporte | EOL |

## Migración de v1 a v2

### CLI
```bash
# Desinstalar CLI v1 (Go)
# rm $(which osdo)  # si fue instalado manualmente

# Instalar CLI v2 (Node.js/oclif)
npm install -g @osdo/cli

# Verificar
osdo --version  # debe mostrar 2.x.x
```

### workflows (actualizar referencias)
```yaml
# Antes (v1)
uses: opensecdevops/osdo-actions/actions/osdo-sast@osdo-sast/v1.0.0

# Después (v2)
uses: opensecdevops/osdo-actions/actions/osdo-sast@osdo-sast/v2.0.0
```

### `.osdo/config.yaml` (schema actualizado)
```yaml
# Agregar campo version requerido en v2
version: "2.0"  # ← nuevo en v2

# El resto de la configuración mantiene compatibilidad
test:
  coverage:
    minimum: 85
security:
  quality_gates:
    critical: 0
    high: 5
```
