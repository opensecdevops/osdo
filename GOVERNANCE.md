# Gobernanza de OSDO

OSDO es un proyecto open source con **Hacker Dreams** como *institutional steward*.

El stewardship institucional existe para asegurar continuidad, custodia de la identidad del proyecto, coordinación externa y sostenibilidad a largo plazo. No convierte OSDO en un proyecto personal ni elimina la autoridad técnica de sus mantenedores.

## Principios de gobernanza

1. **Open source first** — OSDO se desarrolla públicamente y sus contribuciones se rigen por la licencia Apache-2.0 y el proceso de contribución del proyecto.
2. **Institutional continuity** — Hacker Dreams actúa como steward institucional para evitar que la continuidad del proyecto dependa de una sola persona.
3. **Technical merit** — las decisiones técnicas se toman por los mantenedores según mérito, evidencia, seguridad, compatibilidad y sostenibilidad.
4. **Transparent decisions** — los cambios relevantes deben quedar registrados mediante issues, merge requests/pull requests, RFCs o documentación equivalente.
5. **No implied endorsement** — OSDO puede implementar, mapear o alinearse con estándares y proyectos externos sin afirmar certificación, afiliación o endorsement cuando no exista formalmente.
6. **Attribution is preserved** — la contribución histórica de personas y organizaciones se mantiene mediante el historial de Git, documentación y registros del proyecto.

## Steward institucional

**Hacker Dreams** es el steward institucional de OSDO.

Responsabilidades del steward:

- custodiar la continuidad institucional del proyecto;
- mantener la identidad pública y el posicionamiento de OSDO;
- coordinar relaciones con comunidades, fundaciones y organismos externos;
- asegurar que exista una estructura de mantenimiento activa;
- facilitar infraestructura, dominios, cuentas y recursos cuando corresponda;
- proteger al proyecto frente a abandono, captura por un único contribuidor o uso que induzca a error sobre su estatus externo;
- aprobar cambios de gobernanza institucional, sin sustituir la revisión técnica de los maintainers.

El steward **no puede apropiarse de contribuciones de terceros ni reescribir su autoría**. La licencia y el historial del repositorio siguen siendo la fuente de verdad para atribución y derechos sobre contribuciones.

## Dirección técnica

La autoridad técnica reside en los maintainers activos listados en [MAINTAINERS.md](./MAINTAINERS.md).

### Project Lead

El Project Lead coordina roadmap, releases, RFCs y representación técnica del proyecto. El rol no implica propiedad personal sobre OSDO.

El Project Lead actual es:

| Nombre | GitHub | Rol |
|---|---|---|
| Antonio Juanilla | [@Spectertj](https://github.com/Spectertj) | Project Lead / Core Maintainer |

Los cambios en este rol deben documentarse mediante PR/MR y quedar aprobados por el steward institucional y la mayoría de maintainers activos.

## Proceso de decisiones

- **Cambios menores** (bugfixes, documentación, mantenimiento): *lazy consensus*; pueden fusionarse sin objeción después de 72 horas cuando no exista riesgo material.
- **Features nuevas**: issue o propuesta pública, mínimo 5 días de discusión cuando el cambio afecte interfaces, comportamiento o arquitectura compartida.
- **Breaking changes**: RFC público, mínimo 7 días de discusión y aprobación explícita de al menos 2 maintainers activos. Si solo existe un maintainer activo, se requiere además revisión del steward institucional antes de merge.
- **Cambios de gobernanza o identidad institucional**: requieren aprobación explícita del steward y revisión pública.
- **Seguridad del propio framework**: fast-track por maintainers core cuando exista riesgo material; debe quedar documentado posteriormente.

Ninguna persona individual tiene veto permanente sobre el avance del proyecto por ausencia o inactividad.

## RFC (Request for Comments)

Se requiere RFC para:

- breaking changes;
- cambios en el modelo de arquitectura de OSDO;
- incorporación de nuevos dominios principales;
- cambios en el modelo de compatibilidad;
- nuevas especificaciones de política, evidencia, autonomía o delivery loops;
- cambios de gobernanza técnica que afecten a toda la comunidad.

Proceso:

1. Abrir un issue con prefijo `[RFC]` y la etiqueta correspondiente.
2. Describir problema, motivación, propuesta, impacto, seguridad, compatibilidad y alternativas consideradas.
3. Mantener un período mínimo de discusión de 7 días, salvo incidentes de seguridad.
4. Obtener las aprobaciones requeridas por esta gobernanza.
5. Implementar mediante rama o PR/MR dedicada.
6. Registrar la decisión y, cuando corresponda, el impacto en `CHANGELOG.md`.

## Cadencia de releases

| Tipo | Cadencia orientativa |
|---|---|
| Patch | Cada 4 semanas o antes si existe vulnerabilidad crítica |
| Minor | Trimestral cuando exista contenido suficiente |
| Major | Cuando los breaking changes acumulados y el modelo de arquitectura lo justifiquen |

Las fechas son objetivos operativos, no obligaciones contractuales.

## Cómo convertirse en maintainer

1. Contribuciones consistentes y verificables al proyecto.
2. Historial de revisiones técnicas y comportamiento conforme al Código de Conducta.
3. Propuesta pública indicando área de responsabilidad.
4. Aprobación por mayoría simple de maintainers activos.
5. Actualización de `MAINTAINERS.md` mediante PR/MR.

No existe un derecho automático a convertirse en maintainer por antigüedad, empleo o afiliación organizativa.

## Inactividad y estatus emérito

Un maintainer puede declinar el rol en cualquier momento.

Cuando un maintainer permanezca inactivo durante seis meses o más, los maintainers activos y el steward pueden moverlo a **Emeritus Maintainer** después de dejar constancia pública de la decisión.

El estatus emérito:

- preserva la atribución histórica;
- no implica autoridad de aprobación sobre cambios actuales;
- permite reincorporación mediante el mismo proceso usado para maintainers activos.

## Conflictos de interés

Los maintainers deben declarar conflictos de interés materiales cuando una decisión pueda beneficiar directamente a su empleador, empresa, cliente o proyecto comercial.

La participación de una organización en OSDO no le concede control automático del roadmap.

## Política de seguridad del propio framework

OSDO debe aplicar controles de seguridad sobre su propio proceso de desarrollo, incluyendo cuando corresponda SAST, SCA, secret scanning, SBOM, provenance, signing y policy enforcement.

- Las vulnerabilidades siguen el proceso de `SECURITY.md`.
- Los parches críticos pueden publicarse fuera de ciclo.
- Los cambios de seguridad deben priorizar evidencia y reducción de riesgo sobre cadencias administrativas.

## Código de Conducta

Todos los participantes están sujetos a `CODE_OF_CONDUCT.md`.

Los reportes se gestionan a través del canal indicado en dicho documento o en la política de seguridad correspondiente.
