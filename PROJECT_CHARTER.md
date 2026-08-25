# OSDO Project Charter

## 1. Purpose

OSDO (Open SecDevOps) is an open-source framework for security-first software delivery. Its purpose is to make secure delivery practices repeatable, automatable and portable across development platforms without locking users to a single CI/CD, cloud or security vendor.

OSDO combines pipeline generation, security controls, policy enforcement, evidence collection, compliance mapping and delivery automation through interoperable components such as its CLI, App, reusable workflows, actions and extensions.

## 2. Institutional stewardship

**Hacker Dreams** is the institutional steward of the OSDO Project.

The steward exists to provide continuity beyond any individual contributor and to coordinate institutional relationships, project identity, governance and long-term sustainability.

Technical decisions remain subject to the maintainer and RFC processes defined in [GOVERNANCE.md](./GOVERNANCE.md).

## 3. Project identity

OSDO is not presented as a personal project of any individual contributor.

Contributors, founding participants, maintainers and project leads may be credited for their work, but public project identity remains **OSDO Project**, stewarded by Hacker Dreams.

Where names, marks, domains or other project assets are administered by Hacker Dreams, such administration must be exercised for the benefit and continuity of the OSDO Project and in accordance with applicable law and existing contributor rights.

## 4. Scope

The OSDO Project may include:

- secure software delivery reference architectures;
- CI/CD and GitOps integrations;
- pipeline and workflow generation;
- SAST, SCA, secret, container, IaC, API, mobile, cloud, license and AI/LLM security controls;
- SBOM, signing, provenance and software supply-chain controls;
- policy-as-code and runtime policy enforcement;
- compliance and control mapping;
- CLI, APIs, dashboards and developer tooling;
- documentation, implementation guidance and maturity models;
- interoperability profiles for platforms such as GitHub, GitLab and Azure DevOps;
- future research and RFCs related to autonomous or policy-governed software delivery.

## 5. Out of scope

OSDO does not claim to:

- certify an organization against a third-party standard unless an authorized certification mechanism explicitly exists;
- imply endorsement by OWASP, CNCF, OpenSSF, Linux Foundation or any other organization without formal authorization;
- replace the governance of third-party tools it integrates;
- guarantee that use of OSDO alone establishes regulatory compliance;
- make security or delivery decisions outside the authority explicitly configured by the user or organization deploying it.

## 6. Technical independence

OSDO should remain vendor-neutral at the framework level.

Integrations with commercial or open-source products are allowed when they provide technical value, but no vendor receives privileged governance rights solely because OSDO supports its technology or receives sponsorship from it.

## 7. Governance model

The governance model contains three distinct responsibilities:

### Institutional Steward

Hacker Dreams provides institutional continuity, identity stewardship and external coordination.

### Project Lead

The Project Lead coordinates the technical roadmap, releases, cross-repository alignment and RFC process. The role does not imply personal ownership.

### Maintainers

Maintainers review and approve technical changes within defined responsibility areas. Active maintainers and their scopes are listed in [MAINTAINERS.md](./MAINTAINERS.md).

## 8. Contribution model

OSDO accepts external contributions under the repository's Apache-2.0 license and contribution requirements.

Contributors retain attribution through Git history and other project records. Organizational employment or sponsorship is not a prerequisite for contribution.

DCO or equivalent contribution attestation may be required by repository policy.

## 9. Security and supply-chain expectations

The OSDO Project should apply security controls to its own development and release process, including where technically applicable:

- branch protection and peer review;
- dependency and secret scanning;
- static analysis;
- SBOM generation;
- build provenance;
- signed or attestable releases;
- vulnerability disclosure policy;
- reproducible or verifiable release processes;
- OpenSSF Scorecard and Best Practices evaluation.

## 10. External standards and recognition

OSDO may map functionality to, implement controls from, or collaborate with external ecosystems including OWASP, OpenSSF, CNCF, NIST, CIS and SLSA.

The project must distinguish between:

- **alignment or mapping**;
- **participation or collaboration**;
- **listing or recognition**;
- **formal project hosting**;
- **certification or accreditation**.

Only statuses actually granted by the relevant organization may be displayed as such.

See [RECOGNITION.md](./RECOGNITION.md) for the current external-assurance roadmap.

## 11. Evolution of OSDO

Major architectural changes should begin as RFCs rather than being introduced solely by release numbering.

This includes work on autonomous, policy-governed software delivery loops. Such work may ultimately become:

- a new OSDO major version;
- an OSDO subproject or specification;
- or an independent project derived from OSDO concepts.

The choice must be made based on scope, compatibility, governance, audience and implementation boundaries rather than branding convenience.

## 12. Amendments

Changes to this charter require:

1. a public PR/MR;
2. review by active maintainers;
3. approval by the institutional steward;
4. an auditable record of the decision.
