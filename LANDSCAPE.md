# OSDO en el Ecosistema Cloud Native

## Posicionamiento

**"Built on CNCF-Graduated Projects"**

OSDO no es un framework cloud native aspiracional — está construido sobre
proyectos que ya pasaron la revisión de la CNCF.

## Categoría en el CNCF Landscape: Security & Compliance

### Proyectos CNCF integrados

| Proyecto     | Estado CNCF  | Rol en OSDO                                          |
|--------------|--------------|------------------------------------------------------|
| Kubernetes   | Graduated    | Plataforma de deployment target principal            |
| Prometheus   | Graduated    | Monitoring, métricas y alertas (`osdo monitor`)      |
| Argo CD      | Graduated    | GitOps + entrega continua pipelines                  |
| Harbor       | Graduated    | Container registry con scanning integrado            |
| Falco        | Graduated    | Runtime security y detección de amenazas             |
| cert-manager | Incubating   | Gestión automática de certificados TLS               |
| Kyverno      | Incubating   | Policy-as-code enforcement (`osdo-policy-gate`)      |

**Total: 5 proyectos Graduated + 2 Incubating = 7 proyectos CNCF integrados**

## Para la Submission al CNCF Landscape

- **Repositorio**: https://github.com/opensecdevops/osdo
- **Licencia**: Apache 2.0 (ver LICENSE)
- **Website**: https://opensecdevops.gitlab.io
- **Categoría**: Security & Compliance
- **Descripción corta** (<=160 chars): Framework DevSecOps que orquesta proyectos CNCF para implementar SecDevOps desde cero en minutos.
- **Logo**: SVG 300x300px requerido (fondo transparente)

## Por qué OSDO pertenece al CNCF Landscape

1. Cobertura documentada de OWASP Top 10, OWASP Mobile Top 10, OWASP GenAI Top 10
2. Soporte nativo para SLSA Level 3 (supply chain security)
3. OpenSSF Scorecard integrado en CI
4. Todas las herramientas de seguridad son proyectos open source
5. Funciona en cualquier entorno Kubernetes (EKS, GKE, AKS, K3s, bare metal)
