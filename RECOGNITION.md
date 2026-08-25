# OSDO External Assurance & Recognition Roadmap

OSDO distinguishes technical alignment from certification, project hosting, ecosystem participation and institutional recognition.

This roadmap exists to prevent ambiguous or misleading claims while giving the project measurable external-assurance goals.

## Current project status

OSDO is an independent open-source project stewarded by **Hacker Dreams**.

Unless explicitly documented here with a verifiable external reference, OSDO does **not** claim to be certified, endorsed, hosted or approved by OWASP, CNCF, OpenSSF, Linux Foundation or any other external organization.

## Priority 1 — Open-source project assurance

- [ ] OpenSSF Best Practices — Passing
- [ ] OpenSSF Best Practices — Silver
- [ ] OpenSSF Best Practices — Gold
- [ ] Maintain an OpenSSF Scorecard target of at least 8.0/10
- [x] Developer Certificate of Origin enforcement for contributions
- [x] SBOM generation for release workflow
- [x] Build provenance / attestable release workflow
- [ ] Signed release artifacts and documented verification procedure
- [ ] Reproducible or independently verifiable release process where practical
- [ ] Public vulnerability-management metrics and release-security evidence

## Priority 2 — Framework evidence and interoperability

- [ ] Publish a control-mapping methodology for OWASP, SLSA, NIST SSDF and CIS references used by OSDO
- [ ] Separate OSDO-generated compliance evidence from third-party certification claims
- [ ] Publish GitHub Actions interoperability profile
- [ ] Publish GitLab CI interoperability profile
- [ ] Publish Azure DevOps interoperability profile
- [ ] Publish conformance tests for OSDO pipeline/security primitives
- [ ] Maintain an adopter registry with independently verifiable references

## Priority 3 — Ecosystem recognition and participation

### OpenSSF

- [ ] Complete Best Practices evaluation
- [ ] Participate in relevant OpenSSF working groups where OSDO can contribute implementation experience
- [ ] Publish OSDO supply-chain security evidence and lessons learned

### OWASP

- [ ] Maintain explicit mappings to applicable OWASP projects and standards without implying certification
- [ ] Present or contribute research/guidance on secure software delivery where appropriate
- [ ] Evaluate an OWASP Project relationship only if its governance and hosting model serves the OSDO community

### CNCF

- [ ] Complete cloud-native interoperability documentation
- [ ] Build measurable public adoption and project activity
- [ ] Engage relevant CNCF technical communities / TAGs / working groups
- [ ] Evaluate CNCF Landscape eligibility when project criteria are met
- [ ] Evaluate Sandbox only as a separate governance decision, not as a certification badge

### Linux Foundation and other foundations

- [ ] Evaluate participation or hosting only when it solves a concrete governance, sustainability or interoperability requirement
- [ ] Do not list foundation hosting as a generic prestige target

## Terminology rules

Project documentation should use these terms precisely:

| Term | Meaning in OSDO documentation |
|---|---|
| Aligned / mapped | OSDO maps controls or concepts to an external standard/project |
| Compatible / interoperable | OSDO has tested technical integration with a platform or interface |
| Listed / recognized | An external organization has formally listed OSDO in a program or directory |
| Participating | OSDO contributors participate in an external community or working group |
| Hosted | Project governance/assets have formally entered an external foundation's hosting model |
| Certified | Used only when an authorized certification program explicitly grants that status |
| Endorsed | Used only when the external organization explicitly provides endorsement rights |

## Badge policy

Badges representing external status may only be displayed when:

1. the status has actually been granted;
2. the badge links directly to a verifiable external record;
3. use of the badge complies with the external organization's trademark and branding policy;
4. wording does not overstate what the program provides.

Placeholder badge IDs, aspirational project-status badges and badges that imply approval before approval is granted must not be published.

## Review cadence

Maintainers should review this roadmap at least once per quarter and whenever an external status changes.
