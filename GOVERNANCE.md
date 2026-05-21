# Gobernanza de OSDO

## Mantenedores

| Nombre                    | GitHub               | Área de responsabilidad          |
|---------------------------|----------------------|----------------------------------|
| [Nombre del Mantenedor]   | [github-username]    | Core framework, CLI, releases    |
| [Nombre del Mantenedor]   | [github-username]    | osdo-actions, CI/CD pipelines    |
| [Nombre del Mantenedor]   | [github-username]    | Documentación, comunidad         |
| [Nombre del Mantenedor]   | [github-username]    | Seguridad, SAST/SCA/secrets      |

## Proceso de decisiones

- **Cambios menores** (bugfixes, docs): lazy consensus — merge sin objeción en 72 horas.
- **Features nuevas**: issue abierto con label `proposal`, mínimo 5 días de discusión antes de comenzar la implementación.
- **Breaking changes**: RFC en GitHub Discussions, mínimo 7 días de discusión, requiere aprobación explícita de al menos 2 mantenedores.
- **Seguridad del propio framework**: fast-track por mantenedores core sin esperar consensus general. Ver sección "Política de seguridad del propio framework" más abajo.

## Cadencia de releases

| Tipo   | Cadencia                                               |
|--------|--------------------------------------------------------|
| Patch  | Cada 4 semanas (o antes si hay vulnerabilidad crítica) |
| Minor  | Trimestral (Q1 / Q2 / Q3 / Q4)                        |
| Major  | Cuando los breaking changes acumulados lo justifican   |

Los releases de parche de seguridad fuera de ciclo están permitidos en cualquier momento y no requieren esperar al ciclo regular.

## Cómo convertirse en mantenedor

1. Contribuciones consistentes durante más de 3 meses (código, revisiones, issues, documentación).
2. Propuesta en GitHub Discussions con la contribución documentada y el área de responsabilidad propuesta.
3. Voto positivo por mayoría simple de mantenedores actuales durante un período de 7 días.
4. Incorporación a la tabla de mantenedores en este archivo mediante PR firmada por un mantenedor existente.

Un mantenedor puede declinar el rol en cualquier momento notificando al resto del equipo. Si un mantenedor lleva más de 6 meses sin actividad en el proyecto, podrá ser movido a estado "emérito" tras notificación previa.

## RFC (Request for Comments) — Proceso para Breaking Changes

1. Abrir un issue con el prefijo `[RFC]` y la label `breaking-change`.
2. Describir el cambio propuesto, la motivación, el impacto esperado en usuarios y las alternativas consideradas.
3. Período de discusión: mínimo 7 días desde la apertura del issue.
4. El RFC necesita aprobación explícita (comentario o review aprobado) de al menos 2 mantenedores.
5. Una vez aprobado, el RFC se implementa en una rama dedicada y se documenta en `CHANGELOG.md` con el número de issue del RFC.
6. Los RFCs rechazados se cierran con la label `rfc-rejected` y una explicación de los motivos.

## Política de seguridad del propio framework

OSDO come su propia medicina: `osdo-sast`, `osdo-sca` y `osdo-secrets-scan` se ejecutan sobre el código de OSDO en cada PR. Los resultados son requisito para hacer merge y son visibles en el resumen de la PR.

- Las vulnerabilidades del propio framework siguen el proceso de fast-track descrito en `SECURITY.md`.
- Los parches de seguridad se publican fuera del ciclo regular de releases cuando la severidad es crítica o alta.
- Ver `SECURITY.md` para la política completa de divulgación responsable, SLAs y contacto de seguridad.

## Código de Conducta

Todos los participantes en el proyecto OSDO están sujetos al `CODE_OF_CONDUCT.md`. Los reportes de conducta se gestionan a través de conduct@opensecdevops.org.
