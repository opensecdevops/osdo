# OSDO in the Cloud Native Ecosystem

## Positioning

OSDO is an independent open-source project stewarded by **Hacker Dreams**.

OSDO integrates established cloud-native, security and software-supply-chain tools to provide a portable SecDevOps framework. Integration with a CNCF, OWASP, OpenSSF or Linux Foundation project does not imply that OSDO itself is hosted, certified or endorsed by that organization.

## Cloud-native interoperability

OSDO is designed to work with technologies commonly used in cloud-native software delivery, including:

| Technology | Role in OSDO |
|---|---|
| Kubernetes | Deployment target and runtime platform |
| Prometheus | Monitoring, metrics and alerting integration |
| Argo CD | GitOps / continuous-delivery integration |
| Harbor | Container registry and image-security workflows |
| Falco | Runtime-security integration |
| cert-manager | Certificate-management integration |
| Kyverno | Policy-as-code and Kubernetes policy enforcement |
| OPA / Conftest | Policy evaluation for delivery and infrastructure controls |
| Sigstore / Cosign | Signing and software-supply-chain verification |
| Syft | SBOM generation |

The exact maturity or foundation status of third-party projects should be obtained from their respective official sources rather than hard-coded here as an OSDO claim.

## External recognition strategy

OSDO's external strategy is evidence-first:

1. demonstrate secure project governance and supply-chain practices;
2. complete OpenSSF Best Practices evaluation and maintain a strong Scorecard posture;
3. publish interoperable profiles for GitHub Actions, GitLab CI and Azure DevOps;
4. document verifiable adoption;
5. participate in relevant OWASP, OpenSSF and CNCF technical communities;
6. pursue ecosystem listing or formal project relationships only when eligibility and governance requirements are satisfied.

Detailed status and targets are maintained in [RECOGNITION.md](./RECOGNITION.md).

## CNCF Landscape

A future CNCF Landscape submission may be evaluated when OSDO meets the then-current eligibility criteria and has sufficient public adoption/activity.

A Landscape listing is treated as **ecosystem recognition**, not certification.

Potential positioning should be selected according to the Landscape taxonomy in force at the time of submission; this document does not claim a pre-approved category.

## OWASP

OSDO may map its security controls to OWASP projects and standards and may participate in OWASP community activities.

OSDO must not describe such mappings as OWASP certification or endorsement. Any future OWASP Project relationship requires a separate governance decision and must follow OWASP's then-current project requirements.

## OpenSSF

OpenSSF Best Practices and Scorecard are prioritized as external assurance mechanisms because they provide evidence about the security and maintenance practices of the OSDO open-source project without requiring OSDO to represent itself as a foundation-hosted project.

## Project evidence

Evidence relevant to external assessment includes:

- Apache-2.0 licensing;
- DCO/sign-off policy;
- vulnerability disclosure policy;
- OpenSSF Scorecard workflow;
- SBOM generation;
- build provenance;
- documented governance;
- named active and emeritus maintainers;
- public RFC/decision process;
- adopter registry;
- cross-platform interoperability documentation.

## Canonical project references

- Repository mirror: https://github.com/opensecdevops/osdo
- Source of truth: https://gitlab.com/opensecdevops/osdo
- Governance: `GOVERNANCE.md`
- Charter: `PROJECT_CHARTER.md`
- Maintainers: `MAINTAINERS.md`
- Adopters: `ADOPTERS.md`
- External assurance roadmap: `RECOGNITION.md`
