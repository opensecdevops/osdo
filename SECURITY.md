# Política de Seguridad

Este documento describe la política de seguridad del proyecto OSDO, incluyendo las versiones actualmente soportadas, cómo reportar vulnerabilidades de forma responsable y los compromisos del equipo en cuanto a tiempos de respuesta.

---

## Versiones Soportadas

La siguiente tabla indica qué versiones del proyecto OSDO reciben actualmente parches de seguridad:

| Versión | Estado              | Soporte hasta   |
|---------|---------------------|-----------------|
| v2.x    | Activo              | Activo          |
| v1.x    | Mantenimiento       | 2026-12-31      |

- **Activo**: recibe nuevas características, correcciones de errores y parches de seguridad.
- **Mantenimiento**: solo recibe parches de seguridad críticos hasta la fecha indicada. No se publicarán nuevas características.
- Las versiones anteriores a v1.x no reciben ningún tipo de soporte y se recomienda migrar a v2.x.

---

## Reportar una Vulnerabilidad

**Por favor, NO abras _issues_ públicos en GitHub para reportar vulnerabilidades de seguridad.** Publicar vulnerabilidades antes de que exista un parche disponible pone en riesgo a todos los usuarios del proyecto.

### Canales de reporte

Utiliza cualquiera de los siguientes canales para reportar una vulnerabilidad de forma confidencial:

1. **GitHub Security Advisories (preferido)**
   Abre un reporte privado directamente en el repositorio:
   [https://github.com/opensecdevops/osdo/security/advisories/new](https://github.com/opensecdevops/osdo/security/advisories/new)

2. **Correo electrónico**
   Envía un mensaje cifrado (PGP opcional) a:
   **security@opensecdevops.org**

### Información requerida en el reporte

Para que podamos evaluar y reproducir la vulnerabilidad de forma eficiente, incluye la siguiente información:

- **Descripción**: explicación clara de la vulnerabilidad, su naturaleza y posible explotación.
- **Pasos para reproducir**: instrucciones detalladas y, cuando sea posible, un _proof of concept_ (PoC) mínimo.
- **Impacto**: evaluación del alcance del problema (confidencialidad, integridad, disponibilidad) y posibles vectores de ataque.
- **Componente afectado**: indica qué parte del proyecto está afectada (por ejemplo, `osdo-sast`, `osdo-cli`, `osdo-workflow-template`, `osdo-infra-cli`, etc.).
- **Versión afectada**: especifica la versión o rango de versiones donde se ha identificado el problema.
- **Entorno**: sistema operativo, versión de Node.js / Go, versión de GitHub Actions runner u otro contexto relevante.
- **Solución sugerida** (opcional): si tienes ideas sobre cómo mitigar o corregir el problema, inclúyelas.

---

## Acuerdo de Divulgación Responsable

Al reportar una vulnerabilidad, te pedimos que:

- No divulgues la vulnerabilidad públicamente hasta que el equipo haya publicado un parche o declarado que no se tomará acción.
- No accedas, modifiques ni destruyas datos de otros usuarios durante la investigación.
- Actúes de buena fe y dentro de los límites de este acuerdo.

A cambio, el equipo OSDO se compromete a:

- Reconocer tu reporte en un plazo máximo de 48 horas.
- Mantenerte informado sobre el progreso de la evaluación y la corrección.
- Dar crédito público a los investigadores que reporten vulnerabilidades (salvo que prefieran el anonimato).
- No emprender acciones legales contra investigadores que actúen de buena fe conforme a esta política.

---

## SLA de Respuesta

El equipo OSDO se compromete a los siguientes tiempos de respuesta para los reportes de seguridad recibidos:

| Evento                              | Plazo comprometido                        |
|-------------------------------------|-------------------------------------------|
| Acuse de recibo                     | 48 horas                                  |
| Evaluación de severidad             | 5 días hábiles                            |
| Corrección y parche — Crítico       | 60 días calendario desde la confirmación  |
| Corrección y parche — Alto          | 90 días calendario desde la confirmación  |
| Corrección y parche — Medio / Bajo  | Próximo ciclo de release planificado      |

La severidad es evaluada conforme al sistema [CVSS v3.1](https://www.first.org/cvss/) y las definiciones del proyecto:

- **Crítico (9.0 – 10.0)**: compromiso total del sistema, ejecución remota de código sin autenticación, exposición masiva de secretos.
- **Alto (7.0 – 8.9)**: escalada de privilegios, bypass de controles de seguridad, exposición significativa de datos sensibles.
- **Medio (4.0 – 6.9)**: impacto limitado, requiere condiciones específicas o interacción del usuario.
- **Bajo (0.1 – 3.9)**: impacto mínimo, sin consecuencias operativas significativas.

---

## Herramientas de Seguridad

OSDO utiliza las siguientes herramientas de seguridad para proteger el código fuente, las dependencias y los artefactos del proyecto:

| Herramienta     | Categoría                         | Descripción                                                                 |
|-----------------|-----------------------------------|-----------------------------------------------------------------------------|
| **Semgrep**     | SAST                              | Análisis estático de código fuente para detección de patrones vulnerables.  |
| **Bandit**      | SAST (Python)                     | Análisis de seguridad estático para código Python.                          |
| **OSV-Scanner** | SCA                               | Escaneo de dependencias contra la base de datos Open Source Vulnerabilities. |
| **Grype**       | SCA / Contenedores                | Escaneo de vulnerabilidades en imágenes de contenedor y SBOMs.              |
| **Trivy**       | SCA / Contenedores / IaC          | Escáner integral para imágenes, sistemas de archivos e IaC.                 |
| **Gitleaks**    | Detección de Secretos             | Detección de secretos y credenciales expuestas en repositorios Git.         |

---

## Cobertura de Seguridad con OSDO GitHub Actions

Las [OSDO GitHub Actions](./osdo-actions/) proporcionan las siguientes coberturas de seguridad para pipelines de CI/CD:

| Área de Cobertura                        | Acción OSDO principal          |
|------------------------------------------|--------------------------------|
| **SAST** (Análisis Estático)             | `osdo-sast`                    |
| **SCA** (Análisis de Composición)        | `osdo-sca`                     |
| **Secrets** (Detección de Secretos)      | `osdo-secrets-scan`            |
| **Container** (Seguridad de Contenedor)  | `osdo-container-scan`          |
| **IaC** (Infraestructura como Código)    | `osdo-iac-scan`                |
| **SBOM** (Lista de Materiales de SW)     | `osdo-sbom`                    |
| **SLSA** (Seguridad de Cadena de Suministro) | `osdo-slsa-provenance`     |

---

## Hall of Thanks

El equipo OSDO agradece públicamente a las siguientes personas que han contribuido a la seguridad del proyecto mediante la divulgación responsable de vulnerabilidades:

| Investigador / Colaborador | Vulnerabilidad / Contribución   | Fecha      |
|----------------------------|---------------------------------|------------|
| *(próximas entradas)*      | —                               | —          |

Si reportas una vulnerabilidad y deseas ser incluido en esta lista, indícalo en tu reporte junto con el nombre o alias con el que deseas aparecer. Si prefieres el anonimato, tu privacidad será respetada.

---

## Contacto

Para cualquier consulta relacionada con la seguridad del proyecto que no corresponda a una vulnerabilidad activa, puedes contactarnos en:

- **Seguridad:** security@opensecdevops.org
- **Conducta:** conduct@opensecdevops.org
- **General:** https://github.com/opensecdevops/osdo/discussions
