# OSDO Project Roadmap

This roadmap describes the development priorities of the OSDO Project. It is intentionally separate from [RECOGNITION.md](./RECOGNITION.md), which tracks external assurance and ecosystem recognition.

OSDO is an independent open-source project stewarded by **Hacker Dreams**.

## Current stable line — OSDO v2

OSDO v2 remains the stable framework line focused on security-first software delivery, pipeline generation, security automation, policy enforcement, evidence generation and cross-platform delivery integrations.

### Priority A — Stabilize v2

- [ ] Complete and verify GitLab CI parity for supported OSDO pipeline capabilities
- [ ] Complete Azure DevOps parity where documented as supported
- [ ] Publish and validate v2 tags across maintained component repositories
- [ ] Complete v2 documentation and migration guidance
- [ ] Validate CLI/App compatibility matrix
- [ ] Establish release-quality and backward-compatibility tests

### Priority B — Institutional project maturity

- [x] Establish Hacker Dreams as institutional steward
- [x] Publish project charter
- [x] Publish explicit governance and maintainer model
- [x] Publish adopter registry
- [x] Separate third-party alignment from certification/endorsement claims
- [ ] Expand active maintainer coverage beyond a single core maintainer
- [ ] Establish documented technical working groups as contributor activity grows

### Priority C — Security and supply-chain assurance

- [x] DCO enforcement
- [x] OpenSSF Scorecard workflow
- [x] SBOM generation in release workflow
- [x] Build provenance / attestation workflow
- [ ] Complete OpenSSF Best Practices Passing criteria
- [ ] Add signed release verification procedure
- [ ] Document release threat model and trust boundaries

### Priority D — Interoperability and adoption

- [ ] GitHub Actions interoperability profile
- [ ] GitLab CI interoperability profile
- [ ] Azure DevOps interoperability profile
- [ ] Policy/conformance test suite
- [ ] First externally verified adopter
- [ ] Public reference implementation demonstrating end-to-end OSDO v2

## Research track — autonomous policy-governed delivery

OSDO is investigating a broader model for autonomous, policy-governed software delivery loops.

This research is **not automatically OSDO v3**.

Before assigning a release number or project name, the OSDO RFC process must determine whether the work is best represented as:

1. an evolution of OSDO requiring a future major version;
2. an OSDO subproject/specification that consumes OSDO v2 capabilities;
3. or an independent project derived from OSDO's security, policy and delivery primitives.

### Research questions

- What is the canonical definition of a software delivery loop?
- Which responsibilities belong to observation, reasoning, authorization, execution and verification?
- How is autonomous authority bounded by policy?
- How are evidence, identity, risk and provenance carried between loop stages?
- Which actions may be autonomous, supervised or prohibited?
- How does a loop interoperate with existing CI/CD, GitOps, SRE and platform-engineering systems?
- Which OSDO v2 components can serve as enforcement/evidence primitives without coupling the new model to OSDO's existing implementation architecture?

### Decision gate

A formal RFC should compare the three project-shape options before implementation becomes a new major line.

The decision should consider:

- conceptual scope;
- API and configuration compatibility;
- target audience;
- governance requirements;
- release cadence;
- security boundary;
- implementation independence;
- ability to use OSDO without the autonomous-loop project and vice versa.

## External recognition

External-assurance goals are maintained separately in [RECOGNITION.md](./RECOGNITION.md). Foundation hosting or project status is not treated as a generic development milestone.
